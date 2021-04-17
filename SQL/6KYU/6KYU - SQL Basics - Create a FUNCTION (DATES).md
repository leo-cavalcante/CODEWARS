# **6KYU** - SQL Basics: Create a FUNCTION (DATES)
```sql
CREATE FUNCTION agecalculator (numb timestamp) 
RETURNS integer AS $$
BEGIN
  RETURN (SELECT EXTRACT(year FROM age(numb)))::int;
END;
 $$ LANGUAGE plpgsql;
```