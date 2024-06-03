### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17
```
docker run -d --name contenedorPostgres --network mynetwork -e POSTGRES_PASSWORD=my-secret-pw postgres:11.21-alpine3.17
```

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4
```
docker run -d --name pgadmin --network mynetwork -e PGADMIN_DEFAULT_EMAIL=milton.pastor@epn.edu.ec -e PGADMIN_DEFAULT_PASSWORD=admin -p 8080:80 dpage/pgadmin4
```

La figura presenta el esquema creado en donde los puertos son:
- a: 8080
- b: 80
- c: 5432 

![Imagen](imagenes/esquema-ejercicio3.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
![image](https://github.com/Milton599/2024A-ISWD633-GR1/assets/94476149/86f32f3f-2329-4f33-8fcf-aff29be09488)

![Captura de pantalla 2024-06-02 192218](https://github.com/Milton599/2024A-ISWD633-GR1/assets/94476149/3d320bfb-62e3-4620-b13d-d20a74f3db3b)


### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.

## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
![image](https://github.com/Milton599/2024A-ISWD633-GR1/assets/94476149/a2086d0b-2844-46d0-aaa2-d3d6faa8d6e3)

### Realizar un select *from personas
![image](https://github.com/Milton599/2024A-ISWD633-GR1/assets/94476149/6da6ec34-2b1f-4ff8-a690-352013293a78)
