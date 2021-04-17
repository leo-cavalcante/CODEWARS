# **5KYU** - Using LATERAL JOIN To Get Top N per Group
```sql
select categories.id as category_id, category, title,
views, post_id
from categories
left join lateral
  (select id as post_id, category_id, title, views
   from posts
   where posts.category_id = categories.id
   order by views desc, post_id
   limit 2) as posts
on categories.id = posts.category_id
order by categories.category asc, views desc, post_id asc
```