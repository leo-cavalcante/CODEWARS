# **5KYU** - Using Window Functions To Get Top N per Group
```sql
SELECT category_id, category, title, views, post_id
FROM
  (SELECT
    categories.id AS category_id,
    category,
    posts.id AS post_id,
    title,
    SUM(views) OVER (PARTITION BY category_id, posts.id, title ORDER BY SUM(views) ASC) AS views,
    DENSE_RANK() OVER (PARTITION BY category_id ORDER BY SUM(views) DESC, posts.id ASC) AS ranking
  FROM posts
  RIGHT JOIN categories ON categories.id = posts.category_id
  GROUP BY categories.id, category, posts.id, title) AS ranked_posts
WHERE ranking <=2
ORDER BY category, views DESC, post_id ASC
```