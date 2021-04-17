# **7KYU** - SQL Basics: Truncating
```sql
SELECT
  CASE WHEN (number1 + number2)>0 THEN FLOOR(number1 + number2)
       ELSE CEILING(number1 + number2) END
  AS towardzero
FROM decimals
```