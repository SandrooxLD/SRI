
# Actividad #2.1

## Pon en marcha el servidor Apache y lleva a cabo los siguientes cambios en el archivo de configuración.

Se recomienda leer previamente el siguiente documento:

https://httpd.apache.org/docs/2.4/getting-started.html

La distribución de los archivos de configuración puedes consultarla aquí:

http://wiki.apache.org/httpd/DistrosDefaultLayout#Win32_.28Apache_httpd_2.2.29

Si tienes problemas con Apache consulta el siguiente enlace:

https://docs.bluehosting.cl/troubleshooting/servidores/guia-de-solucion-de-problemas-comunes-de-apache.html
<br> 

### Act 1:

1. Apache utilizará el puerto 81 además del 80

### Act 2:

2. Añadir el dominio “marisma.intranet” en el fichero “hosts”
	
### Act 3:

3. Cambia la directiva “ServerTokens” para mostrar el nombre del producto.

### Act 4:

4. Comprueba si se visualiza el pie de página en las páginas generadas por Apache (por ejemplo, en las páginas de error). Cambia el valor de la directiva “ServerSignature” y comprueba que funciona correctamente. 

### Act 5:

5. Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas.

### Act 6:

6. Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”

### Act 7:

7. Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.

### Act 8:

8. Usa la directiva userdir

### Act 9:

9. Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario.

### Act 10:

10. ¿Para qué sirve la directiva Options y dónde aparece. Comprueba si apache indexa los directorios. Si es así, ¿cómo lo desactivamos?
Nota: Para ver la respuesta http podemos usar cURL
https://curl.haxx.se/docs/httpscripting.html
https://www.rosehosting.com/blog/curl-command-examples/
Nota: Si tienes que instalar un módulo en Apache utiliza a2enmod
sudo a2enmod userdir



## Actividad #2.2


Los scripts deben comprobar previamente el número de parámetros y en el caso de no pasar los parámetros necesarios nos mostrará un error indicando la sintaxis correcta.

Se aconseja leer previamente alguno de los siguientes enlaces sobre shell script
https://github.com/denysdovhan/bash-handbook
https://www.shellscript.sh/
http://www.freeos.com/guides/lsst/index.html
Dos comandos que te pueden ser de utilidad son:
grep
https://geekland.eu/uso-del-comando-grep-en-linux-y-unix-con-ejemplos/
sed
https://geekland.eu/uso-del-comando-sed-en-linux-y-unix-con-ejemplos/


Trabajando con scripts  (Debes publicarlos en Github)
Crea un script para cada uno de los siguientes problemas
Crea un script que añada un puerto de escucha en el fichero de configuración de Apache. El puerto se recibirá como parámetro en la llamada y se comprobará que no esté ya presente en el fichero de configuración.
Crea un script que añada un nombre de dominio y una ip al fichero hosts. Debemos comprobar que no existe dicho dominio en el fichero hosts
Crea un script que nos permita crear una página web con un título, una cabecera y un mensaje




