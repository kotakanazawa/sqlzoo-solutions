## SELECT from Nobel Tutorial

[SELECT from Nobel Tutorial \- SQLZOO](https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial)

### 1

```sql
SELECT yr, subject, winner FROM nobel
WHERE yr = 1950;
```

### 2

```sql
SELECT winner FROM nobel
WHERE yr = 1962
  AND subject = 'Literature';
```

### 3

```sql
SELECT yr, subject FROM nobel
WHERE winner = 'Albert Einstein';
```

### 4

```sql
SELECT winner FROM nobel
WHERE yr >= 2000
  AND subject = 'Peace';
```

### 5

```sql
SELECT * FROM nobel
WHERE yr BETWEEN 1980 and 1989
  AND subject = 'Literature';
```

### 6

```sql
SELECT * FROM nobel
WHERE winner IN ('Theodore Roosevelt',
                  'Woodrow Wilson',
                  'Jimmy Carter',
                  'Barack Obama');
```

### 7

```sql
SELECT winner FROM nobel
WHERE winner LIKE 'John%';
```

### 8

```sql
SELECT yr, subject, winner FROM nobel
WHERE (subject = 'Physics' AND yr = 1980)
  OR (subject = 'Chemistry' AND yr = 1984);
```

### 9

```sql
SELECT yr, subject, winner FROM nobel
WHERE yr = 1980
  AND subject NOT IN ('Chemistry','Medicine');
```

### 10

```sql
SELECT * FROM nobel
WHERE (subject = 'Medicine' AND yr < 1910)
  OR (subject = 'Literature' AND yr >= 2004);
```

### 11

```sql
SELECT * FROM nobel
WHERE winner = 'PETER GRÜNBERG';
```

### 12

```sql
SELECT * FROM nobel
WHERE winner = 'EUGENE O''NEILL';
```

You can use single quote to escape single quotes within a quoted string.

### 13

```sql
SELECT winner, yr, subject FROM nobel
WHERE winner LIKE 'Sir%'
ORDER BY yr DESC, winner;
```
