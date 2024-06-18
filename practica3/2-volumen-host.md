# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la se obtiene desde la documentación
![Volúmenes](imagenes/volumen-host.PNG)

```
docker run -d --name nginx_container -v /home/user/html:/usr/share/nginx/html nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?

Al ingresar al servidor de nginx, se servirá el contenido que se encuentra en la carpeta html del sistema host.
### ¿Qué pasa con el archivo index.html del contenedor?
El archivo index.html del contenedor original es reemplazado por el index.html de la carpeta del host.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor de nginx, se mostrará el nuevo template HTML que descargamos en la carpeta html del host

### Eliminar el contenedor
```
docker rm -f nginx_container
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
El nuevo contenedor también servirá el contenido del template HTML que descargamos en la carpeta html del host

### ¿Qué hace el comando pwd?
El comando pwd muestra la ruta del directorio actual de trabajo en el sistema de archivos.

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

