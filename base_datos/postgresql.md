# Comandos Postgresql

## 1. Instalación

[Instalacion Docker postgres](https://medium.com/analytics-vidhya/getting-started-with-postgresql-using-docker-compose-34d6b808c47c)

## 2. Comandos Generales

```pg
\password [usuario]
```

Para listar todas las bases de datos se utiliza
```pg
\l+
```

DCL -> grant, revoke

DDL -> create,alter, drop, rename, truncate, comment

DQL -> SELECT

DML -> Insert, update, delete, merge, call, explain plan, lock TABLE

### 2.1. Select

```sql
SELECT [field]
FROM [table]
WHERE CONDITION = [VALUE]';
```

### 2.2. Funciones aggregate

- AVG()
- COUNT()
- MIN()
- MAX()
- SUM()

```sql
-- Cuenta el número de empleados
SELECT count( emp_no )
FROM employees;
```

```sql
-- El salario maximo es
SELECT MAX( salary )
FROM "public"."salaries";
```

```sql
-- la sumataria del salario pagado es
SELECT MAX( salary )
FROM "public"."salaries";
```

Con tabla employees
```sql
-- El promedio del pago de salarios es
SELECT MAX( salary )
FROM "public"."salaries";
```

```sql
-- la persona más joven dentro de la compañia es
SELECT MAX( birth_date )
FROM "public"."employee";
```

Con tabla France

```sql
-- Cuantas torres hay en francia
SELECT count( id ) 
FROM "public"."towns";
```

Con Tabla WORLD

```sql
-- El número de lenguajes en el mundo
SELECT count(countrycode)
FROM "public"."countrylanguage"
WHERE isofficial = true;
```

```sql
-- El promedio de vida en el mundo es
SELECT avg(lifeexpectancy) 
FROM "public"."country";
```

```sql 
-- buscar el codigo nethelands
SELECT * from "public"."country"
where "code" like 'NLD';

-- La población promedio de netherlands es
SELECT avg( population )  
FROM "public"."city"
WHERE "countrycode" = 'NLD' ;
```

```sql
-- comentario en un línea
/*
 * Comentario multilinea
 *
*/
```

```sql
-- select statement to filter Mayumi Schueller
SELECT first_name, last_name
FROM "public"."employees"
/* filter on first name and last name to limit the amount of data tup_returned
and focus the filtering on a single persona
*/
WHERE first_name = 'Mayumi' AND last_name= 'Schueller'; -- filter here on Mayumi Schueller
```

> Tips
> **"** -> es para las tablas
> **'** -> es para el texto

Filtrar datos con ejercicio

En este filtrara la tabla customers y lo que hara sera contar las mujeres de los estado de oregon(OR) y new work(NY)
```sql
SELECT count(customerid) from "public"."customers"
where gender = 'F' and (state = 'NY' or state = 'OR');
```

filtrar empleados con nombre y apellido
```sql
SELECT first_name, gender, hire_date FROM employees
WHERE (first_name = 'Georgi' and last_name = 'Facello' AND hire_date = '1986-06-26') 
OR (first_name = 'Bezalel' and last_name = 'Simmel');
```

```sql
SELECT first_name, last_name, hire_date FROM employees
WHERE last_name = 'Facello'
OR  last_name = 'Simmel';
```

**NOT**

No selecciona a los clientes que tengan la edad de 55 o 20 años, no los considera
```sql
SElect COUNT(age) FROM "public"."customers"
WHERE NOT age = 55 AND NOT age = 20;
```

No considera a los empleado de genero masculino en el resultado.
```sql
SELECT first_name, gender FROM employees
WHERE NOT gender = 'M';
```


## 3. Section One

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

## 4. Section Two

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

## 5. Section Three

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

## 6. Section Four

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

## 7. Section Five

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

## 8. Section Six

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

## 9. Tipos Datos Comunes 

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
