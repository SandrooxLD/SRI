# Actividad #3

Previamente se recomienda leer previamente:

https://httpd.apache.org/docs/2.4/howto/access.html

https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#requiredirectives

https://www.the-art-of-web.com/system/apache-authorization/


### Act 1:

Crea un directorio llamado "dir1" y otro llamado "dir2"


	
### Act 2:

Explica qué diferencia existe entre ambos y muestra su equivalencia con la directiva Require:

```
<Directory /var/www/example1>

Order Deny,Allow

Deny from All

Allow from 192.168.1.100

</Directory>

```

```

<Directory /var/www/example1>

Order Allow,Deny

Deny from All

Allow from 192.168.1.100

</Directory>

```

### Act 3:

Para dir1

a) Permite el acceso de las peticiones provenientes de 10.3.0.100

b) Permite el acceso desde "marisma.intranet"

c) Permite el acceso desde cualquier subdominio de "marisma.intranet"

d) Permite el acceso de las peticiones provenientes de "10.3.0.100" con máscara "255.255.0.0"

### Act 4:

Modifica la configuración de forma que el acceso a dir1:

a) Se permita a "marisma.intranet" y no se permita desde 10.3.0.101"

### Act 5:

Modifica la configuración de forma que el acceso a dir2:

a) Se permita a "10.3.0.100/8" y no a "marisma.intranet"

