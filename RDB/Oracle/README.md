# Oracle

## Syntax

### Join

#### Outer join

##### (+) Operator

> FROM 절의 복잡성을 줄이기 위해 사용

```bash
SELECT A.*, B.*
FROM A, B
WHERE A(+).data = B.data

SELECT A.*, B.*
FROM A LEFT OUTER JOIN B
ON A.data = B.data
```

