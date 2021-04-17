# **6KYU** - SQL Basics: Simple IN
```sql
SELECT id, name FROM departments
where departments.id in (SELECT department_id FROM sales where price>98)
```