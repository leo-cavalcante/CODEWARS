# **5KYU** - SQL Basics: Group By Day
```sql
select date(created_at) as day, description, count(distinct id) from events
group by date(created_at), name, description
having name='trained'
```