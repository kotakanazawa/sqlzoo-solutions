## SELECT from WORLD Tutorial
[SELECT from WORLD Tutorial \- SQLZOO](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)
### 1

```sql
SELECT name, continent, population FROM world;
```

### 2

```sql
SELECT name FROM world
WHERE population > 200000000;
```

### 3

```sql
SELECT name, gdp/population
FROM world
WHERE population > 200000000;
```

### 4

```sql
SELECT name, population/1000000
FROM world
WHERE continent = 'South America';
```

### 5

```sql
SELECT name, population
FROM world
WHERE name IN ('France','Germany', 'Italy');
```

### 6

```sql
SELECT name
FROM world
WHERE name LIKE '%United%';
```

### 7

```sql
SELECT name, population, area
FROM world
WHERE population > 250000000
OR area > 3000000;
```

### 8

```sql
SELECT name, population, area
FROM world
WHERE population > 250000000
XOR area > 3000000;
```

### 9

```sql
SELECT
  name,
  ROUND(population/1000000,2),
  ROUND(gdp/1000000000,2)
FROM world
WHERE continent = 'South America'
```

### 10

```sql
SELECT name, ROUND(gdp/population, -3)
FROM world
WHERE gdp > 1000000000000;
```

### 11

```sql
SELECT name, capital
FROM world
WHERE length(name) = length(capital);
```

### 12

```sql
SELECT name, capital
FROM world
WHERE LEFT(name, 1) = LEFT(capital, 1)
AND name <> capital;
```

### 13

```sql
SELECT name
FROM world
WHERE name LIKE '%a%'
  and name LIKE '%e%'
  and name LIKE '%i%'
  and name LIKE '%o%'
  and name LIKE '%u%'
  and name NOT LIKE '% %';
```

This looks a bit ugly and there must be a better way to execute the query with regular expression.
