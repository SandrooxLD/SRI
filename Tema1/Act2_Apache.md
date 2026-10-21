
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

Comprueba si se visualiza el pie de página en las páginas generadas por Apache (por ejemplo, en las páginas de error). Cambia el valor de la directiva “ServerSignature” y comprueba que funciona correctamente. 

Primero grep:

<img width="740" height="79" alt="image" src="https://github.com/user-attachments/assets/803a55c4-d5f9-40bd-884d-97be64a79e03" />

Ahora ponemos el serversignature

<img width="874" height="479" alt="image" src="https://github.com/user-attachments/assets/dc9ed18b-e503-418d-bc55-d59a6bc90edb" />

Ahora probamos a ver si funciona metiéndonos a una pagina que no existe para que nos dé error

<img width="620" height="222" alt="image" src="https://github.com/user-attachments/assets/efe58d3f-a295-41ca-891e-fec5c45f2d56" />

### Act 5:

Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas.

Para hacer esto nos vamos a /var/www/html y hacemos 2 directorios, prueba y prueba2, hacemos entonces un index en prueba

<img width="803" height="355" alt="image" src="https://github.com/user-attachments/assets/e0f1b6a1-409d-4c10-bb9b-36a89e6c78b7" />

A continuación deberemos hacer index2.html en prueba e index.html y index2.html en el directorio prueba2, yo hago solo el primer index de cada directorio y luego hago un copy

index2.html de prueba:

<img width="771" height="347" alt="image" src="https://github.com/user-attachments/assets/58e1ddb9-0bd2-42aa-a618-e4e64b3e0ac4" />


Ahora el index.html de prueba 2:

<img width="827" height="357" alt="image" src="https://github.com/user-attachments/assets/a30b0a91-f2e5-4af4-8ac0-349bb2bf7eb4" />


Y ahora la index2.html de prueba2:

<img width="753" height="361" alt="image" src="https://github.com/user-attachments/assets/665ba20c-8c4c-4447-8230-a20769e0801c" />

### Act 6:

Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”

Nos vamos a apache2.conf y añadimos la siguiente línea:

<img width="864" height="468" alt="image" src="https://github.com/user-attachments/assets/95968fe3-4dc0-486a-b715-b8b79e7fc54a" />

Aquí he puesto localhost/prueba/index2.html y me ha mandado a localhost/prueba2/index2.html

<img width="681" height="184" alt="image" src="https://github.com/user-attachments/assets/e5ade46a-09f6-43d2-a82a-e15a31bab27e" />

### Act 7:

Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.

Ahora para hacer esto tenemos que irnos otra vez a apache2.conf y en vez de tener /prueba y /prueba2 , ponemos el index que queremos redireccionar:

<img width="864" height="478" alt="image" src="https://github.com/user-attachments/assets/f3123832-a240-4a6b-a1c5-70dc9c3791d2" />

Lo probamos y vemos que redirecciona la pagina de prueba2: (funciona ya que el index2.html no te redirecciona mientras que la otra si)

<img width="734" height="227" alt="image" src="https://github.com/user-attachments/assets/06956728-dfbc-4b33-83cc-37001b70f98f" />


Recuerda hacer el reload y el restart para que funcione:

```
sudo sytemctl reload apache2
```

```
sudo sytemctl restart apache2
```

### Act 8:

Usa la directiva userdir

Paso 1: Para hacer esto primero activamos el userdir escribiendo "sudo a2enmod userdir":

Ahora tenemos que reiniciar el servicio de apache2:

```
$ service apache2 restart / $ systemctl restart apache2
```

<img width="666" height="116" alt="image" src="https://github.com/user-attachments/assets/8f686bb2-7b71-4d61-87a4-a61c0142add9" />

Paso 2: Ahora creamos el directorio con: mkdir /home/usuario/public_html

<img width="703" height="24" alt="image" src="https://github.com/user-attachments/assets/0237c1d6-d493-4b1c-88e6-878ea1dab3bb" />

Añado que el directorio usuario es el de tu usuario, si se llama diferente, le pones el nombre que es, en mi caso le puse sandro.

Paso 3: Y ahora nos hacemos un index.html en el directorio que acabamos de crear con un nano /home/usuario/public_html/index.html:

<img width="873" height="477" alt="image" src="https://github.com/user-attachments/assets/993b4d14-356a-49a0-9e5c-425f007f5a9d" />

Paso 4: Ahora para ver si está bien hacemos un sudo apachectl configtest

<img width="862" height="74" alt="image" src="https://github.com/user-attachments/assets/ffa8af50-d424-4922-9df8-a1ef9a7f8cc2" />

Paso 5: Procedemos a reinicar el servicio con un service apache2 restart

<img width="691" height="22" alt="image" src="https://github.com/user-attachments/assets/c3d6fc08-0107-4537-b3c7-f408693849b6" />

Paso 6: Ahora tenemos que darle permisos para poder meternos con el comando de chmod 755 /home/usuario

