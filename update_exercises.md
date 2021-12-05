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
