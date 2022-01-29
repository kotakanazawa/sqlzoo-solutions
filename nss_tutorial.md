## NSS Tutorial

[NSS Tutorial \- SQLZOO](https://sqlzoo.net/wiki/NSS_Tutorial)

### 1

```sql
SELECT A_STRONGLY_AGREE
  FROM nss
 WHERE question='Q01'
   AND institution='Edinburgh Napier University'
   AND subject='(8) Computer Science';
```

### 2

```sql
SELECT institution, subject
  FROM nss
 WHERE question='Q15'
   AND score >= 100;
```

### 3

```sql
SELECT institution, score
  FROM nss
 WHERE question='Q15'
   AND score < 50
   AND subject='(8) Computer Science';
```

### 4

```sql
SELECT
  subject,
  SUM(response)
FROM
  nss
WHERE
  question='Q22'
  AND (subject='(8) Computer Science'
  OR subject='(H) Creative Arts and Design')
GROUP BY
  subject
;
```

### 5

```sql
SELECT subject, SUM(A_STRONGLY_AGREE/100*response)
  FROM nss
 WHERE question='Q22'
   AND (subject='(H) Creative Arts and Design'
   OR subject='(8) Computer Science')
GROUP BY subject;
```
