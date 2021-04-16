# **6KYU** - SQL Basics: Simple NULL handling
```sql
SELECT
  id,
  COALESCE(NULLIF(name,''), '[product name not found]') as name,
  price,
  COALESCE(NULLIF(card_name,''), '[card name not found]') as card_name,
  card_number,
  transaction_date
FROM eusales
WHERE price IS NOT null
AND price>50
```