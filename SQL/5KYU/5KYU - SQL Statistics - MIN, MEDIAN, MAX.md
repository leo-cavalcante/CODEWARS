# **5KYU** - SQL Statistics: MIN, MEDIAN, MAX
```sql
SELECT
    MIN(score),
    CAST(((SELECT MAX(score) FROM
        (SELECT score FROM result ORDER BY score LIMIT 50) AS BottomHalf) + (SELECT MIN(score) FROM
        (SELECT score FROM result ORDER BY score DESC LIMIT 50) AS TopHalf)) AS FLOAT)/2 AS median, 
    MAX(score)
FROM result
```