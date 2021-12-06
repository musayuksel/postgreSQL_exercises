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

### Exercise 5

```sql
SELECT facid,SUM(slots) AS "Total Slots"
FROM cd.bookings
WHERE starttime >= '2012-09-01'
		AND starttime < '2012-10-01'
GROUP BY facid
ORDER BY "Total Slots"
```

### Exercise 6

```sql
SELECT facid,extract(month FROM starttime) AS month, SUM(slots) AS "Total Slots"
FROM cd.bookings
WHERE extract(year FROM starttime) = 2012
GROUP BY facid, month
ORDER BY facid, month
```

### Exercise 7

```sql
SELECT COUNT(*)
FROM cd.members
WHERE memid IN(SELECT DISTINCT(memid) FROM cd.bookings)
```

### Exercise 8

```sql
SELECT facid, SUM(slots) AS "Total Slots"
FROM cd.bookings
GROUP BY facid
HAVING SUM(slots) > 1000
ORDER BY facid
```

### Exercise 9

```sql
SELECT name, SUM(slots * CASE
  							WHEN memid = 0 then fc.guestcost
							  ELSE fc.membercost END) AS "revenue"
FROM cd.facilities fc
INNER JOIN cd.bookings bk
		ON bk.facid = fc.facid
GROUP BY fc.name
ORDER BY revenue
```
