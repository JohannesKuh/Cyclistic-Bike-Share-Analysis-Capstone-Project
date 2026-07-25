# Cyclistic-Bike-Share-Analysis-Capstone-Project

Google Data Analytics Capstone project for the Google Data Analytics Certificate 
(Google/Coursera, July 2026) analysing member vs. casual rider behavior.

## Executive Summary

- Analyzed 5.5M Divvy/Cyclistic bike-share trips (2025 data, City of Chicago) to compare member vs. casual rider behavior
- Conducted EDA using Python, pandas, R/ggplot2, and Folium across six areas: Dataset Overview, Missing Station Investigation, Ride Patterns, Temporal Analysis, Statistical Visualizations, and Geospatial Analysis
- Found a consistent behavioral divide across every dimension examined: members ride for commuting (weekday, bimodal, business-district), casual riders ride for leisure (weekend, summer, lakefront)
- Top 3 recommendations: electric bike-focused membership incentives, seasonal & shoulder-month conversion campaigns, and landmark & attraction-based membership benefits
- Limitations & further research: demographic data are missing (age, sex) preventing a deeper segmentation; station-type classifications ("touristic" vs. "business-district") are qualitative and could be validated against an external POI/land-use dataset; start→end station pairs were not analyzed per-ride (a Sankey flow diagram could test this); single-year data limits time-series validation; recommendations should be A/B tested before a full campaign rollout
- Business impact: the analysis shows evidence-based targeting (e.g., geospatial analysis reveals station-level conversion opportunities), replaces guesswork and helps prevent failures — poor data and weak strategy contribute to 14% of overall business failures tied directly to marketing ([Cropink](https://cropink.com/failed-marketing-campaigns), 2026)

## Project Overview

The project analyzed member vs. casual rider behavior based on 5.5M Divvy/Cyclistic bike-share trips (2025) using Python, pandas, R/ggplot2, and Folium. The analysis followed these steps:

**Key steps:**
* Imports & Setup (Python)
* Load & Merge Data (Python)
* Data Cleaning (Python)
* EDA — Dataset Overview (Python)
* EDA — Missing Station Investigation (Python)
* EDA — Ride Patterns (Python)
* EDA — Temporal Analysis (Python)
* EDA — Statistical Visualizations (R/ggplot2)
* EDA — Geospatial Analysis (Python)
* Summary of EDA Findings (Python)
* Top Three Recommendations
* Conclusion

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

## Approach

EDA findings are summarized and formed the basis for the top three recommendation decisions.

1. **EDA** — Dataset Overview, Missing Stations, Ride Patterns, Temporal Analysis,
   Statistical Visualizations (R/ggplot2), and Geospatial Analysis. Differences in start-station
   preferences by rider type, discovered during Ride Patterns, motivated the dedicated
   geospatial analysis (Folium heatmap and top-stations map).
2. **Summary** — the main findings were summarized regarding rider composition, ride duration, bike type preference,
   hourly pattern, weekday vs. weekend behavior, seasonal patterns, and station/geospatial patterns.
3. **Top Three Recommendations** — Electric bike-focused membership incentives, seasonal & shoulder-month conversion
   campaigns, landmark & attraction-based membership benefits

## Key Results

- **Overall Rider Composition:** Members are the largest rider type, accounting for 64% of all rides (3,552,530), while casual riders form a substantial minority at 36% (1,994,691).
- **Ride Duration:** Casual riders ride approximately 7 minutes longer on average (19.10 minutes) than members (11.95 minutes), and show a wider spread of ride durations (IQR: 6.30–21.05 minutes) compared to members (IQR: 5.03–14.50 minutes).
- **Bike Type Preference:** Both groups prefer electric bikes over classic bikes, with casual riders showing a marginally higher preference (67% vs. 64% for members).
- **Hourly Pattern:** Members show a clear bimodal pattern — a first peak at 8:00 (approx. 255,000 rides) and a second, higher peak at 17:00 (approx. 380,000 rides) — while casual riders show a unimodal pattern with a single peak at 17:00 (approx. 190,000 rides). This confirms members' commuter behavior versus casual riders' leisure-oriented usage.
- **Weekday vs. Weekend:** Members ride significantly more on weekdays (approx. 2,720,000 rides, 77% of all member rides); casual riders also lean weekday (approx. 1,251,000 rides, 63% of all casual rides), but far less concentrated. Faceting the hourly pattern by day (R/ggplot2) revealed that members' bimodal, commute-driven pattern on weekdays shifts to a unimodal, leisure-driven pattern on weekends — converging with casual riders' pattern, and confirming members use Cyclistic for two distinct purposes depending on the day.
- **Seasonal Patterns:** Members show high ridership across all warmer seasons (Summer peak ~1,270,000 rides, 36% of all member rides; Fall ~1,130,000, 32%), while casual riders show a steeper seasonal concentration (Summer peak ~950,000 rides, 48% of all casual rides; Fall drop to ~585,000, 29%). Average ride duration follows the same seasonal shape for both groups but at very different scales — casual riders' duration ranges from ~10-12 minutes (Dec-Feb) to ~21-22 minutes (Jun-Jul), while members range only from ~10-11 to ~13 minutes over the same period.
- **Station & Geospatial Patterns:** Casual riders prefer touristic and lakefront locations — most-used station DuSable Lake Shore Dr & Monroe St (31,236 rides, ~1.57% of all casual rides), followed by Navy Pier and Streeter Dr & Grand Ave. Members favor central business-district stations — most-used station Kingsbury St & Kinzie St (31,202 rides), followed by Clinton St & Washington Blvd and Clinton St & Madison St. These findings are supported by the Folium heatmap of start locations and the Folium map of top stations. *("Touristic" and "business-district" labels are qualitative interpretations based on station names and Chicago geography, not a field in the data.)*
- **Overall Key Insight:** across every dimension examined, one consistent divide emerged — members mainly ride for commuting, casual riders mostly use Cyclistic for leisure. This divide directly shapes the recommendations below.
