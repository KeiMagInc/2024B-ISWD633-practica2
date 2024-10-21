### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17
```
docker run -d --name mi_postgres --env POSTGRES_PASSWORD=mi_password postgres:11.21-alpine3.17
```
![image](https://github.com/user-attachments/assets/fd710525-fc95-4189-905b-b44efb7bf09b)

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4
```
docker run -d --name pgadmin -p 8080:80 -e 'PGADMIN_DEFAULT_EMAIL=admin@example.com' -e 'PGADMIN_DEFAULxT_PASSWORD=admin_password' dpage/pgadmin4
```
![image](https://github.com/user-attachments/assets/9fd75669-5b71-4309-aedd-b8762c6958fc)

La figura presenta el esquema creado en donde los puertos son:
- a: 80
- b: 80
- c: 5432

![Imagen](img/esquema-ejercicio3.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
![image](https://github.com/user-attachments/assets/e40fb65d-4781-454b-bee5-87c84ca70ced)

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.

## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
# COMPLETAR
### Realizar un select *from personas
# AGREGAR UNA CAPTURA DE PANTALLA DEL RESULTADO
