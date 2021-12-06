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

### Exercise 4

```sql
SELECT facid, SUM(slots) AS "Total Slots"
FROM cd.bookings
GROUP BY facid
ORDER BY facid;
```
