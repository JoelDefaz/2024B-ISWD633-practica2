# Mi Aprendizaje
## Antes de la práctica
Como en la anterior práctica, de mi parte ya conocía ciertos conceptos como lo son las redes en dockers, el acceso a la consola de cada contenedor, etc. Así que esta práctica me ha ayudado a recordar ciertos comandos que se me había olvidado.

## Después de la práctica
Para esta práctica he aprendido nuevos conceptos que me seguro me serán útiles para el momento de realizar las pruebas de cualquier proyecto, ya que he aprendido acerca de cómo ejecutar comandos sin acceder a la consola, así como siempre el desarrollo de la solución de problemas. Así también como lo es declarar variables de entorno en un archivo, ya que simplemente conocida por comando con el  **-e variable=valor**

## Problemas
En cuanto a problemas, el único que tuve fue el de que un puerto de mi maquina local estaba siendo ocupada para el servidor MySQL instalado en mi maquina host, el cual no me permitía realizar el mapeo de puertos.
Esto se solucionó rápidamente simplemente cambiando el puerto del host, en este caso del 3306 al 3307.

## Resultados
1. Crear redes en Docker, así como conectar los contenedores entre si a través de estas redes.
2. Levantar sistemas en diferentes contenedores para poder separar la parte de la lógica con la presentación, como puede ser WordPress y MySQL.
3. Indicar a los contenedores las variables de entorno necesarias a través de archivos o comandos.
4. Identificar redes, así como identificar que contendores se encuentran dentro de estas redes.
5. Creación de servicios y conectar los puertos expuestos de cada contenedor con los otros contenedores, ya sea con ayuda de la documentación de cada imagen en Docker Hub o con los puertos por defecto.