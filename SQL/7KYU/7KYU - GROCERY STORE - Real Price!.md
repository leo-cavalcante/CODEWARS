# **7KYU** - GROCERY STORE: Real Price!
```sql
SELECT
  name,
  weight,
  price,
  ROUND((1000*price/weight)::numeric,2)::float AS price_per_kg
FROM products
ORDER BY price_per_kg, name
```