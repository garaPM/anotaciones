# Tipos de base datos

los cincos modelos mas populares

## 1. Modelo Relacional
postgresql
Mysql

## 2. Modelo No Relacional (Documentos)

mongodb
roarchdb

## 3. Modelo Llave valor

DynamoDB
Redis

## 4. Modelo Grafo


## 5. Modelo Wide Columnar

Google big tables

# Consultas

```sql
SELECT * FROM USERS
```

```sql
SELECT NAME
FROM USERS
WHERE ROLE = 'MANAGER';
```

[db-fiddle_curso_tarea1](https://www.db-fiddle.com/f/7fnLq7sZNknYPfm6U2xEAH/0)

Solución

```sql
SELECT id , CONCAT(firstName, ' ' , lastName) as NAME 
FROM Student;

SELECT * 
FROM Student;
```

[w3school cursos sql](https://www.w3schools.com/sql/exercise.asp?filename=exercise_where1)

Tablas
Columnas
Filas (Rows)

Primary Key(llave primaria)
Foreign Key(llave Foranea)

![foreign key](_v_images/20200930135138097_1993767444.png =377x)

OLTP

![](_v_images/20200930135911000_1668649019.png =517x)

OLAP

![](_v_images/20200930135956390_1687648120.png =546x)

Tipos de funciones

- Aggregate (agregar) -> opera entre muchos registros(valores) y solo entrega un unico resultado(valor) => como sum.
- Scalar (escalar) -> opera en cada registro(row) entrega multiples valores en cada linea de tabal de valor