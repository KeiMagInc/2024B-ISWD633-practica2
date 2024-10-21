# Redes
Las redes son un componente fundamental que permite la comunicación entre contenedores, así como la comunicación de los contenedores con el mundo exterior. 
![Imagen](img/redes.PNG)
- Bridge: Esta es la red por defecto en Docker. Permite la comunicación entre contenedores en el mismo host. Cada contenedor conectado a la red bridge tiene una IP propia en la subred de la red bridge.
    -  Brige por default: Cuando se ejecuta un contenedor, Docker crea automáticamente una red de tipo bridge por default. Esta red se utiliza para permitir la comunicación entre contenedores en el mismo host. Cada contenedor conectado a esta red obtiene su propia dirección IP en la subred de la red bridge.
    - Bridge creada por nosotros: Un usuario también puede crear sus propias redes de tipo bridge en Docker. Esto puede ser útil para organizar y segmentar los contenedores de una aplicación de manera más controlada. Al crear una red bridge personalizada, se puede especificar un rango de direcciones IP y otras configuraciones de red específicas. Los contenedores conectados a esta red utilizarán las direcciones IP de la subred definida por el usuario.
- Host: Con esta red, los contenedores comparten la red del host en lugar de tener su propia interfaz de red. Esto puede mejorar el rendimiento de red, pero los contenedores pueden entrar en conflicto con los puertos del host si intentan utilizar los mismos puertos.
- None: Con esta red, se deshabilita la configuración de red. Los contenedores que usan esta red tienen su propia red de bucle invertido y no pueden comunicarse con otros contenedores a menos que se conecten explícitamente a una red.

### Crear una red de tipo bridge

```
docker network create <nombre red> -d bridge
```

### Crear un contenedor vinculado a una red

```
docker run -d --name <nombre contenedor> --network <nombre red> <nombre imagen>
```

### Para saber a qué red está conectado un contenedor

```
docker inspect <nombre contenedor>
```
ó
```
docker network inspect <nombre red> 
```

### Vincular contenedor a una red
```
docker network connect <nombre red> <nombre contenedor>
```

### Para desvincular un contenedor de una red
```
docker network disconnect <nombre red> <nombre contenedor>
```

### Para listar las redes existentes
```
docker network ls
```

### Crear los contenedores y las redes que se presentan en el esquema. Usar para todos los contenedores la imagen de nginx:alpine

![Imagen](img/esquema-ejercicio-redes.PNG)
![image](https://github.com/user-attachments/assets/df4c051f-3a71-41c4-ae5e-26c33a76b92d)
![image](https://github.com/user-attachments/assets/a99619cb-304e-4deb-9728-5c52e0a02c7d)
![image](https://github.com/user-attachments/assets/1be7763b-a4f9-44ac-9bae-eff37be9c992)
![image](https://github.com/user-attachments/assets/8dffb9f8-2028-4aec-81ca-4396a2e0de88)
![image](https://github.com/user-attachments/assets/17c1ce31-f220-4464-9a7e-b5d2f9d3ae39)
![image](https://github.com/user-attachments/assets/2fda628a-a765-498f-89b5-9a6deb2eecfe)
![image](https://github.com/user-attachments/assets/536b47e2-aa57-45c8-a0b1-fe5888b400ec)
![image](https://github.com/user-attachments/assets/ad5abbe2-89c7-474f-804e-1f773e309ced)


### Para eliminar las redes creadas
```
docker network rm <nombre de la red>
```

