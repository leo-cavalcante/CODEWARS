# **6KYU** - SELECT Prime Numbers
```sql
WITH series AS
  ( SELECT * FROM generate_series(2, 100) x)

SELECT series.x AS prime
FROM series
WHERE NOT EXISTS (
  SELECT 1 FROM series y
  WHERE series.x > y.x AND series.x % y.x = 0
  )
```