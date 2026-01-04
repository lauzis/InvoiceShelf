# Agents

## GitHub Copilot CLI

**Role**: AI Development Assistant

**Description**: An interactive command-line tool that assists with software engineering tasks, including code generation, refactoring, debugging, and file management.

**Contributions to this Session**:
- **Exchange Rate Provider**: Added support for **Frankfurter** (https://api.frankfurter.dev) as a new exchange rate provider.
- **Exchange Rate Provider Deletion**: Removed the restriction preventing the deletion of active exchange rate providers.
- **Frankfurter Integration**: Fixed a 500 error when saving the Frankfurter provider by ensuring the API key defaults to an empty string instead of null, satisfying the database constraint.
- **Historical Exchange Rates**: Updated the exchange rate retrieval logic to fetch rates based on the expense/invoice date instead of the current date.
- **UI/UX**: Renamed the "Get Metadata" button to "Extract data from image" in the Expense Create/Edit view.
- **Debugging**:
    - Identified and fixed the issue with `FormData` serialization for boolean values in the Pinia store.
    - Diagnosed and resolved the PDF preview URL object structure issue.
    - Debugged date parsing issues and implemented robust formatting using `moment.js`.
    - Resolved a 500 error in the Customer API due to strict SQL mode violations.
    - Improved amount extraction logic to correctly identify and append percentage values (e.g., 21.00%, 21%) to the end of the suggested amounts list.
    - Added validation to filter out invalid UTF-8 characters and replacement characters from suggested currencies.
    - Refined currency symbol extraction to only match symbols that are surrounded by spaces or adjacent to numbers.
    - Updated currency suggestion logic to prioritize 3-letter ISO codes over 1-letter symbols.
    - Removed the redundant "Download Receipt" button next to the "Extract data from image" button.
    - Implemented caching for receipt metadata extraction to improve performance.
    - Added category suggestion logic based on the identified customer's expense history.
    - Updated category suggestion logic to always move "Unverified" to the end of the suggested list.
    - Added "force refresh" capability to the extraction button to bypass cache on second click.
    - Updated the extracted data form to use 100% height, removing the scrollbar constraint.
    - Added a "Delete" button (red) to the Expense Edit view with confirmation dialog.
    - Added a percentage slider to the receipt extraction form to calculate partial expense claims (snaps to 10, manual override).
- **Documentation**: Created this change log and agents file.
