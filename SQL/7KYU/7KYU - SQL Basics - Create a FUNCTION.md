# **7KYU** - SQL Basics: Create a FUNCTION
```sql
CREATE FUNCTION increment(age integer)
RETURNS integer AS $$
BEGIN
  RETURN (SELECT age + 1)::int;
END;
 $$ LANGUAGE plpgsql;
```