# Variables de Entorno
### ¿Qué son las variables de entorno

Las variables de entorno son pares de nombre-valor que configuran el entorno de ejecución de los procesos en un sistema operativo, proporcionando información y configuraciones necesarias para las aplicaciones y el sistema. Estas variables pueden afectar aspectos como rutas de búsqueda de ejecutables, configuraciones de aplicaciones y datos del sistema y usuario.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.
```
docker run -d --name contenedornginx -e username=user -e role=admin nginx:alpine
```

![image](https://github.com/Milton599/2024A-ISWD633-GR1/assets/94476149/b153f98c-bdbd-428e-840d-0c8712e719f8)


### Crear un contenedor con mysql:8 , mapear todos los puertos
```
docker run -P -d --name contenedorMysql mysql:8
```
### ¿El contenedor se está ejecutando?

No

### Identificar el problema

El mensaje de error indica que el contenedor MySQL requiere que se especifique una contraseña de root o se configure una opción de contraseña específica para la base de datos durante su inicialización. Esto se puede hacer proporcionando una de las siguientes variables de entorno:

MYSQL_ROOT_PASSWORD: Establece la contraseña de root.
MYSQL_ALLOW_EMPTY_PASSWORD: Permite que la contraseña de root esté vacía.
MYSQL_RANDOM_ROOT_PASSWORD: Genera una contraseña de root aleatoria.

### Eliminar el contenedor creado con mysql:8 
```
docker rm contenedorMysql
```
### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo
```
docker run -P -d --name contenedorMysql --env-file=variablesEntorno.txt mysql:8
```
![image](https://github.com/Milton599/2024A-ISWD633-GR1/assets/94476149/a41953f7-284e-4e8e-807a-f9fbc487cb12)



### ¿Qué bases de datos existen en el contenedor creado?
Las siguientes bases de datos:

- information_schema: Esta base de datos contiene metadatos sobre las otras bases de datos en el servidor MySQL.
- mydatabase: Base de datos creada.
- mysql: Esta base de datos contiene las tablas de control de acceso y privilegios del servidor MySQL.
- performance_schema: Esta base de datos contiene información sobre el rendimiento del servidor MySQL.
- sys: Esta base de datos proporciona vistas que muestran información sobre el rendimiento del servidor MySQL.
