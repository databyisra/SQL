# NYC Bicycle - SQL Queries

This repository contains SQL queries completed as part of the Google Data Certifications program. The SQL queries are used to explore, analyze, and manipulate data from various datasets, including public datasets from Google BigQuery.

## Query 1: Retrieve End Station Name from Cycle Hire Dataset

### Problem:
The goal of this query is to retrieve the `end_station_name` for a specific bike rental (`rental_id`).

### Dataset:
- **Dataset**: `bigquery-public-data.london_bicycles.cycle_hire`
- **Table**: `cycle_hire`
- **Description**: This dataset contains information about bicycle hire transactions in London, including rental details such as start and end stations, timestamps, and more.

### SQL Query:
```sql
SELECT end_station_name
FROM `bigquery-public-data.london_bicycles.cycle_hire`
WHERE rental_id = 57635395;
