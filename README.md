# NYC Yellow Taxi ETL Pipeline (Databricks + Delta Lake)

This project involves the implementation of a complete ETL pipeline using the Databricks Community Edition.
The pipeline loads raw taxi data (Bronze), performs cleaning and transformations (Silver)
, and produces analytical aggregations that are stored as Delta tables.

## Architecture
- Bronze: raw input files uploaded to a Unity Catalog volume
- Silver: cleaned and standardized Delta tables
- Gold: aggregated metrics for analytics

## Technologies
- Databricks Community Edition
- PySpark
- Unity Catalog Volumes
- Delta Lake

## Files
- nyt_etl.py (full ETL notebook exported from Databricks)
