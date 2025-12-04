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

## Tech stack / Skills demonstrated
- Databricks (Unity Catalog, Volumes, Bronze/Silver/Gold architecture)
- PySpark (DataFrame API, transformations, aggregations)
- Delta Lake (optimized storage, ACID transactions)
- ETL design (ingestion → cleaning → aggregation)
- Git & GitHub workflow
- SQL (validation queries у Databricks SQL)
