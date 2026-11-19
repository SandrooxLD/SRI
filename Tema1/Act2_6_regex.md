# Actividad 4:

Previamente se recomienda leer:

http://www.rexegg.com/regex-quickstart.html

http://www.regexr.com/

http://iie.fing.edu.uy/~vagonbar/unixbas/expreg.htm

Lleva a cabo los problemas planteados en la web:

http://regexone.com


## Escribe las expresiones regulares para los siguientes supuestos:

Directorios en /www/ cuyo nombre consista en tres dígitos.

```
^/www/(.+/)?[0-9]{3}
```

Ficheros: *.gif, *.jpeg, *.jpg, *.png

```
.+\.(gif|jpe?g|png)$
```

Escribe una directiva para redireccionar todos los GIF a ficheros JPEG en otro servidor

```
RedirectMatch "(.+)\.gif$" "http://other.example.com/$1.jpg
```

Números enteros y decimales

```
(\d+\.)?\d+
```

Números de teléfono en el formato Americano: 123-123-1234

```
\b\d{3}-?\d{3}-?\d{4}\b
```

Palabras

```
[a-zA-Z]+
```

Códigos hexadecimales de color de 24 o 32 bits

```
(#|0x)?(?:[0-9A-F]{2}){3,4}
```

Palabras de 4 letras

```
\b\w{4}\b
```

Número entero sin signo

```
\b\d+\b
```

Número entero con signo

```
[-+]?\d+
```

Números reales

```
[-+]?([0-9]*\.[0-9]+|[0-9]+)
```

Número reales con exponente

```
[-+]?[0-9]*\.?[0-9]+([eE][-+]?[0-9]+)?
```

Email

```
\b[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}\b
```

Números del 0 a 255

```
^([01][0-9][0-9]|2[0-4][0-9]|25[0-5])$
```

