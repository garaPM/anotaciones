# Comandos Postgresql

## 1. Section One

```
CREATE DATABASE database_name;

CREATE TABLE table_name(
column_name datatype CONSTRAINT
);
```

```
INSERT INTO table_name(
column_name
)VALUES(
‘value’
);
```

```
SELECT * FROM table_name;

SELECT column_name
FROM table_name;
```

## 2. Section Two

```
SELECT DISTINCT column_name
FROM table_name;
```

```
SELECT column_name
WHERE <condition>;
```

```
SELECT DISTINCT column_name
WHERE <condition>;
```

```
UPDATE table_name
SET column_name = ‘new_value’
WHERE <condition>;
```

```
DELETE FROM table_name
WHERE <condition>;
```

## 3. Section Three

```
SELECT COUNT(column_name)
FROM table_name;
```

```
SELECT COUNT(*)
FROM table_name;
```

```
SELECT COUNT(DISTINCT column_name)
FROM table_name;
```

```
SELECT column_name
FROM table_name
ORDER BY column_name;
```

```
SELECT column_name
FROM table_name
ORDER BY column_name DESC;
```

```
SELECT column_name
FROM table_name
ORDER BY column_name ASC;
```

## 4. Section Four

```
SELECT column_name
FROM table_name
WHERE column_name
BETWEEN value1 AND value2;
```

```
SELECT column_name
FROM table_name
WHERE column_name
NOT BETWEEN value1 AND value2;
```

```
SELECT column_name
FROM table_name
WHERE column_name
LIKE ‘_abc%’;
```

```
SELECT column_name
FROM table_name
WHERE column_name
IN (‘abc’, ‘xyz’);
```

## 5. Section Five

```
SELECT MIN(column_name)
FROM table_name;
```

```
SELECT MAX(column_name)
FROM table_name;
```

```
SELECT ROUND(MIN(column_name))
FROM table_name;
```

```
SELECT ROUND(MAX(column_name))
FROM table_name;
```

```
SELECT AVG(column_name)
FROM table_name;
```

```
SELECT SUM(column_name)
FROM table_name;
```

```
SELECT ROUND(AVG(column_name))
FROM table_name;
```

```
SELECT ROUND(SUM(column_name))
FROM table_name;
```

## 6. Section Six

```
SELECT AGGREGATE_FUNCTIOM(column_name)
FROM table_name
GROUP BY column_name;
```

```
SELECT AGGREGATE_FUNCTIOM(column_name)
FROM table_name
GROUP BY column_name
HAVING <condition>;
```

```
SELECT column_name AS alias_name
FROM table_name AS alias_name;
```

```
SELECT column_name alias_name
FROM table_name alias_name;
```

```
SELECT column_name
FROM table_name
LIMIT max_value;
```

```
SELECT column_name
FROM table_name
LIMIT max_value
OFFSET value;
```

```
SELECT
	a.column_name, b.column_name
FROM
	table_a
INNER JOIN
	table_b ON table_a.column_name = table_b.column_name;
```


```
SELECT
	a.column_name, b.column_name
FROM
	table_a
LEFT JOIN
	table_b ON table_a.column_name = table_b.column_name;
```

```
SELECT
	b.column_name, a.column_name
FROM
	table_b
RIGHT JOIN
	table_a ON table_b.column_name = table_ba.column_name;
```

```
SELECT
	b.column_name, a.column_name
FROM
	table_b
FULL OUTER JOIN
	table_a ON table_b.column_name = table_ba.column_name;
```

## 7. Tipos Datos Comunes 

Los tipos de datos comunes en postgresql

    • Numeric
        ◦ integer
        ◦ decimal
        ◦ Serial
    • Character
        ◦ character(n) - char(n)
        ◦ character varying(n) - varchar(n)
        ◦ Text
    • Boolean
        ◦ Boolean - bool

Common PostgreSQL Constraints

    • PRIMARY KEY
    • UNIQUE
    • FOREIGN KEY - REFERENCES
    • NOT NULL
    • CHECK(condition)




```
ALTER TABLE
table_name
ADD COLUMN
column_name datatype CONSTRAINT;
```

```
ALTER TABLE
table_name
RENAME COLUMN old_name TO new_name;
```

```
ALTER TABLE table_name
DROP COLUMN column_name;
```

```
ALTER TABLE table_name
ALTER COLUMN column_name
SET DATATYPE datatype;
```

````
ALTER TABLE table_name
RENAME TO new_table_name;
```
