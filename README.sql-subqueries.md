# 🧬 Mastering SQL Subqueries – NYC Mobility Dataset

This project explores public Citi Bike trip data from New York City using **SQL in Google BigQuery**. It focuses on understanding **trip duration trends** by station and detecting **trip outliers** that deviate significantly from station averages.

Dataset location:  
`bigquery-public-data.new_york_citibike.citibike_trips`

---

## 📊 Dataset Structure

**citibike_trips table**
- `tripduration`: Duration of the trip (in seconds)  
- `starttime`: Trip start timestamp  
- `start_station_id`: ID of the station where the trip started  
- `end_station_id`: ID of the ending station  
- `usertype`: Subscriber or customer classification  

---

## 🧪 SQL Queries

### 🔹 Query 1 & 2 — **Trips with Above-Average Duration (by Station) and Station Ranking by Average Duration**

#### Combined Query Code:

```sql
-- Query 1: Trips with Above-Average Duration (by Station)
SELECT
  starttime,
  start_station_id,
  tripduration,
  (
    SELECT ROUND(AVG(tripduration), 2)
    FROM `bigquery-public-data.new_york_citibike.citibike_trips`
    WHERE start_station_id = outer_trips.start_station_id
  ) AS avg_duration_for_station, 
  ROUND(
    tripduration - (
      SELECT AVG(tripduration)
      FROM `bigquery-public-data.new_york_citibike.citibike_trips`
      WHERE start_station_id = outer_trips.start_station_id
    ),
    2
  ) AS difference_from_avg
FROM `bigquery-public-data.new_york_citibike.citibike_trips` AS outer_trips
ORDER BY difference_from_avg DESC
LIMIT 25;

-- Query 2: Stations with the Longest Average Trip Durations
SELECT  
  subquery.start_station_id,
  subquery.avg_duration
FROM (
    SELECT
      start_station_id,
      AVG(tripduration) AS avg_duration
    FROM
      `bigquery-public-data.new_york_citibike.citibike_trips`
    GROUP BY
      start_station_id
) AS subquery
ORDER BY
  subquery.avg_duration DESC;
🔍 Purpose:
Query 1 identifies the top 25 trips where the duration exceeds the average for that starting station. This is useful for detecting:

Outlier trips (e.g., recreational detours or data errors)

Stations where unusual behavior may occur

Query 2 ranks all start stations by their average trip duration, helping to identify:

Stations used for longer rides (e.g., scenic areas or longer commutes)

Potential urban trends by location
