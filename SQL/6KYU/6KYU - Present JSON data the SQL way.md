# **6KYU** - Present JSON data the SQL way
```sql
WITH cleaned_users AS
(SELECT
  id,
  data->>'first_name' as first_name,
  data->>'last_name' as last_name,
  data->>'date_of_birth' as date_of_birth,
  data#>>'{email_addresses,0}' as email_addresses,
  data->>'private' as private
FROM users)
SELECT
  first_name,
  last_name,
  EXTRACT(YEAR FROM AGE(NOW(),DATE(date_of_birth)))::int AS age,
  CASE WHEN private='true' THEN 'Hidden'
       WHEN email_addresses IS NULL THEN 'None'
       ELSE email_addresses
       END AS email_address
FROM cleaned_users
ORDER BY first_name, last_name
```