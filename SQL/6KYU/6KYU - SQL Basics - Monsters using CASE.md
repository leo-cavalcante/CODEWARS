# **6KYU** - SQL Basics: Monsters using CASE
```sql
SELECT
  th.id,
  heads,
  legs,
  arms,
  tails,
  CASE WHEN (heads>arms OR tails>legs) THEN 'BEAST' ELSE 'WEIRDO' END AS species
FROM top_half as th
JOIN bottom_half AS bh
ON th.id = bh.id
ORDER BY species
```