# Actividad 5

Reescritura
Lee la documentación sobre  mapeo de contenidos en Apache:
http://httpd.apache.org/docs/current/urlmapping.html
http://httpd.apache.org/docs/current/mod/mod_rewrite.html

Algunos ejemplos de redirecciones útiles
https://www.elarraydejota.com/ejemplos-de-redirecciones-utiles-y-comunes-con-mod_rewrite-para-apache/

## Lleva a cabo los ejercicios propuestos en el siguiente enlace
http://www.josedomingo.org/pledin/2011/10/ejemplos-del-modulo-rewrite-en-apache-2-2/

### Ejemplo 1: Reescribir URL

### Ejemplo 2: Cambiar la extensión de los ficheros


### Ejemplo 3: Crear URL amigables

### Ejemplo 4: Acortar URL

### Ejemplo 5: Uso del RewriteCond

### Ejemplo 6: URL amigables con WordPress



Nota: Si no utilizas ficheros .htaccess, incluye las directivas de reescritura dentro de la directiva “directory” correspondiente, tal como se muestra a continuación:
<Directory /var/www/html>
    	Options FollowSymLinks
    	RewriteEngine On
    	RewriteBase /
    	RewriteRule ^([a-z]+)/([0-9]+)/([0-9]+)$ operacion.php?op=$1&op1=$2&op>
</Directory>

El fichero: operacion.php

<?php
if (isset($_GET['op']) && isset($_GET['op1']) && isset($_GET['op2'])) {
   $op = $_GET["op"];
   $op1 = $_GET["op1"];
   $op2 = $_GET["op2"];
   $r = 0;
 
   if ($op == "suma")
   $r = $op1 + $op2;
   else if ($op == "resta")
   $r = $op1 - $op2;
   else if ($op == "multiplica")
   $r = $op1 * $op2;
   else if ($op == "divide")
   $r = $op1 / $op2;
 
   echo "op = " . $op . "<br>";
   echo "op1 = " . $op1 . " ";
   echo "op2 = " . $op2 . " ";
   echo "Resultado  = " . $r;
}
?>

