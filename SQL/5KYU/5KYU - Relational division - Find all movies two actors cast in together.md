# **5KYU** - Relational division: Find all movies two actors cast in together
```sql
SELECT title FROM film
WHERE film_id in (SELECT film_id FROM film_actor WHERE actor_id = 105)
AND film_id in (SELECT film_id FROM film_actor WHERE actor_id = 122)
```