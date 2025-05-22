# 📈 SQL Subqueries – FDA Hospitalization Analysis

This project explores food safety incident data using **SQL** in **Google BigQuery**. It identifies the **top 10 food industry categories** most frequently linked to **hospitalization events**, leveraging **subqueries**, **filtering**, and **pattern matching** techniques.

**Dataset location:**  
`bigquery-public-data.fda_food.food_events`

---

## Dataset Overview

**food_events table**

-  `report_number`: Unique ID for each FDA event report  
-  `products_industry_name`: Category of the reported food product  
- `outcomes`: Description of the health result (e.g., Hospitalization, Death)

---

## SQL Query  

### Query — Top 10 Food Industries by Hospitalization Count

**Query Code:**

```sql
SELECT 
  products_industry_name, 
  COUNT(report_number) AS count_hospitalizations
FROM
  bigquery-public-data.fda_food.food_events
WHERE products_industry_name IN (
    SELECT 
      products_industry_name
    FROM 
      bigquery-public-data.fda_food.food_events
    GROUP BY products_industry_name
    ORDER BY COUNT(report_number) DESC
    LIMIT 10
)
AND outcomes LIKE '%Hospitalization%'
GROUP BY products_industry_name
ORDER BY count_hospitalizations DESC;
----
🎯 Purpose 
This query is designed to:

- Focus on the top 10 industries based on total event volume

- Filter for cases that mention "Hospitalization" in the outcome

- Count and rank industries by the number of hospitalization reports

🧠 SQL Concepts Demonstrated:
- Subqueries inside WHERE IN clauses

- Pattern matching using LIKE '%Hospitalization%'

📈 Aggregation with COUNT() and GROUP BY

📌 Ranking results using ORDER BY and LIMIT

