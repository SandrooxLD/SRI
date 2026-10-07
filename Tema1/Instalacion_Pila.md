# Instalación de la pila Linux

Primero instalamos el Ubuntu completamente


Ahora nos vamos al sistema, actualizamos el firewall

```
$ sudo apt update
```

<img width="714" height="150" alt="image" src="https://github.com/user-attachments/assets/323fca96-1f4f-4b47-87e4-2a2dd7ae1067" />

## Apache:
E instalamos Apache:

```
$ sudo apt install apache2
```

<img width="647" height="82" alt="image" src="https://github.com/user-attachments/assets/4fd75b1b-d005-47ac-b9e8-833ae43973cc" />

Ahora buscamos la ip publica, pero nos dirá que no existe el eth0, así que habrá que ver cual es tu adaptador de red, y para eso hay que usar ifconfig. y para eso hay que instalar el paquete de net-tools 
```
$ sudo apt install net-tools
```

<img width="709" height="144" alt="image" src="https://github.com/user-attachments/assets/36978bbb-90e8-4769-b11f-08b9f904a6d9" />

Vemos que el adaptador es "ens18"
```
$ ifconfig
```

<img width="675" height="353" alt="image" src="https://github.com/user-attachments/assets/3313751d-dc20-4269-ac9c-08da016d4548" />

Y ahora vemos que si funciona y que podemos ver la IP pública
```
$ ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'
```

<img width="735" height="108" alt="image" src="https://github.com/user-attachments/assets/41d25eaa-e4ae-4c4e-9ada-a382713b2e23" />

Ahora nos  metemos al navegador y ponemos "http://10.4.0.99" (la IP) y veremos que funcione

<img width="1117" height="735" alt="image" src="https://github.com/user-attachments/assets/69a07a7f-ffaa-4500-97ed-bc96befdb988" />

## MYSQL:

Ahora instalamos mysql-server, cuando pongamos el comando, nos pedirá confirmación, le daremos a Y
```
$ sudo apt install mysql-server
```

<img width="692" height="165" alt="image" src="https://github.com/user-attachments/assets/a96a3712-3243-4fcc-9c85-3f41ef03fb95" />

Ahora ponemos el comando para hacer la instalación segura, ahora, empezará a hacernos preguntas, y pondremos a todo que sí, menos la segunda pregunta que te pide la validación de complejidad de contraseñas, pondremos 0 que es la más baja
```
$ sudo mysql_secure_installation
```

<img width="1153" height="759" alt="image" src="https://github.com/user-attachments/assets/6af510d4-dd3a-4612-be3b-b33bfeae71e6" />

Aquí hay más preguntas:

<img width="959" height="553" alt="image" src="https://github.com/user-attachments/assets/4ab837b7-1b53-4a9f-8369-9f44e193df1c" />


Ahora para comprobar que funciona:
```
$ sudo mysql
```

<img width="874" height="264" alt="image" src="https://github.com/user-attachments/assets/e3f80982-f7f2-4d96-b5a0-442c9c68ea62" />

Para salir ponemos exit
```
mysql> exit
```

## PHP:

Ahora instalamos PHP, ponemos el siguiente comando para que se empiece a instalar
```
$ sudo apt install php libapache2-mod-php php-mysql
```
<img width="1174" height="330" alt="image" src="https://github.com/user-attachments/assets/1985b57c-4b4a-4ff5-a279-fc9b536053be" />

Ahora comprobamos que se haya instalado bien:
```
$ php -v
```

<img width="772" height="101" alt="image" src="https://github.com/user-attachments/assets/1f511599-a5a5-4f1e-abb4-8ab89adefd88" />

## Creación de Host Virtual

Ahora hacemos un directorio llamado your_domain
```
$ sudo mkdir /var/www/your_domain
```

<img width="744" height="40" alt="image" src="https://github.com/user-attachments/assets/24f30408-d112-4a9a-b53a-acad4d2c0d4b" />

Le ponemos que el owner sea $USER ($USER es el usuario actual)
```
$ sudo chown -R $USER:$USER /var/www/your_domain
```
y lo comprobamos
```
$ ls -l /var/www
```

<img width="882" height="97" alt="image" src="https://github.com/user-attachments/assets/9a963de1-2f04-4f84-9e16-30e66d711180" />

Ahora hacemos un nano
```
$ sudo nano /etc/apache2/sites-available/your_domain.conf
```

<img width="965" height="27" alt="image" src="https://github.com/user-attachments/assets/d14d7a99-3e29-448a-b1c6-7e7e48a9d9ba" />



Y le ponemos la configuración básica:

<img width="1160" height="282" alt="image" src="https://github.com/user-attachments/assets/bb382e25-50c9-4890-bd75-1bcf76ecbe5e" />


Ahora se puede usar el comando a2ensite para habilitar el nuevo host virtual:
```
$ sudo a2ensite your_domain
```
<img width="704" height="84" alt="image" src="https://github.com/user-attachments/assets/0a390634-9b76-4cea-b66e-bced7406d442" />

Ahora lo podemos deshabilitar con a2dissite

```
$ sudo a2dissite 000-default
```
<img width="677" height="40" alt="image" src="https://github.com/user-attachments/assets/9914f890-45fa-480b-8860-d35889c19f28" />

