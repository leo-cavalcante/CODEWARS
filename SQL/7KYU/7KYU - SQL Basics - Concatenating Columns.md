# **7KYU** - SQL: Concatenating Columns
```sql
SELECT
  prefix || ' ' || first || ' ' || last || ' ' || suffix AS title
FROM names
```