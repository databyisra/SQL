# Solar Potential in Pennsylvania – BigQuery Exploration

This project explores solar potential by ZIP code in the state of **Pennsylvania** using data from Google’s Project Sunroof via the BigQuery public datasets.

##  Query Overview

We query the `bigquery-public-data.sunroof_solar.solar_potential_by_postal_code` table to extract all available solar potential data specific to Pennsylvania.

### SQL Used:
```sql
SELECT *
FROM `bigquery-public-data.sunroof_solar.solar_potential_by_postal_code`
WHERE state_name = 'Pennsylvania';
