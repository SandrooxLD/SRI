
# Actividad #2.1

## Pon en marcha el servidor Apache y lleva a cabo los siguientes cambios en el archivo de configuración.

Se recomienda leer previamente el siguiente documento:

https://httpd.apache.org/docs/2.4/getting-started.html

La distribución de los archivos de configuración puedes consultarla aquí:

http://wiki.apache.org/httpd/DistrosDefaultLayout#Win32_.28Apache_httpd_2.2.29

Si tienes problemas con Apache consulta el siguiente enlace:

https://docs.bluehosting.cl/troubleshooting/servidores/guia-de-solucion-de-problemas-comunes-de-apache.html


### Act 1:

Apache utilizará el puerto 81 además del 80

Primero hacemos cd a /etc/apache2/, luego nos vamos a ports.conf y escribimos Listen 81

<img width="675" height="406" alt="image" src="https://github.com/user-attachments/assets/027c142e-8165-4cf8-bf1a-1f122c0c0f5e" />



### Act 2:

Añadir el dominio “marisma.intranet” en el fichero “hosts”

Ahora nos salimos de /apache2, nos vamos a etc y nos metemos a "hosts", añadimos marisma.intranet a la dirección 127.0.0.1 y le hacemos un ping para confirmar que responde

<img width="665" height="341" alt="image" src="https://github.com/user-attachments/assets/67d791c2-9a17-4aac-85ee-54dc9e467d67" />


	
### Act 3:

Cambia la directiva “ServerTokens” para mostrar el nombre del producto.

Para hacer esto nos vamos a /apache2/apache2.conf, nos vamos al final del fichero de configuración y añadimos la siguiente línea:

<img width="727" height="484" alt="image" src="https://github.com/user-attachments/assets/3a3fd07c-f285-4724-84dc-07d2f64f13e8" />


### Act 4:

4. Comprueba si se visualiza el pie de página en las páginas generadas por Apache (por ejemplo, en las páginas de error). Cambia el valor de la directiva “ServerSignature” y comprueba que funciona correctamente. 




### Act 5:

Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas.

Para hacer esto nos vamos a /var/www/html y hacemos 2 directorios, prueba y prueba2, hacemos entonces un index en prueba

<img width="727" height="520" alt="image" src="https://github.com/user-attachments/assets/fb067beb-161c-440b-b688-33513d59a4d0" />

A continuación deberemos hacer pag2.html en prueba e index.html y prueba2 en el directorio prueba2:

Pag 2 de prueba:

<img width="731" height="217" alt="image" src="https://github.com/user-attachments/assets/043097b8-4f6b-4f9d-9d66-3493083fa91b" />

Ahora el index de prueba 2:

<img width="728" height="376" alt="image" src="https://github.com/user-attachments/assets/56273683-209e-4dfa-ae05-9d7cc316a348" />

Y ahora la pag2 de prueba2:

<img width="730" height="202" alt="image" src="https://github.com/user-attachments/assets/9b97629b-fe7a-47a2-a516-e357649b8d6a" />


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




