## Protocolo

Es el lenguaje utilizado por distintos equipos para poder comunicarse entre si

## Redes

Las IPs se pueden partir en dos partes. La primera define a que red pertenece y la segunda identifica al host dentro de la misma. Si tenemos `192.168.1.1`, no nos dice nada por si sola. Para saber la parte que identifica la red, se usan las mascaras, que indica qué bits identifican a la red. Recordemos el CIDR, que indica cuantos bits son de la mascara. Existe tambien la binaria y la decimal.

En una red, hay 2 direcciones reservadas:
- `X.0.0.0`: identifica a la red
- `X.255.255.255`: broadcast

Si esa red esta conectada a un default gateway, es decir un host al que mando todos los paquetes que no pertenecen a mi red local (por ejemplo el router), entonces vamos a necesitar una IP extra. Esto NO es obligatorio, por lo que a la cantidad de direcciones totales, se le resta solamente dos para obtener las asignables. Esta IP NO cuenta. 

Las clases de IP son un sistema de clasificación diseñado en los inicios de Internet para organizar y distribuir las direcciones IP según el tamaño de la red a la que se asignan.
- Clase A: Primer bit en `0` y máscara de 8 bits (`/8`). Entonces:
	- Primera dirección: `0.0.0.0/8`
	- Última dirección: `127.0.0.0/8`
	- Cantidad de direcciones: 
		- Redes: 2^7 --> 128 (se resta el primer bit que no se puede modificar)
		- Hosts: 2^24 --> 16M
- Clase B: 

Existen dos categorías de IPs, públicas y privadas. 

Existen dos formas de subidividir una red.
- FLSM (Fijo): se parte el espacio de redes en porciones iguales
- VLSM (Variable): se parte el espacio en "pedacitos" según la necesidad