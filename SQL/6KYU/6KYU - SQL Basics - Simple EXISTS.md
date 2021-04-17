# **6KYU** - SQL Basics: Simple EXISTS
```sql
SELECT *
FROM departments
WHERE EXISTS (SELECT department_id FROM sales
              WHERE departments.id = sales.department_id
              AND price>98)
```