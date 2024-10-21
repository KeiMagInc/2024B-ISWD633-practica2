## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio5.PNG)

### Crear la red
```
docker network create net-wp -d bridge
```
![image](https://github.com/user-attachments/assets/b75bc9ad-37a1-449f-9258-53fb8ddd3fd4)


### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
```
docker run -d --name mysql --network net-wp -e MYSQL_ROOT_PASSWORD=secretpassword -e MYSQL_DATABASE=wordpress_db -e MYSQL_USER=wp_user -e MYSQL_PASSWORD=wp_password mysql:8
```
![image](https://github.com/user-attachments/assets/8f317499-8d96-48a6-b264-705844ed1543)


### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
```
docker run -d --name wordpress --network net-wp -e WORDPRESS_DB_HOST=mysql:3306 -e WORDPRESS_DB_USER=wp_user -e WORDPRESS_DB_PASSWORD=wp_password -e WORDPRESS_DB_NAME=wordpress_db -p 9300:80 wordpress
```
![image](https://github.com/user-attachments/assets/ad14518c-19a1-48d2-a0ff-8bcfaf82974b)
![image](https://github.com/user-attachments/assets/3b5b72b0-f4a2-44fc-be91-e71fd1a8962c)


De acuerdo con el trabajo realizado, en la el esquema de ejercicio el puerto a es 9300, ya que este es el puerto que se está mapeando desde el contenedor de WordPress al host. Es el puerto por el cual puedes acceder a la instalación de WordPress en tu navegador, usando la URL http://localhost:9300.

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
![image](https://github.com/user-attachments/assets/285b752b-f237-4056-8c1d-afaa4a3987b9)
![image](https://github.com/user-attachments/assets/292e4523-e01a-45ce-9dd9-853fcc96df65)
![image](https://github.com/user-attachments/assets/7600454f-c958-4fee-b8af-8eeb41724f92)


Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
![image](https://github.com/user-attachments/assets/efb2fc03-d34a-41b2-b3ce-46b42d427837)
![image](https://github.com/user-attachments/assets/7a8fac0f-d0c4-4810-b91a-c78efb454df3)


### Eliminar el contenedor wordpress
![image](https://github.com/user-attachments/assets/30601fea-36a3-4421-84b3-79e21fadc921)


### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
![image](https://github.com/user-attachments/assets/46b67836-b5d7-4423-a27c-9728efd5f2bd)
![image](https://github.com/user-attachments/assets/4301879a-0f4c-4dfe-94c0-27f4e6829ef4)


### ¿Qué ha sucedido, qué puede observar?
Los datos persisten, es decir, tanto el cambio de tema como la publicación que se creó anteriormente estarán presentes. Esto sucede porque los datos de WordPress están almacenados en la base de datos MySQL en un contenedor separado, y no se pierden al eliminar y recrear el contenedor de WordPress.





