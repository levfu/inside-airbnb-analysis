# Inside Airbnb
### Airbnb Booking Data Analysis Project by Time / City

**Objective:** Analyze supply trends, pricing, and operational performance of the Airbnb market across 3 cities: Brussels, Berlin, and Paris.

---

## Table of Contents
1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
3. [Installation Requirements](#installation-requirements)
4. [How to Run](#how-to-run)
5. [Data Processing Pipeline](#data-processing-pipeline)
6. [List of Charts](#list-of-charts)
7. [Team Members](#team-members)

---

## 1. Introduction
* This project uses data from **Inside Airbnb**, a website providing Airbnb data snapshots by city and collection date. Files are typically in CSV format (sometimes gzipped), including listings (accommodation info and pricing), calendar (availability and daily prices), reviews, and neighbourhoods (GeoJSON/CSV boundary data) depending on the city.

* Official data download page: https://insideairbnb.com/get-the-data/

* Exploration documentation: https://insideairbnb.com/explore

* The processed data for each city will be used to answer the following questions:
  1. How do supply and rental prices change over time?
  2. Which areas are the most expensive and which have the highest listing density?
  3. What are the occupancy rates and revenue performance?
  4. What is the level of host professionalization?
  5. What do guest reviews say?
  6. What are the location and neighborhood insights?

* Data includes the following snapshots:
  1. **Brussels, Belgium:** 22/12/2024, 16/03/2025, 21/06/2025
  2. **Berlin, Germany:** 21/12/2024, 15/03/2025, 20/06/2025, 23/09/2025
  3. **Paris, France:** 06/12/2024, 03/03/2025, 06/06/2025, 12/09/2025

---

## 2. Project Structure
```text
.
├── raw/                         # Raw data (organized by city/snapshot_date)
├── processed/                   # Cleaned data & KPI tables
├── figures/                     # Visualizations
├── reports/                     # Technical reports (PDF)
├── src/                         # Notebooks / scripts
├── README.md                    # Run instructions
└── requirements.txt             # Libraries & versions
```

---

## 3. Installation Requirements
* All required libraries are listed in `requirements.txt`.

* Install dependencies:
```text
pip install -r requirements.txt
```

* Contents of `requirements.txt`:
```text
pandas
numpy
matplotlib
seaborn
adjustText
scikit-learn
```

---

## 4. How to Run

**Step 1: Prepare the Data**
1. Download the files `listings.csv.gz`, `calendar.csv.gz`, `reviews.csv.gz`, and `neighbourhoods.csv` for Brussels, Berlin, and Paris from Inside Airbnb.
2. Place them into the following directory structure:
```text
/raw/<city_name>/<snapshot_date>/
(<city_name> - city name, <snapshot_date> - data collection date)
```

**Step 2: Process Data & Compute KPIs**
1. Run the notebooks for each city in order — Brussels → Berlin → Paris — to clean, process, and generate KPI summary files.
```text
# Data processing, cleaning, and normalization
/src/<city_name>_EDA.ipynb/

# Aggregation and KPI computation
/src/<city_name>_Summary_KPI.ipynb/

(<city_name> - city name)
```
2. Input: Raw data from `/raw/`.
3. Output: Cleaned CSV files in `/processed/<city_name>/` and `/reports/`.
```text
CSV files in /processed/<city_name>/
# Neighborhood-level data for the city
/processed/<city_name>/kpi_neighbourhood_<city_name>.csv/

# Review trend data for the city
/processed/<city_name>/kpi_review_trends_<city_name>.csv/

# Room type distribution data for the city
/processed/<city_name>/kpi_room_type_<city_name>.csv/

# Occupancy rate / seasonality data for the city
/processed/<city_name>/kpi_seasonality_<city_name>.csv/

# General summary data for the city
/processed/<city_name>/kpi_summary_general_<city_name>.csv/


CSV files in /reports/
# Report on processed data quality
/reports/qa_summary_<city_name>.csv

(<city_name> - city name)
```

**Step 3: Visualization & Comparison**
1. Run the notebooks for each city in order — Brussels → Berlin → Paris — to generate per-city charts and a combined comparison chart.
```text
# Per-city charts
/src/<city_name>_Visualization.ipynb/

# Combined cross-city comparison charts
/src/Summary_Visualization.ipynb/
```
2. Input: KPI CSV files from `/processed/`.
3. Output: Charts saved as PDF files in `/figures/`.


---

## 5. Data Processing Pipeline
* Read data from `/raw/`, process currency columns, etc.
* Flag outliers, filter out noise, etc.
* Compute base metrics for each city.
* Perform deep analysis on computed metrics to generate visualizations.

---

## 6. List of Charts
* Output files in `/figures/` include:

**1. Brussels charts:**
```text
brussels_01_supply.pdf
brussels_02_price.pdf
brussels_03_multi_host.pdf
brussels_04_availability.pdf
brussels_05_occupancy.pdf
brussels_06_room_type.pdf
brussels_07_map_labeled.pdf
brussels_08_top10_supply.pdf
brussels_09_top10_price.pdf
brussels_10_price_distribution.pdf
brussels_11_price_heatmap_optimized.pdf
brussels_12_reviews_trend.pdf
```

**2. Berlin charts:**
```text
berlin_01_supply.pdf
berlin_02_price.pdf
berlin_03_multi_host.pdf
berlin_04_availability.pdf
berlin_05_occupancy.pdf
berlin_06_room_type.pdf
berlin_07_top10_supply.pdf
berlin_08_top10_price.pdf
berlin_09_price_distribution.pdf
berlin_10_property_type.pdf
berlin_11_price_segments.pdf
berlin_12_reviews_trend.pdf
```

**3. Paris charts:**
```text
paris_01_supply.pdf
paris_02_price.pdf
paris_03_multi_host.pdf
paris_04_availability.pdf
paris_05_occupancy.pdf
paris_06_room_type.pdf
paris_07_map_labeled.pdf
paris_08_top10_supply.pdf
paris_09_top10_price.pdf
paris_10_price_distribution.pdf
paris_11_price_heatmap.pdf
paris_12_reviews_trend.pdf
```

**4. Combined comparison charts (Brussels, Berlin, Paris):**
```text
H01_Total_Supply_All_Snapshots.pdf
H02_Median_Price_Horizontal.pdf
H03_Price_Anomaly_ZScore.pdf
H04_Availability_Trend.pdf
H05_MultiHost_Stacked.pdf
H06_Occupancy_Rate_LineChart.pdf
H07_Room_Type_GroupedBar.pdf
H08_Price_RoomType.pdf
H09_Price_Segments.pdf
H10_KMeans_Price_Quality.pdf
H11_Quality_Scores.pdf
H12_Price_Quality_Boxplot.pdf
H13_Top15_Neighborhoods.pdf
H14_Reviews_Trend.pdf
H15_Radar_Summary.pdf
```

---

## 7. Team Members
* Lê Việt Phú 
* Hoàng Huy Hoàng 
* Trần Trung Hiếu 