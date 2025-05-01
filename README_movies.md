## 🎯 Project Goals

This project demonstrates how SQL can be used to:

- Filter movies by genre
- Identify high-grossing movies
- Sort results by release date
- Gain insights into trends within a specific genre

---

## 🧾 SQL Queries Used

### 🔹 Query 1: All Comedy Movies (Sorted by Release Date)

```sql
SELECT 
  *
FROM 
  `bold-artifact-458415-p5.movie_data.movies` 
WHERE
  Genre = "Comedy"
ORDER BY 
  `Release Date` DESC;
Purpose:
Retrieve all comedy movies and list them from the most recent to the oldest, showing how comedy films have evolved over time.

🔹 Query 2: High-Grossing Comedy Movies
sql
Copy
Edit
SELECT 
  *
FROM 
  `bold-artifact-458415-p5.movie_data.movies` 
WHERE
  Genre = "Comedy"
  AND Revenue > 300000000
ORDER BY
  `Release Date` DESC;

---
Purpose:
Focus on comedy movies that earned more than $300 million, sorted by release date. This highlights the most commercially successful comedies.

---
🛠️ Key SQL Concepts
SELECT *: Selects all available fields from the table.

WHERE Genre = "Comedy": Filters rows to only comedy movies.

AND Revenue > 300000000: Adds a revenue-based filter.

ORDER BY Release Date DESC: Sorts results to show recent movies first.

