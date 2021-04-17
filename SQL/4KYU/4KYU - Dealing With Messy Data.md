# **4KYU** - Dealing With Messy Data
```sql
WITH new_customers AS
  (SELECT first_name, last_name,
    UPPER(first_name) || ' ' || UPPER(last_name) AS first_last,
    UPPER(last_name) || ', ' || UPPER(first_name) AS last_first,
    credit_limit as old_limit
  FROM customers),
  
 new_prospects AS
  (SELECT
    full_name,
    REGEXP_REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(UPPER(TRIM(full_name)), 'MRS. ',''), 'MR. ',''), 'DR. ',''), 'MS. ',''), 'MISSES ',''), 'MISTER ',''), 'MISS ',''), 'DOCTOR ',''), ' JR.',''), ' SR.',''), ' DVM',''), ' MD',''), ' PHD',''), ' DDS',''), '\s[I]*[V]*$', '')  as full_name_modified, 
    credit_limit AS new_limit
  FROM prospects),
  
union_all AS
  (SELECT first_name, last_name, old_limit, new_limit
  FROM new_customers nc
  JOIN new_prospects np
  ON nc.first_last = np.full_name_modified
  
  UNION ALL
  
  SELECT first_name, last_name, old_limit, new_limit
  FROM new_customers nc
  JOIN new_prospects np
  ON nc.last_first = np.full_name_modified
  )

SELECT first_name, last_name, old_limit, max_new_limit AS new_limit FROM
  (SELECT
    first_name,
    last_name,
    old_limit,
    new_limit,
    MAX(new_limit) OVER (PARTITION BY first_name, last_name, old_limit) as max_new_limit
  FROM union_all
  WHERE new_limit > old_limit
  ORDER BY 1,2) AS final_table
WHERE new_limit = max_new_limit;
```