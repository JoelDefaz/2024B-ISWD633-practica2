# Variables de Entorno
### ¿Qué son las variables de entorno?
Se trata de pares de clave-valor que se utilizan en sistemas operativos para almacenar información que puede ser utilizada por aplicaciones y procesos en ejecución. 

### Para crear un contenedor con variables de entorno?

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

```
docker run -d --name nginx-container -e username=jdefaz -e role=admin nginx:alpine
```

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
![Imagen](img/practica/env.png)

### Crear un contenedor con mysql:8 , mapear todos los puertos
```
docker run -d --name mysql-container --publish published=3306,target=3306 mysql:8
```

### ¿El contenedor se está ejecutando?
Ell contenedor creado no se esta ejecutando

### Identificar el problema
Tengo dos problemas
1. De inicio el estado del contenedor era simplemente **Created**, pero el error de esta parte es causado que el puerto 3306 de mi computadora host esta siendo utilizada por MySQL local, por lo que este error se soluciona cambiando el puerto del host a 3307
2. El segundo problema, el contenedor tiene un estado **Exited**, y entrando a los **logs** se puede evidenciar que el error esta en que no se han declarado las variables de entorno necesarias, en especifico las siguientes:
    - MYSQL_ROOT_PASSWORD
    - MYSQL_ALLOW_EMPTY_PASSWORD
    - MYSQL_RANDOM_ROOT_PASSWORD

### Eliminar el contenedor creado con mysql:8 
```
docker rm mysql-container
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
docker run -d --name mysql-container --env-file=./env/.env mysql:8
```

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR 

![Imagen](img/practica/envMysql.png)

### ¿Qué bases de datos existen en el contenedor creado?
Las bases de datos que existen actualmente en el contenedor son:
- information_schema 
- mysql              
- performance_schema 
- sys  
