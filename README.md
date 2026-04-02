# Crime-Data-Analytics
### Data Cleaning and Preprocessing
- Instead of plain Pandas, Dask is used for all preprocessing steps.<br>
- Dask splits the large file into smaller partitions and processes 
them chunk by chunk, keeping memory usage low on the full 8M row dataset.<br>
- Will suffice to answer scalability questions.<br>

### What has been done:
- Loaded the dataset using dd.read_csv() with correct column dtypes
- Removed duplicate records based on ID column
- Dropped rows with missing values
- Removed rows with invalid/zero coordinates
- Parsed the Date column into datetime format
- Extracted Hour, Month, DayOfWeek, Year as separate columns
- Kept only the top 25 most frequent Location Descriptions, rest marked as OTHER
- Converted Primary Type, Location Description, Description to categorical
- Dropped unnecessary columns (IUCR, FBI Code, Case Number, Updated On, Beat, Ward)
- Called .compute() to finalize all steps.<b> Result is a clean Pandas DataFrame</b>

### For the next steps:
- The final output is a standard Pandas DataFrame called allCrimes.
- Next person can use it for EDA, visualizations, clustering, 
and any ML modeling without worrying about Dask anymore.
- A backup copy is saved as backup in case you need the clean data again.

## Exploratory Data Analysis & Visualization 

### Overview
* Full EDA is performed on the cleaned `allCrimes` DataFrame produced during Data Cleaning.

### What has been done

**Statistical Summary**
* Printed dataset shape, column types, and numeric descriptive statistics
* Computed value counts for Primary Type and Location Description
* Calculated overall arrest rate and domestic crime rate
* Confirmed no missing values remain after cleaning

**Univariate Analysis**
* Bar chart of top 15 crime types by frequency
* Bar chart of top 10 location types where crimes occur

**Time-based Analysis**
* Line chart of crime frequency by hour of day (0–23) with peak hour marked
* Bar chart of crime frequency by day of week with peak day highlighted
* Multi-line trend chart of top 5 crime types over the years which shows which crimes are rising or falling
* Line chart of seasonal pattern, crimes by month across all years
* Line chart of long-term yearly trend from 2003 to 2024

**Bivariate Analysis**
* Heatmap of crime count by hour of day vs day of week : reveals peak time windows
* Horizontal bar chart of arrest rate per crime type (top 10) : highlights which crimes are more/less likely to result in arrest

**Location-based Analysis**
* Bar chart of total crime count per police district with highest district highlighted
* Geographic scatter plot of 50,000 sampled crime locations using Latitude and Longitude which gives a visual sense of spatial crime density across Chicago

**Pattern Identification**
* Printed summary of all key patterns: peak hour, peak month, peak day, most common crime, most dangerous district, overall arrest rate, and long-term crime reduction percentage

