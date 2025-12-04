# NYC Yellow Taxi ETL Pipeline (Databricks)

End-to-end ETL pipeline for NYC yellow taxi trips built in Databricks Community Edition.  
The pipeline reads raw taxi trips from Unity Catalog volumes (Bronze), cleans and enriches them (Silver) and produces aggregated Delta tables for analytics (Gold).

## Dataset

- NYC Yellow Taxi trip data for 2019-01 and 2019-02  
- Input files: compressed CSV files (`yellow_tripdata_2019-01.csv.gz`, `yellow_tripdata_2019-02.csv.gz`)  
- Storage: Unity Catalog volume in the **Bronze** layer

## Pipeline / Architecture

- **Bronze**  
  - Raw CSV files stored in a Unity Catalog volume  
  - No transformations applied at this stage

- **Silver**  
  - Load raw trips from Bronze  
  - Compute derived fields:
    - `trip_duration_min` – ride duration in minutes (from pickup and dropoff timestamps)
    - `pickup_hour` – hour of day for pickup
    - `pickup_dow` – day of week for pickup
    - `speed_mph` – average speed in miles per hour
  - Filter out invalid / extreme records (duration, distance, fare amount, unrealistic speed)
  - Save cleaned trips as a Delta table in the Silver layer

- **Gold**  
  - Build analytical aggregations from the cleaned Silver data:
    - `trips_by_hour` – trip counts and averages by pickup hour
    - `trips_by_dow` – trip counts and averages by day of week
    - `payment_stats` – trip counts, average total and average tip by payment type
    - `speed_by_hour` – distribution of average speed by pickup hour
    - `slowest_hours` – hours with the lowest average speed
    - `trip_length_buckets` – short / medium / long trips with basic stats
  - Store each aggregation as a separate Delta table in the Gold layer

## Technologies

- Databricks Community Edition
- PySpark (Spark DataFrame API)
- Spark SQL
- Unity Catalog & Volumes
- Delta Lake (Silver / Gold tables)

## Tech stack / Skills demonstrated

- Databricks:
  - Unity Catalog schemas and volumes
  - Bronze / Silver / Gold architecture
- PySpark:
  - DataFrame API
  - column expressions and derived features
  - filtering and data quality rules
  - groupBy + aggregations
- Delta Lake:
  - writing Delta tables for Silver and Gold layers
- SQL:
  - Spark SQL queries for validation and additional aggregations
- ETL design:
  - ingestion → cleaning → enrichment → aggregation
- Git & GitHub:
  - version control for the notebook and project structure
