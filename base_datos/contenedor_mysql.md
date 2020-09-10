# Contenedor en Mysql

Cargar archivos sql al MYsql desde contenedor de docker
```sh
docker exec -i 01d66 mysql -uroot -pudemy [base de datos] < setencias.sql
docker exec -i 01d66 mysql -uroot -pudemy mysql < setencias.sql
```

Cargar la terminar del contenedor para iniciar bash del contenedor
`docker exec -it 01d66 bash`

de ahi ingresar al mysql
```bash
mysql -uroot -pudemy [ingresar con la base de datos]
mysql -uroot -pudemy libreria_cf
```

Con el Tag -e se puede realizar consultas u otro tipos de setencias rápidas en mysql `docker exec -i 01d66 mysql -uroot -pudemy libreria_cf -e "select * from autores"`

## 1. ejemplos
para cargar datos a la base de datos de scripcase

```sh
docker exec -i 4bc93 mysql -uroot -proot sc_negocios  --skip-comments < ~/globalmusic_invent
ory.sql
```