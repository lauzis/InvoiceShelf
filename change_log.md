# Change Log

## [Unreleased] - 2026-01-03

### Added
- **Exchange Rate Provider**: Added support for **Frankfurter** (https://api.frankfurter.dev) as a new exchange rate provider. This provider is free and does not require an API key.
- **Exchange Rate Provider Deletion**: Removed the restriction preventing the deletion of active exchange rate providers.
- **Frankfurter Integration**: Fixed a 500 error when saving the Frankfurter provider by ensuring the API key defaults to an empty string instead of null, satisfying the database constraint.
- **Historical Exchange Rates**: Updated the exchange rate retrieval logic to fetch rates based on the expense/invoice date instead of the current date. This ensures more accurate financial records.

### Changed
- **UI/UX**: Renamed the "Get Metadata" button to "Extract data from image" in the Expense Create/Edit view.

### Fixed
- **Attachment Persistence**: Fixed a bug in `expense.js` store where the `is_attachment_receipt_removed` flag was incorrectly serialized as a string "false" (evaluated as true by PHP), causing attachments to be deleted on the second save.
- **PDF Preview**: Fixed a 404 error for PDF previews in the Edit Expense view by correctly handling the object structure of `attachment_receipt_url`.
- **Customer List**: Fixed a 500 error in the customer list API caused by a strict SQL mode violation in the `GROUP BY` clause. Refactored the query to use subqueries for aggregate calculations.
- **Receipt Extraction**: Improved amount extraction logic to correctly identify and append percentage values (e.g., 21.00%, 21%) to the end of the suggested amounts list.
- **Receipt Extraction**: Added validation to filter out invalid UTF-8 characters and replacement characters from suggested currencies.
- **Receipt Extraction**: Refined currency symbol extraction to only match symbols that are surrounded by spaces or adjacent to numbers, reducing false positives from text.
- **Receipt Extraction**: Updated currency suggestion logic to prioritize 3-letter ISO codes (e.g., EUR, USD) over 1-letter symbols (e.g., $) in the suggested list.
- **UI/UX**: Removed the redundant "Download Receipt" button next to the "Extract data from image" button in the Expense Create/Edit view, as a download button already exists at the top of the page.
- **Performance**: Implemented caching for receipt metadata extraction. Extracted data is now stored in the media object's custom properties, preventing redundant OCR processing on subsequent requests.
- **Receipt Extraction**: Added category suggestion logic. The system now identifies the customer from the receipt and suggests the most frequently used expense categories for that customer.
- **Receipt Extraction**: Updated category suggestion logic to always move "Unverified" to the end of the suggested list, prioritizing specific categories.
- **Receipt Extraction**: Added "force refresh" capability. Clicking "Extract data from image" a second time bypasses the cache and re-runs OCR.
- **UI/UX**: Updated the extracted data form in the Expense Create/Edit view to use 100% height, removing the fixed maximum height constraint and allowing it to match the preview column's height.
- **UI/UX**: Added a "Delete" button to the top of the Expense Edit view (in red), allowing users to delete the expense directly from the edit page with a confirmation modal.
- **Receipt Extraction**: Added a percentage slider (0-100%) to the extracted data form. This allows users to specify what portion of the extracted amount should be claimed as an expense (e.g., 50% for shared costs). The slider snaps to multiples of 10, while the input field allows precise manual entry. The layout uses a 2/3 to 1/3 ratio.
