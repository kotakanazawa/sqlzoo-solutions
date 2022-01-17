## SELECT basics

### 1

```sql
SELECT population FROM world
WHERE name = 'Germany';
```

### 2

```sql
SELECT name, population FROM world
WHERE name IN ('Sweden', 'Norway', 'Denmark');
```

### 3

```sql
SELECT name, area FROM world
WHERE area BETWEEN 200000 AND 250000;
```
