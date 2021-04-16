# **6KYU** - SQL Basics: Top 10 customers by total payments amount
```sql
SELECT
  c.customer_id,
  c.email,
  COUNT(payment_id) as payments_count,
  SUM(amount)::FLOAT AS total_amount
FROM customer c
JOIN payment p
ON c.customer_id = p.customer_id
GROUP BY c.customer_id, c.email
ORDER BY total_amount DESC
LIMIT 10
```