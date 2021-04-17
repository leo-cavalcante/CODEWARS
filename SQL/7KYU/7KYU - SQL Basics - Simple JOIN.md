# **7KYU** - SQL Basics: Simple JOIN
```sql
SELECT p.id, p.name, p.isbn, p.company_id, c.name as company_name, p.price
FROM products p
JOIN companies c
ON p.company_id = c.id
```