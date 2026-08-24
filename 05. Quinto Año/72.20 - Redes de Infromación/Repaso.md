## Redes

El **protocolo** es el lenguaje utilizado por distintos equipos para poder comunicarse entre sí. IP es un protocolo de direccionamiento lógico que permite comunicarse entre un origen y un destino y enrutar paquetes entre estos.

Las IPs se pueden partir en dos partes. La primera define a que red pertenece y la segunda identifica al host dentro de la misma. Si tenemos `192.168.1.1`, no nos dice nada por sí sola. Para saber la parte que identifica la red, se usan las mascaras, que indica qué bits identifican a la red. Recordemos el CIDR, que indica cuantos bits son de la mascara. Existe tambien la binaria y la decimal.

En una red, hay 2 direcciones reservadas:
- `X.0.0.0`: identifica a la red
- `X.255.255.255`: broadcast

Si esa red esta conectada a un default gateway, es decir un host al que mando todos los paquetes que no pertenecen a mi red local (por ejemplo el router), entonces vamos a necesitar una IP extra. Esto NO es obligatorio, por lo que a la cantidad de direcciones totales, se le resta solamente dos para obtener las asignables. Esta IP NO cuenta. 

---
## Clases de IP

Las **clases de IP** son un sistema de clasificación diseñado en los inicios de Internet para organizar y distribuir las direcciones IP según el tamaño de la red a la que se asignan.
- Clase A: Primer bit en `0` y máscara de 8 bits (`/8`). Entonces:
	- Primera dirección: `0.0.0.0/8`
	- Última dirección: `127.0.0.0/8`
	- Cantidad de direcciones: 
		- Redes: $2^7 \rightarrow 128$  (se resta el primer bit que no se puede modificar)
		- Hosts: $2^{24} \rightarrow 16\text{M}$ 
- Clase B: Primeros bits en `10` y máscara de 16 bits (`/16`). Entonces:
	- Primera dirección: `128.0.0.0/16`
	- Última dirección: `191.255.0.0/16`
	- Cantidad de direcciones: 
		- Redes: $2^{14} \rightarrow 16.384$  (se restan los 2 primeros bits)
		- Hosts: $2^{16} \rightarrow 65.536$
- Clase C: Primeros bits en `110` y máscara de 24 bits (`/24`). Entonces:
	- Primera dirección: `192.0.0.0/24`
	- Última dirección: `223.255.255.0/24`
	- Cantidad de direcciones: 
		- Redes: $2^{21} \rightarrow 2.097.152$  (se restan los 3 primeros bits)
		- Hosts: $2^8 \rightarrow 256$
- Clase D: Primeros bits en `1110` (multicast, sin máscara definida ni división de hosts). Entonces:
	- Primera dirección: `224.0.0.0`
	- Última dirección: `239.255.255.255`
	- Cantidad de direcciones: 
		- Redes/Hosts: No aplica (uso exclusivo para transmisiones Multicast)
- Clase E: Primeros bits en `1111` (Experimental y de investigación). Entonces:
	- Primera dirección: `240.0.0.0`
	- Última dirección: `255.255.255.255`
	- Cantidad de direcciones: 
		- Redes/Hosts: No aplica (reservado para uso futuro/experimental)

---
## Categorías

Existen dos categorías de IPs, públicas y privadas. Las primeras no garantizan que un dispositivo tenga acceso a internet, ya que puede no existir una ruta hacia ella. Las segundas se utilizan para redes internas, y tienen los siguientes rangos:
- `192.168.0.0` a `192.168.255.255`
- `172.16.0.0` a `172.31.255.255`
- `10.0.0.0` a `10.255.255.255`

Dos dispositivos de la misma red no pueden tener una misma dirección IP, y tampoco puede haber dos dispositivos con IP pública conectada a internet.

---
## Subredes

Una **subred** es una subdivisión del bloque de direcciones de una red, y **subnetting** es el proceso de dividir ese bloque en pedazos más pequeños, bien alineados y sin superposición de direcciones. Podríamos dividir una red en estos bloques para tener una mejor organización del espacio de direcciones y para no desperdiciar direcciones, como en el caso de 

Existen dos formas de subidividir una red.
- **FLSM (Fijo)**: se parte el espacio de redes en porciones iguales.
- **VLSM (Variable)**: se parte el espacio en "pedacitos" según la necesidad.