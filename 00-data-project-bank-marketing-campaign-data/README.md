# Jupyter Notebook: Bank Marketing Data Cleaning
This Jupyter Notebook cleans and reformats data from a marketing campaign conducted by a bank with the goal of acquiring personal loans.  The cleaned data will be split into three separate CSV files for easier storage and analysis in a PostgreSQL database.

## Data Description
The original data is stored in a CSV file named "bank_marketing.csv" and contains information about clients contacted during a marketing campaign. The data includes:

- Client demographics (age, job, marital status, education)
- Loan information (credit default, mortgage status)
- Campaign details (number of contacts, contact duration, previous campaign outcome)
- Economic indicators (consumer price index, Euribor rate)
- Contact information (month, day - used to create a "last contact date")
- Cleaning and Splitting Process

This script performs the following cleaning and reformatting steps:

1. **Change special characters**: Replaces "." to "_" in "job" and "education" columns. Replaces "unknown" in "education" with NaN.
2. **Convert Booleans**: Converts "yes" and "no" values in "credit_default" and "mortgage" columns to True/False booleans.
3. **Standardize Month**: Converts month names in the "month" column to lowercase for consistent mapping.
4. **Map Month to Numbers**: Creates a dictionary to map month names (lowercase) to numerical values (1-12).
5. **Create Year**: Adds a new column "year" with a constant value of 2022.
6. **Convert Campaign Outcome**: Converts "yes" and "no" values in "previous_outcome" and "campaign_outcome" to True/False booleans.
7. **Create Last Contact Date**: Combines "day", "month", and "year" columns into a new "last_contact_date" column in YYYY-MM-DD format.

## Splitting Data into Separate Files
The script then splits the cleaned data into three separate CSV files:

- **client.csv**: Contains client demographics and loan information.
- **campaign.csv**: Contains campaign details and last contact date.
- **economics.csv**: Contains economic indicators.

## Running the Script
Save this script as a Jupyter Notebook file (e.g., "bank_marketing_cleaning.ipynb").
Ensure you have pandas and numpy libraries installed (`pip install pandas numpy`).
Run the script within a Jupyter Notebook environment.
## Output
The script will generate three CSV files in the same directory as the notebook:

- client.csv
- campaign.csv
- economics.csv

These files can be imported into a PostgreSQL database for further analysis.