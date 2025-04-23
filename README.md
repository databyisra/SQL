Google Data Certifications - SQL Queries
This repository contains SQL queries completed as part of the Google Data Certifications program. The SQL queries are used to explore, analyze, and manipulate data from various datasets, including public datasets from Google BigQuery.

NYC Bicycle - SQL Queries
Query 1: Retrieve End Station Name from Cycle Hire Dataset
Problem:
The goal of this query is to retrieve the end_station_name for a specific bike rental (rental_id).

Dataset:
Dataset: bigquery-public-data.london_bicycles.cycle_hire

Table: cycle_hire

Description: This dataset contains information about bicycle hire transactions in London, including rental details, start and end stations, timestamps, and more.

SQL Query:
sql
Copy
Edit
SELECT end_station_name
FROM `bigquery-public-data.london_bicycles.cycle_hire`
WHERE rental_id = 57635395;
Solar Potential - SQL Queries
Query 2: Retrieve Solar Potential Data for Pennsylvania
Problem:
The goal of this query is to retrieve solar potential data for the state of Pennsylvania.

Dataset:
Dataset: bigquery-public-data.sunroof_solar.solar_potential_by_postal_code

Table: solar_potential_by_postal_code

Description: This dataset contains information about the solar potential for different postal codes across the United States. It includes estimates of how much energy can be produced from solar panels installed at various locations, along with other data points related to solar energy potential.

SQL Query:
sql
Copy
Edit
SELECT *
FROM `bigquery-public-data.sunroof_solar.solar_potential_by_postal_code`
WHERE state_name = 'Pennsylvania';
