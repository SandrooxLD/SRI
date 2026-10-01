

Primero instalamos el Ubuntu

...

Ahora nos vamos al sistema, actualizamos el firewall
<img width="714" height="150" alt="image" src="https://github.com/user-attachments/assets/323fca96-1f4f-4b47-87e4-2a2dd7ae1067" />
E instalamos Apache:

<img width="647" height="82" alt="image" src="https://github.com/user-attachments/assets/4fd75b1b-d005-47ac-b9e8-833ae43973cc" />

Ahora buscamos la ip publica, pero nos dirá que no existe el eth0, así que habrá que ver cual es tu adaptador de red, y para eso hay que usar ifconfig. y para eso hay que instalar el paquete de net-tools 

<img width="709" height="144" alt="image" src="https://github.com/user-attachments/assets/36978bbb-90e8-4769-b11f-08b9f904a6d9" />

Vemos que el adaptador es "ens18"

<img width="675" height="353" alt="image" src="https://github.com/user-attachments/assets/3313751d-dc20-4269-ac9c-08da016d4548" />

Y ahora vemos que si funciona y que podemos ver la IP pública
<img width="735" height="108" alt="image" src="https://github.com/user-attachments/assets/41d25eaa-e4ae-4c4e-9ada-a382713b2e23" />

Ahora nos  metemos al navegador y ponemos 2http://10.4.0.992 (la IP) y veremos que funcione

<img width="1117" height="735" alt="image" src="https://github.com/user-attachments/assets/69a07a7f-ffaa-4500-97ed-bc96befdb988" />





