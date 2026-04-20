# Crime Data Analytics - Chicago Crime Dataset

## Dataset
Chicago Crime Dataset from the [City of Chicago Open Data Portal](https://data.cityofchicago.org/api/views/ijzp-q8t2/rows.csv?accessType=DOWNLOAD).
7.8M+ crime records spanning 2001 to present, with 19 attributes including crime type, location, date, and arrest status.

## Steps
**1. Data Preprocessing - Dask**<br>
Loaded and cleaned the full 7.8M row dataset using Dask for memory-efficient, parallel processing. Steps include deduplication, null removal, coordinate filtering, datetime parsing, rare-value encoding, and column pruning. Output is a clean Pandas DataFrame ready for analysis.

**2. Exploratory Data Analysis**<br>
Analyzed crime type distribution, arrest rates, monthly/seasonal patterns, and long-term trends from 2003–2024 using Dask for scalable groupby and aggregation operations.

**3. Modelling** <br>
**i) Hotspot Detection - PySpark (Bisecting K-Means):**
Clustered crimes into 30 spatiotemporal zones using Latitude, Longitude, and Hour as features. Bisecting K-Means was chosen over standard K-Means for its speed on large datasets. Each cluster represents a distinct crime hotspot.

**ii) Arrest Prediction - PySpark (Random Forest):**
Trained a Random Forest classifier (100 trees, depth 10) on 80/20 split to predict whether a crime leads to arrest. The Hotspot_ID from clustering is used as an engineered feature, linking the two pipelines. Achieved AUC 0.84 and F1 0.85 on 1.58M test records.


## Results
| Metric | Value |
|---|---|
| AUC-ROC | 0.8402 |
| Precision | 87.5% |
| Recall | 86.5% |
| F1 Score | 0.8494 |

## Team Members:
Foram Gandhi (U23CS032) <br>
Bhumika Patil (U23CS046) <br>
Nirmeet Parmar (U23CS047) <br>
Harsh Parmar (U23CS056) <br>
Krishna Chhipa (U23CS075)
