# **4KYU** - Challenge - Two actors who cast together the most
```sql
WITH actors_together AS
  (SELECT fa1.film_id, fa1.actor_id as actor1, fa2.actor_id as actor2,
     count(*) OVER (PARTITION BY fa1.actor_id, fa2.actor_id) AS films_together
  FROM film_actor fa1, film_actor fa2
  WHERE fa1.film_id = fa2.film_id AND fa1.actor_id <> fa2.actor_id
  ),
top_actors AS
  (SELECT * FROM actors_together
  WHERE films_together = (SELECT MAX(films_together) FROM actors_together)
  limit (SELECT MAX(films_together) FROM actors_together)),

final_table_with_duplicates AS
  (SELECT
    a1.first_name || ' ' || a1.last_name as first_actor,
    a2.first_name || ' ' || a2.last_name as second_actor,
    f1.title AS title
  FROM top_actors ta
  JOIN actor a1 ON actor1 = a1.actor_id
  JOIN actor a2 ON actor2 = a2.actor_id
  JOIN film_actor fa1 ON ta.actor1 = fa1.actor_id
  JOIN film f1 ON f1.film_id = fa1.film_id
  JOIN film_actor fa2 ON ta.actor2 = fa2.actor_id
  JOIN film f2 ON f2.film_id = fa2.film_id
  WHERE fa1.film_id = fa2.film_id)

SELECT
  DISTINCT ON (first_actor, second_actor, title)
  first_actor, second_actor, title
FROM final_table_with_duplicates
```