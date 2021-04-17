# **6KYU** - SQL Basics: Simple WITH
```sql
WITH special_sales AS (SELECT department_id FROM sales WHERE price>90)
SELECT * FROM departments
WHERE departments.id IN (select * from special_sales)
```