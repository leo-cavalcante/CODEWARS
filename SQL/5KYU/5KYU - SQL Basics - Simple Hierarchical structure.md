# **5KYU** - SQL Basics: Simple Hierarchical structure
```sql
WITH RECURSIVE employee_levels AS
(
  SELECT 1 as level, id, first_name, last_name, manager_id
  FROM employees
  WHERE manager_id is null

UNION ALL

  SELECT el.level+1, e.id, e.first_name, e.last_name, e.manager_id
  FROM employees e, employee_levels el
  WHERE e.manager_id = el.id
)
SELECT * FROM employee_levels;
```