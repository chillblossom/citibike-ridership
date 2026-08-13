# citibike-ridership
# Citibike Ridership

A data analytics project exploring Citibike ridership and building a model of trends to understand what drives daily ridership.

## Repo structure

- `code/` — Jupyter notebooks: `eda.ipynb` (exploratory analysis), `preprocessing.ipynb` (data cleaning/prep), `model.ipynb` (model building/evaluation)
- `data/` — exported CSV dataset(s) used in this project
- `queries/` — final SQL queries used to pull/shape the data
- `docs/` — data dictionary and supporting notes

## Data

Daily-level data (~1,610 days, July 2013–May 2018) combining Citibike trip counts with NOAA GSOD weather observations for NYC, built via SQL joins in BigQuery. See `queries/` for the extraction logic and `docs/` for the full data dictionary.

## Key EDA findings

- *System growth outweighs weather.* Identical weather and day-of-week return very different ridership in different years. The average July ridership more than doubled from ~27,000 rides/day in 2013 to ~56,000 in 2017, due to the system itself expanding (more stations, more bikes, more members). A model using only weather and day-of-week has no way to see this, so a trend feature (year or days-since-launch) is essential.
- *A 6-month data gap.* 186 of 1,796 calendar days in the range are missing from the dataset, almost entirely as one contiguous block: October 2016 through March 2017. This lines up with a likely NOAA weather-station reporting gap rather than a Citibike outage, and means the model has no training data at all for that winter.
- *A coded missing value in precipitation.* One row (2016-02-11) carries `precip_in = 99.99`, which is NOAA GSOD's sentinel code for "no observation" rather than an actual data, addressed in preprocessing rather than treated as a real value.
- *(EDA on the temperature/precipitation relationship to ridership — in progress)*


## Status

In progress — Part 1 (repo scaffolding) complete. Part 2 (analysis + write-up) coming soon.
EDA — data quality issues, missing-data patterns, system growth trend
EDA — weather/ridership relationships
Preprocessing — cleaning, encoding, feature engineering
Modeling — linear regression, evaluation, interpretation
