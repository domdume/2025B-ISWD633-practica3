# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO
```
docker run -d --name nginxBind -P -v C:\Users\domin\Documents\nginx\html:/usr/share/nginx/html nginx:alpine
```
<img width="720" height="85" alt="image" src="https://github.com/user-attachments/assets/f1a704d2-89dd-470b-9c07-862108c4b269" />


### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Aparece un error 403, significa que no se pude acceder a un recurso que no existe, en este caso la carpeta html estaba vacía y no existe un archivo index.html para ver. 
<img width="947" height="487" alt="image" src="https://github.com/user-attachments/assets/a0bf3c51-f134-422d-ae5b-ba8af7f784c8" />

### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El archivo index.html del contenedor es remplazado por el contenido de la carpeta vacía del host. No existe un archivo .html contenido en el contenedor. 
### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Una vez descargado el template, los recursos index.html están disponibles en la carpeta html del host. 
<img width="937" height="527" alt="image" src="https://github.com/user-attachments/assets/85c00de3-c810-4177-ad92-03183eb56953" />

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
```
docker rm -f nginxBind
```
### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
```
docker run -d --name nginxBind2 -P -v C:\Users\domin\Documents\nginx\html:/usr/share/nginx/html nginx:alpine
```
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

La plantilla descargada anteriormente se está mostrando porque los archivos están almacenados en el directorio del host y no en el contenedor. No importa si el contenedor se elimina, la información se almacena en el directorio host y este persiste. 
