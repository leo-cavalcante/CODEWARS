# **6KYU** - SQL Basics: Simple table totaling.
```sql
SELECT
  RANK() OVER (ORDER BY SUM(points) DESC) AS rank,
  COALESCE(NULLIF(clan,''),'[no clan specified]') AS clan,
  SUM(points) AS total_points,
  count(people) AS total_people
FROM people
GROUP BY COALESCE(NULLIF(clan,''),'[no clan specified]')
ORDER BY 1 ASC
```