# **7KYU** - SQL - RIGHT and LEFT
```sql
SELECT
  LEFT(project, commits) as project,
  RIGHT(address, contributors) as address
FROM repositories
```