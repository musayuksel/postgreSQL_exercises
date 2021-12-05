# https://pgexercises.com/questions/aggregates/

### Exercise 1

```sql
SELECT COUNT(*)
FROM cd.facilities;
```

### Exercise 2

```sql
SELECT COUNT(*)
FROM cd.facilities
WHERE guestcost >= 10;
```

### Exercise 3

```sql
SELECT recommendedby , COUNT(*)
FROM cd.members
WHERE recommendedby IS NOT NULL
GROUP BY  recommendedby
ORDER BY recommendedby ASC;
```
