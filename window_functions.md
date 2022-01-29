
## Window functions

[Window functions \- SQLZOO](https://sqlzoo.net/wiki/Window_functions)

```sql
SELECT lastName, party, votes
FROM ge
WHERE constituency = 'S14000024' AND yr = 2017
ORDER BY votes DESC;
```

### 2

```sql
SELECT
    party,
    votes,
    RANK() OVER (ORDER BY votes DESC) AS posn
FROM ge
WHERE constituency = 'S14000024' AND yr = 2017
GROUP BY party;
```

### 3

```sql
SELECT
    yr,
    party,
    votes,
    RANK() OVER (PARTITION BY yr ORDER BY votes DESC) AS posn
FROM ge
WHERE constituency = 'S14000021'
ORDER BY party, yr
```

### 4

```sql
SELECT
    constituency,
    party,
    votes,
    RANK() OVER (PARTITION BY constituency ORDER BY votes DESC) AS rankings
FROM ge
WHERE constituency BETWEEN 'S14000021' AND 'S14000026'
   AND yr  = 2017
ORDER BY rankings, constituency
```

### 5

```sql
SELECT
  constituency,
  party FROM (SELECT constituency,party, votes,RANK() OVER (PARTITION BY constituency ORDER BY votes DESC) AS r
FROM ge
WHERE
  constituency BETWEEN 'S14000021' AND 'S14000026'
  AND yr  = 2017
ORDER BY r, constituency) x
WHERE x.r=1;
```

### 6

```sql
SELECT
  party,
  count(1) FROM (SELECT constituency,party FROM (SELECT constituency,party, votes,RANK() OVER (PARTITION BY constituency ORDER BY votes DESC) AS r
FROM ge
WHERE
  constituency LIKE 'S%'
  AND yr  = 2017
ORDER BY r , constituency) x
WHERE x.r = 1) y
GROUP BY party
```
