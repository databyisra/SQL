# 🔗 SQL Joins with BigQuery – Employee & Department Data

This project demonstrates how to use SQL join types—**INNER**, **LEFT**, **RIGHT**, and **FULL OUTER**—in **Google BigQuery** to connect employee records with department data.

Dataset location:
bold-artifact-458415-p5.employee_data

pgsql
Copy
Edit

---

## Dataset Structure

**employees table**
- `name`: Employee name  
- `role`: Job title  
- `department_id`: Department identifier  

**departments table**
- `department_id`: Unique department identifier  
- `name`: Department name  

---

##  Join Types & Queries

###  LEFT JOIN – All Employees (with or without a department)

```sql
SELECT
  employees.name AS employee_name,
  employees.role AS employee_role,
  departments.name AS department_name
FROM
  `bold-artifact-458415-p5.employee_data.employees` AS employees
LEFT JOIN
  `bold-artifact-458415-p5.employee_data.departments` AS departments
ON employees.department_id = departments.department_id;
🔍 Purpose: Returns all employees, even if they don't belong to a department. Unmatched departments show as NULL.

🔹 INNER JOIN – Employees with a Matching Department
  employees.name AS employee_name,
  employees.role AS employee_role,
  departments.name AS department_name
FROM
  `bold-artifact-458415-p5.employee_data.employees` AS employees
INNER JOIN
  `bold-artifact-458415-p5.employee_data.departments` AS departments
ON employees.department_id = departments.department_id;
🔍 Purpose: Returns only employees who are assigned to a department.

🔹 RIGHT JOIN – All Departments (even if no employees are assigned)
SELECT
  employees.name AS employee_name,
  employees.role AS employee_role,
  departments.name AS department_name
FROM
  `bold-artifact-458415-p5.employee_data.employees` AS employees
RIGHT JOIN
  `bold-artifact-458415-p5.employee_data.departments` AS departments
ON employees.department_id = departments.department_id;
🔍 Purpose: Returns all departments. If a department has no employees, those fields will be NULL.

🔹 FULL OUTER JOIN – All Employees and All Departments
SELECT
  employees.name AS employee_name,
  employees.role AS employee_role,
  departments.name AS department_name
FROM
  `bold-artifact-458415-p5.employee_data.employees` AS employees
FULL OUTER JOIN
  `bold-artifact-458415-p5.employee_data.departments` AS departments
ON employees.department_id = departments.department_id;
🔍 Purpose: Returns all employees and departments—even when there's no match between them.

🧠 SQL Concepts Highlighted
LEFT JOIN: Includes all records from the left table, and matched rows from the right

INNER JOIN: Includes only records with matches in both tables

RIGHT JOIN: Includes all records from the right table, and matched rows from the left

FULL OUTER JOIN: Includes all records from both tables, matched and unmatched
