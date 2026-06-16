# Netflix-Movies-and-TV-Shows
Clean and prepare a raw dataset (with nulls, duplicates, inconsistent formats).
Data Cleaning and Preprocessing Summary

The Netflix Movies and TV Shows dataset was cleaned using Python Pandas. Missing values in the director, cast, and country columns were replaced with "Unknown". Records with missing date_added values were removed, while missing rating and duration values were filled appropriately. Duplicate records were checked and removed. Text values were standardized using title case, and the date_added column was converted into a consistent date format (dd-mm-yyyy). Column names were cleaned by converting them to lowercase and replacing spaces with underscores. Finally, data types were verified and the cleaned dataset was exported as netflix_cleaned.csv.

## Key Changes

*Handled missing values
*Removed duplicates
*Standardized text formatting
*Converted date formats
*Renamed column headers
*Validated data types
*Exported cleaned dataset
