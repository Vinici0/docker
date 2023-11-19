Para ejecutar el compose en segundo plano
```
docker compose up -d
```

Esto hace una gran diferencia para ocupoar los volumenes, ya que si se hace con docker container run, se debe crear el volumen primero y luego el contenedor, pero con docker compose, se crea el volumen y el contenedor al mismo tiempo.
```
external: true
```

Para eliminar los contenedores creados con docker compose
```
docker compose down
```