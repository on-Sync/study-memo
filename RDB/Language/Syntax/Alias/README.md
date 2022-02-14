# Alias

## How

```sql

-- default
SELECT eid TEST_ID
FROM ENTITY_TABLE;

-- keyword
SELECT eid AS TEST_ID
FROM ENTITY_TABLE;

-- quotation (for white-space)
SELECT eid "TEST D"
FROM ENTITY_TABLE;

-- quotation + keyword
SELECT eid AS "TEST ID"
FROM ENTITY_TABLE;

```

> Note : 2022.01 기준 IntelliJ 를 사용할 때, Native Query 가 복잡해지면 IDE 가 `FROM` 절의 `AS` keyword 방식을 인식하지 못했다. 이 경우, 실행시 차이점은 확인하지 않았으나, SQL 디자인이 적용이 안되어 가독성이 취약해졌다. FROM 절의 경우, `sub-query` 에도 Alias 가 사용될 수 있다. 그렇다 하더라도 IDE 가 `default` 형태만을 인식하는 것은 IntelliJ 에 임의의 버그가 존재하는 것으로 생각된다.

## Whom

```sql

-- SELECT
SELECT eid "TEST"
FROM ENTITY_TABLE;

-- FROM
SELECT eid
FROM ENTITY_TABLE "TEST_TABLE";

```

## When

```sql

-- string concat
SELECT eid || ' ' ename AS "TEST_ENTITY"
FROM ENTITY_TABLE

-- group function
SELECT eid, COUNT(edata) AS "Summary by ID"
FROM ENTITY_TABLE
GROUP BY ENTITY_TABLE.eid

```