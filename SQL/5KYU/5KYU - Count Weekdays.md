# **5KYU** - Count Weekdays
```sql
CREATE FUNCTION weekdays(date_1 DATE, date_2 DATE)
RETURNS integer AS $$
BEGIN
  RETURN (select
          sum(case when extract(dow from dt)::int in (1,2,3,4,5) then 1 else 0 end) as weekdays
          from generate_series(least(date_1,date_2), greatest(date_1,date_2), '1 day'::interval) as dt
          )::int;
END;
$$ LANGUAGE plpgsql;
```