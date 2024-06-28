## VOLUMEN ANÓNIMO
Un volumen anónimo es un volumen que Docker crea automáticamente sin nombre específico cuando ejecutas un contenedor. Son útiles cuando deseas almacenar datos temporalmente sin preocuparte por el nombre del volumen. Docker asigna un identificador único en lugar de un nombre. Se utilizan principalmente para almacenamiento temporal. 
**Considerar**
Los datos persisten mientras el contenedor exista, pero son más difíciles de gestionar y referenciar después.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta contenedor> <nombre imagen>
```

### Para eliminar el contenedor y el volumen
```
docker rm -fv server-nginx
```
_esta instrucción elimina el volumen si éste es de tipo anónimo_

# Eliminar todos los volúmenes anónimos (dangling volumes) no utilizados
Los dangling volumes son volúmenes en Docker que no están asociados a ningún contenedor en ejecución. Estos volúmenes se crean cuando se monta un volumen en un contenedor y luego se elimina ese contenedor sin eliminar explícitamente el volumen.
```
docker volume prune
```

![image](https://github.com/Milton599/2024A-ISWD633-GR1/assets/94476149/aba9b1da-94fd-49b3-bf07-402f06230f5d)
