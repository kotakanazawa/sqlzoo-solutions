## SELECT within SELECT Tutorial

[SELECT within SELECT Tutorial \- SQLZOO](https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial)

### 1

```sql
SELECT name FROM world
WHERE population >
   (SELECT population FROM world
    WHERE name='Russia');
```

### 2

```sql
SELECT name FROM world
WHERE continent = 'Europe'
AND gdp/population > (SELECT gdp/population FROM world WHERE name = 'United Kingdom');
```

### 3

```sql
SELECT
  name,
  continent
FROM world
WHERE continent IN (SELECT continent FROM world WHERE name = 'Argentina' OR name = 'Australia')
ORDER BY name;
```

### 4

```sql
SELECT
  name,
  population
FROM world
WHERE population > (SELECT population FROM world WHERE name = 'Canada')
AND population < (SELECT population FROM world WHERE name = 'Poland');
```

### 5

```sql
SELECT
  name,
  CONCAT(ROUND(population/(SELECT population FROM world WHERE name = 'Germany')*100, 0),'%')
FROM world
WHERE continent = 'Europe';
```

### 6

```sql
SELECT
  name
FROM
  world
WHERE
  gdp > ALL(SELECT MAX(gdp) FROM world WHERE continent = 'Europe')
;
```

`ALL` is used to select all records of a SELECT statment. It compares a value to every value in a list or results from a query.

### 7

```sql
SELECT
  continent,
  name,
  area
FROM world x
WHERE area >= ALL(SELECT area FROM world y WHERE y.continent=x.continent);
```

### 8

```sql
SELECT
  continent,
  MIN(name)
FROM world
GROUP BY continent;
```

### 9

```sql
SELECT
  name,
  continent,
  population
FROM world A
WHERE 25000000 >= ALL
  (
    SELECT
      population
    FROM
      world B
    WHERE A.continent = B.continent
  )
;
```

### 10

```sql
SELECT
  name,
  continent
FROM world A
WHERE population > ALL
  (
    SELECT
      population * 3
    FROM world B
    WHERE
      A.continent = B.continent
    AND NOT A.name = B.name
  )
;
```
