# Actividad #3

Previamente se recomienda leer previamente:

https://httpd.apache.org/docs/2.4/howto/access.html

https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#requiredirectives

https://www.the-art-of-web.com/system/apache-authorization/


### Act 1:

Crea un directorio llamado "dir1" y otro llamado "dir2"

Primero nos vamos a la carpeta con un cd y luego hacemos mkdir para hacer los directorios

Para hacer esto ponemos lo siguiente en linux:

```
cd /var/www/html/

mkdir dir1

mkdir dir2

```

Si estamos en la carpeta nos pedirá permisos así que le añadimos el sudo

<img width="580" height="95" alt="image" src="https://github.com/user-attachments/assets/911e8913-bd0a-41d3-bde6-f528d08da73a" />


### Act 2:

Explica qué diferencia existe entre ambos y muestra su equivalencia con la directiva Require:

```
<Directory /var/www/example1>

Order Deny,Allow

Deny from All

Allow from 192.168.1.100

</Directory>

```

En este ejemplo se niega el acceso a todos excepto a 192.168.1.100

```

<Directory /var/www/example1>

Order Allow,Deny

Deny from All

Allow from 192.168.1.100

</Directory>

```

En este ejemplo se niega el acceso a todos

La explicación es que en el order la primera opción es el primer filtro, y el segundo lo sobrescribe, así que en la segunda opción el allow queda anulado por el deny from all

### Act 3:

Para dir1

a) Permite el acceso de las peticiones provenientes de 10.3.0.100

Para hacer esto nos vamos al archivo de configuración de apache y ponemos lo siguiente:

<img width="726" height="362" alt="image" src="https://github.com/user-attachments/assets/6691d415-1f36-4598-b1e8-9c81fc6744fa" />

Ahora todo lo demás lo vamos añadiendo al apartado de Directory

b) Permite el acceso desde "marisma.intranet"

Añadimos Require host marisma.intranet

<img width="332" height="79" alt="image" src="https://github.com/user-attachments/assets/fdad3c52-8372-4a32-9d07-b2aaa4c845f8" />

c) Permite el acceso desde cualquier subdominio de "marisma.intranet"

Ahora en el marisma.intranet le añadimos un punto antes de marisma

<img width="329" height="90" alt="image" src="https://github.com/user-attachments/assets/032091b8-aa08-4909-a78b-d008dd4d1bbc" />

d) Permite el acceso de las peticiones provenientes de "10.3.0.100" con máscara "255.255.0.0"
Allow from 10.3.0.100/255.255.0.0  
// equivalente a 
Require ip 10.3.0.100/255.255.0.0

### Act 4:

Modifica la configuración de forma que el acceso a dir1:

a) Se permita a "marisma.intranet" y no se permita desde 10.3.0.101"
<Directory /var/www/html/dir1>
	Allow from marisma.intranet
	Deny from 10.3.0.101
</Directory>

// esto es equivalente a esto otro

<Directory /var/www/html/dir1>
	<RequireAll>
	Require host marisma.intranet
		Require not ip 10.3.0.101
	</RequireAll>
</Directory>

### Act 5:

Modifica la configuración de forma que el acceso a dir2:

a) Se permita a "10.3.0.100/8" y no a "marisma.intranet"

	Allow from 10.3.0.101/8  equivalente a Require ip 10.3.0.101/8
	Deny from marisma.intranet  equivalente a Require not host marisma.intranet

<Directory /var/www/html/dir2>
	Allow from 10.3.0.101/8
	Deny from marisma.intranet
</Directory>

// esto es equivalente a esto otro

<Directory /var/www/html/dir2>
	<RequireAll>
	Require ip 10.3.0.101/8
		Require not host marisma.intranet
	</RequireAll>
</Directory>

