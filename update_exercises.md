# https://pgexercises.com/questions/updates

### Exercise 1

```sql
INSERT INTO cd.facilities
(facid,name,membercost,guestcost,initialoutlay, monthlymaintenance)
VALUES(9,'Spa',20,30,100000,800);
```

### Exercise 2

```sql
INSERT INTO cd.facilities
(facid,name,membercost,guestcost,initialoutlay, monthlymaintenance)
VALUES (9,'Spa',20,30,100000,800),
        (10, 'Squash Court 2', 3.5, 17.5, 5000, 80);
```

### Exercise 3

```sql
INSERT INTO cd.facilities
(facid,name,membercost,guestcost,initialoutlay, monthlymaintenance)
SELECT (SELECT MAX(facid) from cd.facilities)+1,'Spa',20,30,100000,800;
-- Since the VALUES clause is only used to supply constant data, we need to replace it with a query instead. The SELECT statement is fairly simple: there's an inner subquery that works out the next facid based on the largest current id, and the rest is just constant data. The output of the statement is a row that we insert into the facilities table.
```

### Exercise 4

```sql
UPDATE cd.facilities
SET initialoutlay = 10000
WHERE name = 'Tennis Court 2';
```

### Exercise 5

```sql
UPDATE cd.facilities
SET membercost = 6, guestcost = 30
WHERE name LIKE 'Tennis Court%';
```

### Exercise 6

```sql
UPDATE cd.facilities
SET membercost = (SELECT membercost FROM cd.facilities WHERE name = 'Tennis Court 1' ) *1.1,
 guestcost = (SELECT guestcost FROM cd.facilities WHERE name = 'Tennis Court 1' )*1.1
WHERE name = 'Tennis Court 2';
-- OR
update cd.facilities t2
    set
        membercost = t1.membercost * 1.1,
        guestcost = t1.guestcost * 1.1
    from (select membercost,guestcost from cd.facilities where name = 'Tennis Court 1') t1
    where t2.facid = 1;
```

### Exercise 7

```sql
DELETE FROM cd.bookings;
```

### Exercise 8

```sql
DELETE FROM cd.members
WHERE memid = 37;
```

### Exercise 9

```sql
DELETE FROM cd.members
WHERE memid NOT IN (SELECT memid
                    FROM cd.bookings);
```
