# Cyclistic-Bike-Share-Analysis-Capstone-Project

Google Data Analytics Capstone project for the Google Data Analytics Certificate 
(Google/Coursera, July 2026) analysing member vs. casual rider behavior.

## Project Overview

The analysis comprised 5.5M Divvy/Cyclistic bike-share trips (2025) comparing member vs. casual rider 
behavior using Python, pandas, R/ggplot2, and Folium. It includes temporal, geospatial, and statistical 
analysis with data-driven marketing recommendations.

**Key steps:**

- Data Cleaning (Python)
- Exploratory Data Analysis (EDA) (Python) — Dataset Overview, Missing Stations, Ride Patterns, Temporal Analysis, Statistical Visualizations (R/ggplot2) and Geospatial Analysis
- Summary of EDA Findings
- Top Three Recommendations
- Conclusion

## Business Problem

Cyclistic is a fictive bike-share company in Chicago. Their director of marketing wants to maximize the number of annual memberships. For that reason, the data analytics team is asked to analyse the different usage behaviors of casual riders and annual members. Based on the results, the data analytics team should provide recommendations for a new marketing strategy. 

## Dataset

- **Source:** Divvy Trips dataset, published by the City of Chicago on the Chicago Data Portal
- **Link:** [Divvy Trips — Chicago Data Portal](https://data.cityofchicago.org/Transportation/Divvy-Trips/fg6s-gzvg/about_data)
- **Raw data URL:** [Divvy trip data S3 bucket](https://divvy-tripdata.s3.amazonaws.com/index.html) (12 monthly ZIP files, Jan-Dec 2025)
- **Size:** ~5.55M rides across 12 months (Jan-Dec 2025)
- **Documentation:** [divvybikes.com/system-data](https://divvybikes.com/system-data)

**Fields used:** `ride_id`, `rideable_type`, `started_at`, `ended_at`, `start_station_name`/`id`, `end_station_name`/`id`, `start_lat`/`lng`, `end_lat`/`lng`, `member_casual`

**Note on demographic data:** the Divvy Trips documentation states that subscriber-pass trips may include basic demographic fields (age, gender). However, the 2025 extract used in this analysis does not include any demographic columns — only trip, station, and rider-type (member/casual) data are present.

**Note on data context (2025 vs. earlier Divvy/Cyclistic analyses):** readers comparing this analysis to other Cyclistic capstone projects (many of which use 2019-2021 data, the original case study period) should note that the Divvy station network grew substantially in 2025 — Chicago's Department of Transportation and Lyft added or upgraded over 140 stations that year, part of a broader expansion past 1,100 total stations. Station-level findings (e.g., top 10 start/end stations) may not directly match earlier analyses simply because the underlying station network itself has changed and grown. The `rideable_type` (classic/electric bike) and `member`/`casual` rider-type schema used throughout this analysis have been Divvy's standard data structure since 2020 and are not unique to this dataset.

*Data license: this repository's code is MIT-licensed (see LICENSE), but the underlying Divvy trip data remains subject to the [Divvy Data License Agreement](https://divvybikes.com/data-license-agreement), which governs how the data may be accessed, analyzed, and redistributed.*
