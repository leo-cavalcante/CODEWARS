# **7KYU** - GROCERY STORE: Support Local Products
```sql
SELECT 
  country,
  count(id) as products
FROM products
WHERE country IN ('United States of America', 'Canada') 
GROUP BY country
ORDER BY products desc
```