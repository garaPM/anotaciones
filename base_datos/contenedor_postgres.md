# contenedor_postgres

```sh
docker-compose run dbinpg bash

docker-compose run dbinpg psql --host=dbinpg -U gonzalo_cursos --dbname Employees --port 543
2
docker-compose run dbinpg psql --host=dbinpg -U gonzalo_cursos --dbname Employees --port 543
2 
```

Restaurar base de datos del curso de Zero To Master en contenedor de postgresSql
```sh
docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d Employees < employees.sql
docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d Employees < load_departments.
sql
docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d Employees < load_employees.sq
l
docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d Employees < load_dept_manager
.sql
docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d Employees < load_titles.sql
docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d Employees < load_salaries.sql
docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d Employees < load_dept_emp.sql
```


```sh
docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d France < france.sql

docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d World < world.sql

docker exec -i sql_postgres_dbinpg_1 psql -U gonzalo_cursos -d Store < store.sql
```