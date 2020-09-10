# Docker

Docker es una alternativa para poder ejecutar programas sin la necesidad 

## 1. contenedores

**detener todos los contenedores que estan activos** `docker stop $(docker ps -q)

**eliminar todos los contenedores** `docker container prune`

## 2. Volumes

Para ver agregar datos a los contenedores

```docker volumes```

opciones

- create, crea volúmenes
- inspect, entrega datos sobre el volumen
- ls, lista
- prune, elimina todos lo volúmenes
- rm,elimina un o más volúmenes

**montar volúmenes**

```
docker container run -dit -v local:/app imagen
docker exec -it <<contenedor>> bash```
docker volume inspect local
sudo ls /var/lib/docker/volumes/local/_data
docker container -it -v local/src <<imagen>>
```

**compartir un volúmenes con varios contenedores**
```
docker container run -it -v local:/src <<imagen>>
```

**unir una carpeta del host al contenedor**
```
docker container run -it -v <<ruta_carpeta>>:/app <<imagen>>
```
**ejemplo agregar mi archivo html al contenedor de nginx**
```
docker container run -d -v /home/gonzalo/src/index.html:/usr/share/nginx/html -p 80:80 nginx
```

## 3. Imagenes

DockerFile usa directivas
- FROM <<imagen:tag>>
- RUN <<ejecutar_comandos>>
- COPY <<ruta_archivo_host>> <<ruta_contenedor>>, copia archivos
- ADD <<archivo_host>> <<ruta_contenedor>>, permite descargar contenido o descomprimir archivos

```
FROM ubuntu

RUN mkdir app
RUN cd /app & touch data.txt
```

**crear una imagen nueva y instancia un contenedor**
```
docker image build -t ubuntu-file .
docker container run -it ubuntu-file
```
**copiar un archivo a la imagen**
```
COPY <<ruta_archivo_host>> <<ruta_carpeta_contenedor>>
```
**Ejemplo**
```
COPY ./src/data /app/src/com/data
-- crea un nueva imagen
docker imagen build -t ubuntu-file:v2 .
docker container run --rm -it ubuntu-file:v2
```

**copiar una carpeta**
```
COPY <<ruta_carpeta_host>> <<ruta_carpeta_contenedor>>
docker imagen build -t ubuntu-file:v3 .
docker container run --rm -it ubuntu-file:v3
```

**permitir agregar contenedor archivos comprimir o bajarlos por internet**
```
ADD <<archivo_host>> <<ruta_contenedor>>
ADD file.tar.gz /com/src
docker imagen build -t ubuntu-file:v4 .
docker container run --rm -it ubuntu-file:v4
```

## 4. Redes

**mostrar las redes disponibles** `docker network ls`
**revisar inspeccionar las redes** `docker inspect (bridge|host|none)`

```
docker container run -dit ubuntu
docker network inspect bridge
-- revisar Containers
docker container inspect <<id_contenedor>>
```

**agregar una red a un contenedor** `docker container run -dit --network bridge ubuntu`

**quitar enlace o desconectar una red a un contenedor** `docker network disconnect bridge <<id_contenedor>>`

**enlazar o conectar una red a un contenedor** `docker network connect bridge <<id_contenedor>>`

**revisar el contenido de una red** `docker network inspect bridge`

```
docker run -dit --network none ubuntu
docker run -dit --network host ubuntu
docker container ls
docker network inspect none

# no tiene internet es un loopback
docker container exec -it <<nombre_contenedor_none>> bash

#no tiene internet -- agregamos a la ip del equipo local
docker container exec -it <<nombre_contenedor_host>> bash
```

## 5. docker machine
`docker-machine version`

**crear contenedor digital ocean**
`docker-machine create -d digitalocean --digitalocena-access-token <<token_id>> <<nombre_contenedor>>`

`docker-machine ls`

**Acceder al docker machine**
`docker-machine env <<maquina_virutal>>` listara todas las variables entorno
`# eval $(docker machine env local) `
`docker-machine ls`
`docker-machine ip local`, da ip del contenedor en maquina virtual
`docker-machine ssh local`, ingresa al contenedor virtual
`docker-machine rm local`, elimina el contenedor de la maquina virtual


## 6. Docker-compose

servicios que pueden tener multiple contenedores archivo YAML llamado **docker-compose.yml**

```
version: "3.7"

services:
    nginx:
        image: nginx
        container_name: nginx # da el nombre contenedor o servicio
        ports:
            - "80:80" # puerto maquina local // puerto contenedor

    mysql:
        image: mysql
        container_name: mysql
        ports
            - "3306:3306"
        environment:
            MYSQL_ROOT_PASSWORD: root
```

`docker-compose up`  inicia los servicios
`docker-compose ls` lista los servicios
`docker-compose up -d`  inicia los servicios en segundo plano
`docker-compose ps`  lista los servicios activos
`docker-compose down`  para y elimina los contenedores del servicio

`docker-compose ps -a`  lista todos los servicios

```shell
docker-compose logs mysql
```
