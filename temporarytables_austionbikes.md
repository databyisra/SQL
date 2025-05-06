# 🚴‍♂️ 📊 From Raw Data to Insight: Using Temporary Tables for Bike Trip Analysis


This project analyzes the Austin Bikeshare dataset using SQL in Google BigQuery to explore bike usage behavior. It demonstrates the use of temporary tables (Common Table Expressions, or CTEs) to structure a multi-step query. Specifically, the workflow identifies the most-used bike by total ride duration, then determines which station it most frequently departs from—all within a clean and modular SQL statement.


---

### 📍 Dataset Location:
`bigquery-public-data.austin_bikeshare.bikeshare_trips`

---

### 📊 Dataset Structure

**bikeshare_trips table**
- 🆔 `bike_id`: Unique identifier for each bike  
- ⏱ `duration_minutes`: Duration of the trip in minutes  
- 📍 `start_station_id`: Station where the trip started  
- 📅 `start_time`, `end_time`: Timestamps of the trip  

---

## 🧪 Combined SQL Workflow — Longest-Used Bike + Most Frequent Start Station

```sql
WITH longest_used_bike AS (
  -- Step 1 & 2: Identify the bike with the longest total ride time
  SELECT
    bike_id,
    SUM(duration_minutes) AS trip_duration
  FROM
    bigquery-public-data.austin_bikeshare.bikeshare_trips
  GROUP BY
    bike_id
  ORDER BY
    trip_duration DESC
  LIMIT 1
)

-- Step 3: Use that bike ID to find the station it starts from most often
SELECT
  trips.start_station_id,
  COUNT(*) AS trip_ct
FROM
  longest_used_bike AS longest
JOIN
  bigquery-public-data.austin_bikeshare.bikeshare_trips AS trips
ON
  longest.bike_id = trips.bike_id
GROUP BY
  trips.start_station_id
ORDER BY
  trip_ct DESC
LIMIT 1;
