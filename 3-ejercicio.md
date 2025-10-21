## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO
```
docker network create net-wp
```
### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es (/var/lib)

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
La carpeta no contiene nada. 
### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
```
docker run -d --name practica3 --network net-wp -v "C:\Users\domin\OneDrive - Escuela Politécnica Nacional\SEXTO SEMESTRE\Construccion y evolucion sw\ejercicio3\db":/var/lib/mysql -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=wordpressdb -e MYSQL_USER=dome -e MYSQL_PASSWORD=password mysql:8
```
### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
La carpeta contiene todos los archivos relacionados al contenedor que se creo con la imagen de mysql. 
<img width="655" height="529" alt="image" src="https://github.com/user-attachments/assets/26839d58-da9b-4ad8-bebb-a0b0a98eedc7" />

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es (/var/www/html)

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
```
docker run -d --name servidor-wordpress --network net-wp -p 9500:80 -v "C:\Users\domin\OneDrive - Escuela Politécnica Nacional\SEXTO SEMESTRE\Construccion y evolucion sw\ejercicio3\www":/var/www/html -e WORDPRESS_DB_HOST=practica3 -e WORDPRESS_DB_USER=dome -e WORDPRESS_DB_PASSWORD=password -e WORDPRESS_DB_NAME=wordpressdb
```
### Personalizar la apariencia de wordpress y agregar una entrada
<img width="929" height="479" alt="image" src="https://github.com/user-attachments/assets/9a76bacc-d606-40f1-98ca-99066155aad8" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
```
docker rm -f servidor-wordpress
```
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 
Redirige a la pagina de perfil con el tema y entrada que puse anteriormente. 
