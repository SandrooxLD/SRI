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


