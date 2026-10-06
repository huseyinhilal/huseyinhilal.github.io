+++
date = '2026-01-03T02:17:27+03:00'
title = 'Testing the post and checking how to use'
+++

Today I have learned how to use double ORDER BY in sql. Basically what it does is it orders by the first condition and if any of the records have same value we can order them with some other condition. 
The logic is as follows:

```sql
SELECT *
FROM competition
WHERE age < 50
ORDER BY age DESC, avg_speed DESC
```

First we have ordered by ***age***, if there is two or more records have same age than it will order by ***avg_speed***.


Limit:
Limits the number of records


```sql
SELECT *
FROM table1
LIMIT 10
```
