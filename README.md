Creando un volumen
```

docker volume create postgres-db
```


Creando una imagen y un volumen de postgres
```
docker container run \
-d \
--name postgres-db \
-e POSTGRES_PASSWORD=123456 \
-v postgres-db:/var/lib/postgresql/data \
postgres:15.1
```

Creando una imagen y un volumen de pgAdmin
```
docker container run \
--name pgAdmin \
-e PGADMIN_DEFAULT_PASSWORD=123456 \
-e PGADMIN_DEFAULT_EMAIL=superman@google.com \
-dp 8080:80 \
dpage/pgadmin4:6.17
```

Creando una red
```docker network create postgres-net```

Listando los contenedores existentes
```docker container ls```

Conectado contenedores a la misma red
```
docker network connect postgres-net 061
docker network connect postgres-net 7d1
```

Eliminar contenedores
```
docker container ls
docker container rm -f 061 7d1
```

docker-compose
```
version: '3.8'
services:
  postgres-db:
    container_name: postgres-db
    image: postgres:15.1
    environment:
      POSTGRES_PASSWORD: 123456
    volumes:
      - postgres-db:/var/lib/postgresql/data
    networks:
      - postgres-net
  pgAdmin:
    container_name: pgAdmin
    image: dpage/pgadmin4:6.17
    environment:
      PGADMIN_DEFAULT_EMAIL:

        PGADMIN_DEFAULT_PASSWORD: 123456
    ports:
        - 8080:80
    networks:
        - postgres-net
volumes:
    postgres-db:
networks:
    postgres-net:
        driver: bridge
```
 