<img width="632" height="20" alt="image" src="https://github.com/user-attachments/assets/b5adbde3-b038-495b-b545-e92ddbf32fb6" />

### Act 9:

Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario.

Vamos a hacer esto por pasos:
1. Paso: Hacemos un "sudo nano /etc/apache2/apache2.conf" para irnos al archivo.conf y le hacemos un grep para ver si tiene alias, voy a hacer un antes y un después (el después es a continuación de los siguientes pasos)

antes:

<img width="953" height="61" alt="image" src="https://github.com/user-attachments/assets/8fb9e73f-d292-4031-87da-53135c4df3e7" />

después:

<img width="860" height="57" alt="image" src="https://github.com/user-attachments/assets/3cb6dc70-3da1-4f5a-8112-5eee7e3f1d1c" />


2. Paso: Añadimos al apache2.conf el Alias, para hacer esto en el conf tendremos que poner el siguiente texto: (Recuerda que pongo usuario pero en mi caso usuario no es el mío, mi nombre de usuario es "sandro", tienes que poner el tuyo o el nombre que tengas en el directorio)

   Alias "/image" "/home/usuario/image"
   <Directory "/home/usuario/image">
		Require all granted
   </Directory>

<img width="1030" height="422" alt="image" src="https://github.com/user-attachments/assets/e1670ca0-a69b-49a3-bcc5-666ac4d59b8d" />
   
3. Paso: Ahora creamos el directorio con un mkdir "mkdir /home/usuario/image", en mi caso "mkdir /home/sandro/image"

<img width="695" height="116" alt="image" src="https://github.com/user-attachments/assets/afaf00e3-8352-4344-b1a2-6b24c37e1955" />

También sirve sin poner el ls con nada:

<img width="981" height="45" alt="image" src="https://github.com/user-attachments/assets/c2fc3e9a-acf3-4ea9-9a8a-c6a7da0b3c65" />

4. Paso: A continuación añadimos ficheros en el directorio de image y los probamos con cat

<img width="906" height="92" alt="image" src="https://github.com/user-attachments/assets/1a92e4a5-f2db-4c6b-a207-411b393d8d16" />

Ojo, es importante hacer un index.html:

<img width="817" height="96" alt="image" src="https://github.com/user-attachments/assets/6d2a4ad5-960f-4a2c-9239-40bfb1dec845" />

5. Paso: Deberemos reiniciar apache ahora:

<img width="747" height="26" alt="image" src="https://github.com/user-attachments/assets/76b83aee-a7b3-429b-821a-8d25e24678c0" />

6. Paso: Y por último debemos comprobar que funciona:

Ahora nos vamos al navegador y lo probamos:

<img width="499" height="188" alt="image" src="https://github.com/user-attachments/assets/8b8f4bb6-37ef-47d9-9b86-d3086db7e499" />

### Act 10:

10. ¿Para qué sirve la directiva Options y dónde aparece. Comprueba si apache indexa los directorios. Si es así, ¿cómo lo desactivamos?
Nota: Para ver la respuesta http podemos usar cURL
https://curl.haxx.se/docs/httpscripting.html
https://www.rosehosting.com/blog/curl-command-examples/
Nota: Si tienes que instalar un módulo en Apache utiliza a2enmod
sudo a2enmod userdir

La directiva options controla que servicios del servidor están disponibles en un directorio en particular

Está en apache2.conf

<img width="878" height="481" alt="image" src="https://github.com/user-attachments/assets/f4cbb5ce-bdf7-44b8-84e2-b1cafa092507" />

Nos metemos al directorio de html y le hacemos un fichero que no sea index.html

<img width="711" height="77" alt="image" src="https://github.com/user-attachments/assets/7282039e-534a-4021-969d-e60c5c1e3339" />

Ahora le cambiamos el nombre a index.html para que no nos salte

<img width="833" height="170" alt="image" src="https://github.com/user-attachments/assets/7cb8943e-8568-4833-95eb-77243af543f9" />

Ahora nos metemos a localhost y veremos que nos indexa

<img width="454" height="372" alt="image" src="https://github.com/user-attachments/assets/44ace0aa-d8ad-4af8-9cf9-29b1f141e9e3" />

Para desactivar el indexado deberemos añadir a Indexes un - y a FollowSymLinks un + en el apache2.conf:

<img width="377" height="123" alt="image" src="https://github.com/user-attachments/assets/023fa16c-f752-4e2a-bf1f-e61035f08f44" />

Hacemos un sudo systemctl restart apache2

Y si ahora lo buscamos nos sale un forbidden:

<img width="463" height="255" alt="image" src="https://github.com/user-attachments/assets/ae95e2e2-c815-4567-b530-881f3d758b75" />

Y si escribimos localhost/Cambio.html veremos que nos manda a la página de Apache2

<img width="1035" height="757" alt="image" src="https://github.com/user-attachments/assets/ca51c4a4-9cbd-4474-83e3-085197cbb2ac" />


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