Pero si queremos activar la nueva configuración cuando lo habilites o deshabilites hay que poner lo siguiente:

Primero nos aseguramos de que el archivo de configuración no contenga errores de sintaxis:

```
$ 
sudo apache2ctl configtest
```
Y segundo lo recargamos para que los cambios puedan surtir efecto:

```
$ sudo systemctl reload apache2
```
Ahora que el nuevo sitio web está activo, pero el directorio root web /var/www/your_domain todavía está vacío, por lo que hay que crear un archivo index.html en la ubicación para poder probar que el host virtual funcione:
```
$ nano /var/www/your_domain/index.html
```

<img width="779" height="326" alt="image" src="https://github.com/user-attachments/assets/74b3b1d9-7ad1-4adb-ba40-d03083937dd3" />

Ahora por últimos nos vamos al navegador, y en la pestaña donde antes pusimos la dirección IP ahora recargamos la página y veremos como se ve el index.html:


Ahora cambiamos el orden del index.php e index.html, primero nos metemos y luego lo probamos

<img width="738" height="222" alt="image" src="https://github.com/user-attachments/assets/555618b6-2a89-4879-b14e-4e2a53f35b71" />

Y ahora volveremos a cargar Apache para que los cambios surtan efecto:

<img width="709" height="29" alt="image" src="https://github.com/user-attachments/assets/f81fa985-74b0-46e0-a01c-641f10ea5cc7" />


## Ahora vamos a probar el procesamiento de PHP en su servidor web:

Primero crearemos un archivo nuevo llamado info.php dentro de su carpeta root web personalizada:

<img width="733" height="97" alt="image" src="https://github.com/user-attachments/assets/2dd41354-a18f-4899-8d5e-1c3597082230" />

Ahora nos vamos al navegador para probar la secuencia de comando accediendo a la dirección IP del dominio

<img width="1132" height="315" alt="image" src="https://github.com/user-attachments/assets/0f0b6500-e82c-45b2-ba80-e5737bd1aa3b" />

Ahora hay que borrar el php:

<img width="737" height="42" alt="image" src="https://github.com/user-attachments/assets/ccc59673-0fc7-4819-89a1-ce16d0c42fd3" />


## Ahora vamos a probar la conexión con la base de datos desde PHP

Primero, establecemos una conexión con la consola de MySQL usando la cuenta root:

<img width="728" height="240" alt="image" src="https://github.com/user-attachments/assets/63f09e3e-2cd3-480a-bd00-bb6b86cee82b" />

Ahora creamos la Base de datos:

<img width="423" height="57" alt="image" src="https://github.com/user-attachments/assets/9ed8eaab-7027-490f-a387-383d88985d95" />

Y ahora el creamos un usuario y su contraseña:

<img width="787" height="43" alt="image" src="https://github.com/user-attachments/assets/ab235c33-8c83-4161-ad54-155812ae79bf" />

y procederemos a darle todos los permisos

<img width="428" height="53" alt="image" src="https://github.com/user-attachments/assets/3e4758c3-b4fb-4108-8438-7cf6db84d377" />

A continuación nos vamos de sql:

<img width="433" height="63" alt="image" src="https://github.com/user-attachments/assets/7c51c2f8-6d8e-470b-9712-a2b51c23dc93" />

Ahora nos metemos desde el usuario y le damos a ver todas las base de datos

<img width="731" height="399" alt="image" src="https://github.com/user-attachments/assets/19538cf6-1774-47a8-96c3-74b8127e9c33" />

Ahora hacemos 2 cosas, primero creamos una tabla, le creamos unos campos y ahora le insertamos algunas filas al campo content

<img width="767" height="372" alt="image" src="https://github.com/user-attachments/assets/935dccae-3af7-4506-b3ca-d00df601baa2" />

Ahora vemos si los datos se han guardado correctamente en la tabla y una vez confirmado que hay datos válidos, nos saldremos de la consola de MySQL:

<img width="538" height="247" alt="image" src="https://github.com/user-attachments/assets/e8ed85f1-fd5a-40ac-b38c-8c6218fe09fc" />

Ahora hacemos un nano para crear un archivo php:
```
$ nano /var/www/your_domain/todo_list.php
```

<img width="784" height="348" alt="image" src="https://github.com/user-attachments/assets/297338ff-8f83-4380-ba91-7dab7cfe1aa1" />

Importante, tenemos que poner los datos que hemos puesto anteriormente, yo en mi caso en vez de poner de usuario "example_user" puse "sandro", la contraseña puse "Usuario1_" y la base de datos puse "Redes", así que ahora cuando pongamos el user, la password y la database tenemos que poner esos datos o no nos funcionará, aquí el como lo he hecho: 

<img width="786" height="484" alt="image" src="https://github.com/user-attachments/assets/54a6ed9e-d52b-440a-a623-f0c58adf91ac" />

Y ahora deberemos acceder a esta página en el navegador web al visitar el nombre de dominio o la dirección IP pública de su sitio web seguido de /todo_list.php

En mi caso he puesto:
```
http://localhost/todo_list.php
```
Y una vez nos metemos veremos que todo funciona correctamente

<img width="715" height="330" alt="image" src="https://github.com/user-attachments/assets/3aed9574-03b4-4c8f-bf23-86c91bd51cb9" />







