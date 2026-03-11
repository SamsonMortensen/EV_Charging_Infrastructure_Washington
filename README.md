## EV Charging Infrastructure in Washington State ##

## Project Overview ##
The goal of this project is to analyze the relationship between Electric Vehicle (EV) adoption and the availability of public charging infrastructure in Washington state. By wrangling and merging disparate datasets, this analysis identifies whether the deployment of DC fast chargers is keeping pace with the regions showing the highest concentration of registered EVs.

**Data Sources**
This project extracts and synthesizes data from two distinct sources:

***National Renewable Energy Laboratory (NREL) API***: JSON data was programmatically extracted using the requests library to gather a list of registered public electric vehicle charging stations in Washington State. Key variables included station_name, zip, and the count of high-speed chargers (ev_dc_fast_num).

***Washington State Data.gov***: A CSV dataset containing Washington state EV registrations was programmatically downloaded using Pandas. Key variables used for analysis were the vehicle Model and Postal Code.

***Technologies Used***
Python (Data Extraction, Cleaning, and Analysis)

Pandas (Data Manipulation and Merging)

Requests (API Integration)

Matplotlib & Seaborn (Data Visualization)

Jupyter Notebook (Development Environment)

**Data Wrangling & Cleaning Process**

To prepare the raw datasets for a cohesive analysis, several data wrangling steps were executed:

Excluded incomplete records by dropping rows with missing Postal Code values to ensure location-based merging remained accurate.

Resolved tidiness issues by converting all EV registration column names to snake_case (lowercasing, replacing spaces with underscores, and removing parentheses) to align with Python programmatic best practices.

Checked for and dropped exact duplicate rows in the charging station dataframe based on a subset of critical columns to prevent inflating the charger counts.

Standardized the key merging columns by renaming zip to postal_code and removing trailing decimals (e.g., .0) from the EV registration postal codes to create identical string matches.

Aggregated the total number of fast chargers per postal code and performed an inner join to combine the two dataframes into a single, clean dataset (cleaned_merged_tukwila_ev_data.csv).

# Key Visualizations & Insight #
The project answers the core research question: Do zip codes with high Electric Vehicle (EV) registrations also have a higher number of DC fast charging stations available?

**Scatter Plot Analysis**: Visualizes the direct correlation between the total number of registered EVs and the total number of DC fast chargers across different zip codes.

**Top 10 Zip Code Bar Chart**: Isolates the top 10 zip codes with the highest EV adoption and displays the exact number of fast chargers available in those specific areas, highlighting infrastructure gaps.

# Future Work & Reflections #
If given more time to expand this project, future iterations would include exploring the nested JSON structures from the NREL API to extract additional variables such as pricing structures and connector types. Furthermore, deeper text standardization on the vehicle "Make" and "Model" fields would allow for an expanded analysis to determine which EV manufacturers are most popular in areas with high fast-charger availability.
