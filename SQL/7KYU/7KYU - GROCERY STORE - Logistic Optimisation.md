# **7KYU** - GROCERY STORE: Logistic Optimisation
```sql
SELECT 
  producer,
  count(id) AS count_products_types
FROM products
GROUP BY producer
ORDER BY count_products_types DESC, producer
```