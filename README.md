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
