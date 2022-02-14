# Join

## Case

- Inner Join
- Outer Join
  - Left Outer Join
  - Right Outer Join
  - Full Outer Join

### Inner Join

```sql

SELECT 
FROM DEPT

```



## Outer join

### (+) Operator (Oracle)

> FROM 절의 복잡성을 줄이기 위해 사용

```sql

SELECT A.*, B.*
FROM A, B
WHERE A(+).data = B.data

SELECT A.*, B.*
FROM A LEFT OUTER JOIN B
ON A.data = B.data

```
