## Capa Física

La **capa física** es el soporte físico para entablar comunicaciones. El **medio de coaxil** tiene un core de cobre con un material aislante y otro conductor de malla trenzada que cubre ese material. Esto es contenido por una capa protectora de plástico. Tiene una característica importante que es la inmunidad al ruido.

El **Unshielded Twisted Pair (UTP)** consiste en dos hilos de un material de cobre que funcionan de manera diferencial. Es muy poco inmune al ruido, ya que no tiene la malla que veíamos antes. Para mejorar la supervivencia se lo trenza.

La **fibra óptica** consiste en un filamento de vidrio del grosor de un cabello o de un polímero con características similares al vidrio de la frecuencia a la que transmite.







---
## Wide Area Network (WAN)

Una **WAN (Wide Area Network)** es una red de telecomunicaciones diseñada para interconectar múltiples redes locales (LAN) dispersas en distintas ciudades, países o continentes. Puede ser pública (Internet) o privada. Esta última se puede clasificar en:
- **Dedicada:** Consiste en otorgar un porción de la red para uso exclusivo de un cliente. Tiene muy poco overhead pero es más caro.
- **Switched**: La infraestructura del proveedor es compartida con otros clientes que tenga de manera segura.
	- **Circuit-Switched**: Establece dinámicamente una conexión dedicada para voz o datos entre un emisor y un receptor. Se establece la conexión previamente a comenzar cualquier comunicación. 
	- **Packet-Switched**: Es un circuito virtual punto a punto establecido utilizando la red de un proveedor, que permite a múltiples clientes compartir sus recursos. 

Existen dos tipos de redes:
- **Redes Broadcast** (Generalmente LAN): Como por ejemplo el Wi-Fi, donde todos nos conectamos.
- **Redes Punto a Punto** (Generalmente WAN): Las puntas normalmente son routers o switches, no computadoras como en la figura.

**Frame Relay** es una tecnología de conmutación de paquetes para redes WAN que opera en las capas física y de enlace de datos. Este protocolo prescinde de mecanismos pesados de corrección de errores en el nivel físico y delega esa tarea en las capas superiores, logrando una transmisión considerablemente más ágil y eficiente. Permite multiplexar múltiples circuitos virtuales sobre un único enlace, por lo que cada router requiere solo una interfaz física para conectarse a múltiples destinos remotos simultáneamente.
![[Pasted image 20260825190625.png|center|390]]

El **Protocolo PPP (Point-to-Point Protocol)** es un estándar de enlace multiprotocolo capaz de transportar tráfico de capa de red variado como IP, IPX o AppleTalk. Se encuentra dentro de los protocolos punto a punto en WAN. Destaca por ofrecer mecanismos robustos de autenticación (mediante PAP y CHAP), a diferencia de Frame Relay, y la capacidad de asignar direcciones IP de forma dinámica al extremo remoto durante el establecimiento de la sesión.

**Metro Ethernet (MAN)** es una tecnología de telecomunicaciones diseñada para redes de área metropolitana (MAN) que opera en la capa 2. Su funcionamiento se basa en crear una conexión EVC (Ethernet Virtual Connection), lo que permite extender el estándar Ethernet más allá de la red local tradicional sin necesidad de convertir o encapsular tramas en protocolos seriales complejos.

Para conectar usuarios residenciales a las redes WAN/Internet, las dos tecnologías de acceso más extendidas históricamente son:
- **ADSL (Asymmetric Digital Subscriber Line):** Utiliza el par de cobre telefónico tradicional y suele apoyarse en PPPoE (PPP over Ethernet).
- **Cablemodem:** Opera sobre la red física de televisión por cable (coaxial o híbrida HFC). Se rige bajo el protocolo DOCSIS (Data Over Cable Service Interface Specification).

---
## Calidad de Servicio

Cuidado. Mientras que QoS gestiona prioridades y colas ante cuellos de botella, la aceleración WAN busca optimizar el uso del ancho de banda (BW) entre sitios mediante dispositivos o aplicaciones que se ejecutan en ambos extremos (origen y destino).

La **buferización (buffering)** es una técnica que se aplica directamente en el extremo receptor para almacenar temporalmente los paquetes antes de procesarlos o reproducirlos. Reduce la variación en los tiempos de llegada de los paquetes (jitter), logrando una reproducción continua y estable en servicios multimedia.

Las **normas de encolamiento** entran en juego en las interfaces del router, donde cada puerto dispone de una cola de memoria para retener temporalmente los paquetes que esperan ser transmitidos.
- **Cola FIFO**: Se retienen los paquetes y los despacha estrictamente en el mismo orden cronológico en el que ingresaron.
- **Cola de Prioridad**: Clasifica el tráfico separándolo en cuatro colas jerárquicas. La interfaz sólo transmite paquetes de un nivel inferior cuando la cola de mayor prioridad se encuentra completamente vacía. Hay riesgo de inanición (starvation).
- **Cola Personalizada**: Aplica Round-Robin para alternar de forma cíclica entre distintas colas. El administrador puede definir qué tipo de tráfico se asocia a cada y otras reglas.
- **Weighted Fair Queueing (WFQ)**: Crea dinámicamente una cola separada para cada flujo de tráfico individual. El algoritmo busca la equidad al balancear flujos de poco caudal frente a transferencias masivas.

La **clasificación de tráfico** permite identificar y categorizar los paquetes según criterios como listas de control de acceso (ACL por IP y puerto), el puerto físico del switch o el tipo de aplicación. 

En la configuración de un **Firewall/Router**, las reglas de filtrado permiten controlar el flujo de tráfico entre diferentes zonas de la red definiendo una acción específica (Allow, Deny o Discard).

**MPLS (Multiprotocol Label Switching)** es una tecnología de conmutación de alto rendimiento que asigna una etiqueta a los datagramas para acelerar su reenvío en los routers del núcleo de la red. Al recibir un paquete, los equipos intermedios únicamente leen la etiqueta y no la dirección IP de destino, definiendo una ruta o circuito virtual preestablecido a lo largo de toda la infraestructura. Esta tecnología se ubica entre las capas 2 y 3. Para establecer los caminos de conmutación, los routers intercambian información de etiquetas de forma coordinada.

---
## Internet

Existen 3 tipos de ISPs en Internet, y a medida que vamos subiendo de tier, encontramos un requerimiento de una mayor capacidad de procesamiento.
- **Tier-1**: Backbone global con cables submarinos; operan sin default gateway (DFZ).
- **Tier-2**: Proveedores regionales que compran tránsito a Tier-1, hacen peering en IXPs y revenden conectividad hacia abajo.
- **Tier-3**: ISPs de última milla (como Telecom o Claro) que pagan tránsito a niveles superiores y dan servicio al usuario final.
- **Usuario final**: Clientes residenciales o corporativos que contratan acceso a Internet (habitualmente a un Tier-3) para enviar y recibir tráfico.

El **peering** es un acuerdo de interconexión directa y voluntaria entre dos redes o proveedores de Internet para intercambiar tráfico de manera recíproca, típicamente libre de costos (settlement-free), permitiendo que los clientes de una red alcancen a los de la otra sin pagarle tránsito a un proveedor superior.
- **Peering Privado**: dos operadores establecen un enlace físico punto a punto exclusivo y dedicado entre sus infraestructuras.
- **Peering Público**: se implementa a través de un IXP, donde múltiples ISPs y proveedores de contenido se conectan a un switch central compartido para intercambiar tráfico entre sí mediante un único enlace físico.

Los **IXP (Internet Exchange Points)** son centros neurálgicos de interconexión que adoptan una topología en estrella con un switch central compartido donde diversas entidades se conectan mediante un único puerto físico. La incorporación de un IXP no elimina el peering privado ni las conexiones de tránsito tradicionales. El IXP es un sistema autónomo y no da acceso a Internet, sino que brinda conectividad con el resto de los proveedores locales.

**CABASE (Cámara Argentina de Internet)** es la entidad pionera en Argentina que nuclea a ISPs, empresas de telecomunicaciones y proveedores de contenido, responsable de crear y operar la red federal de IXPs del país.

Un **PAT (Punto de Agregación de Tráfico)** es un punto de presencia intermedio provisto por un miembro de la red para extender el alcance físico del IXP Regional. Su objetivo es facilitar el acceso remoto de varios miembros distantes hacia el punto de intercambio central sin que cada uno deba tender un enlace directo y costoso hasta la sede principal de CABASE.

Los **Looking Glass Servers** son herramientas de diagnóstico públicas provistas por ISPs e IXPs con acceso de solo lectura, diseñadas para consultar el estado de la red y las tablas de enrutamiento desde la perspectiva externa de un router específico.

**Anycast** es una técnica de direccionamiento y enrutamiento en la que una misma dirección IP pública se asigna a múltiples servidores o nodos distribuidos geográficamente (relación 1-a-muchos). A diferencia de Unicast (donde una IP identifica a una única interfaz específica de forma 1-a-1), en Anycast los paquetes enviados a dicha IP son encaminados por los routers hacia el nodo de destino topológicamente más cercano según las métricas y la convergencia de BGP (menor longitud de AS-Path o menor costo).

En la práctica, Anycast "engaña" a la capa de red, ya que mientras que en la realidad física existen múltiples servidores independientes en distintas ubicaciones configurados con la misma IP, los routers del plano de control asumen que se trata de un único servidor físico alcanzable a través de dos caminos redundantes.

---
## ISPs

La arquitectura de un ISP se organiza en capas jerárquicas:
- **Access Network**: red de acceso que llega hasta la casa del usuario.
- **Aggregation Network**: también llamada red de distribución. Red de múltiples capas que va consolidando el tráfico de diferentes partes de la red de acceso.
- **Edge Network**: red de borde. Se usa tanto como borde de la red de interior (hacia los usuarios) como de la red exterior (hacia internet).
	- Red que termina el tráfico de los usuarios donde son autenticados y se controla el ancho de banda (esto también puede hacerse en la red de acceso)
	- Red donde se interconecta con otras redes (ISPs/IXP )
- **Core Network**: red de núcleo es la red que interconecta a todo el ISP internamente. En particular conecta los Edge entre sí.
![[Pasted image 20260908182228.png|center|399]]

**NAT (Network Address Translation)** es una técnica utilizada en redes IP que permite modificar las direcciones IP en los encabezados de los paquetes que atraviesan un router u otro dispositivo de red. Su uso principal es permitir que múltiples dispositivos de una red privada accedan a Internet utilizando una única dirección IP pública.

**Source NAT (SNAT)** se usa cuando un dispositivo de la red privada (A) inicia una conexión hacia uno de la red pública (B, típicamente un servidor). El NAT ve salir el paquete con la IP y puerto privados de A como origen, y los traduce reemplazándolos por su propia IP pública y un puerto asignado, dejando intacto el destino (B). **Destination NAT (DNAT)** es el caso inverso.

Dentro de SNAT tenemos:
- **NAT – Full Cone**: es el tipo menos restrictivo. Una vez que A abre una conexión saliente, cualquier host externo puede enviarle tráfico a esa IP y puerto públicos y el NAT lo va a reenviar hacia A.
- **NAT – IP Restricted**: el NAT sí impone una restricción, pero solo sobre la dirección IP de origen del tráfico entrante.
- **NAT – Port Restricted**: es un paso más estricto que el anterior. El tráfico tiene que venir exactamente del mismo puerto, además de la IP.
- **NAT – Symmetric** es el tipo más restrictivo. Se genera un puerto público distinto por cada combinación de destino (`IP:puerto`).

**Double NAT (SNAT & DNAT)** aparece cuando el cliente está en una red pública (o al menos distinta) y el servidor con el que quiere hablar está en una red privada, publicado detrás de un NAT. 

**Double NAT (SNAT & SNAT)** es el escenario típico de una conexión P2P real: A y B están cada uno detrás de su propio NAT, y ninguno de los dos tiene una regla de DNAT configurada de antemano (porque no es práctico configurar manualmente una regla por cada posible peer). Entonces ambos NATs solo aplican SNAT sobre el tráfico saliente de su respectivo host, pero como no hay ninguna regla que permita el tráfico entrante desde el otro lado, ninguno puede alcanzar directamente al otro sin recurrir a alguna de las técnicas de NAT Traversal.

**UDP Hole** resuelve el problema de conectar dos PCs detrás de NAT/firewall sin depender de un tercero en el momento de la conexión, pero exige una condición fuerte: que ambos lados ya conozcan de antemano el puerto UDP público que va a usar el otro extremo, y que el firewall no cambie ese puerto entre conexiones.

**UDP Hole Punching** es una técnica que requiere que ambas PCs mantengan una conexión TCP permanente hacia un servidor conocido; a través de esa conexión, cada NAT le revela al servidor cuál es su IP y puerto públicos reales (los que usó para esa conexión TCP), y el servidor queda en condiciones de conocer las "coordenadas" públicas de ambos extremos. Cuando A y B quieren conectarse entre sí, el servidor le pasa a cada uno la `IP:puerto público` del otro.

**Session Traversal Utilities for NAT (STUN)** es un protocolo que le permite a un cliente detrás de NAT averiguar con qué IP pública y puerto está saliendo realmente su tráfico. El cliente le manda una consulta a un servidor STUN, y este le responde indicándole la `IP:puerto público` que vio en el paquete que le llegó, dato que el cliente puede usar después para publicarlo en otro protocolo.

**TURN (Traversal Using Relay NAT)** se basa en un relay real que reenvía el tráfico de datos entre los dos extremos cuando el NAT hole punching no logra atravesar el firewall. **ICE (Interactive Connectivity Establishment)** no es una técnica nueva en sí misma, sino un framework que combina y coordina las anteriores.

---
## VPNs

Una **VPN (Virtual Private Network)** se usa para interconectar redes o equipos a través de otras redes, típicamente Internet. Encapsula la comunicación original dentro de otro protocolo, creando un canal lógico entre las dos puntas que atraviesa la red intermedia sin que esta pueda ver el contenido real. Las ventajas de implementar VPN se ven en costos, seguridad y escalabilidad.

En el modo **Cliente a Sitio**, un dispositivo individual se conecta remotamente a la red de un sitio central, como si estuviera físicamente dentro de esa red. En el modo **Sitio a Sitio**, en cambio, lo que se interconecta son dos redes completas entre sí a través de Internet, por ejemplo para unir sucursales de una misma empresa.

En el extremo emisor, el router agrega una cabecera VPN (y su propia IP de tránsito) por delante del paquete original completo, de forma que ese paquete queda **encapsulado** dentro de otro paquete IP nuevo. Ese paquete "exterior" es el que efectivamente viaja por Internet entre los dos routers. Al llegar al otro extremo, el router remoto **desencapsula**: le saca la cabecera IP+VPN externa y recupera el paquete original tal cual salió del host emisor, para entregarlo dentro de la LAN destino.

Es importante tener presente que un paquete que atraviesa una VPN, previamente pasa dos veces por la tabla de ruteo. El paquete original entra y se dirige a una interfaz virtual que le agrega los encabezados mencionados. Esa interfaz virtual reenvía el paquete con dichos headers, entrando por segunda vez a la tabla de ruteo, pero con la IP agregada por la interfaz virtual apuntando al servidor VPN.

Para **autenticar** la conexión entre cliente y servidor VPN se usan principalmente tres protocolos: EAP (Extensible Authentication Protocol), considerado el más seguro; CHAP (Challenge Handshake Protocol); y PAP (Password Authentication Protocol).

---
## DMZ

El **network edge** es el borde entre la red interna (hogareña o empresarial) y la red externa, típicamente Internet. Aunque muchas veces se piensa como "el router" nada más, en la práctica puede ser bastante más que eso: puede incluir firewalls, proxies u otros equipos que en conjunto cumplen la función de frontera.

La **DMZ (Demilitarized Zone)** es una zona de red intermedia entre la red interna y externa, pensada como una especie de tierra de nadie donde se ubican los servicios que necesitan ser accesibles desde Internet, pero sin exponer directamente la red interna. La idea es que si un servicio en la DMZ es comprometido, el atacante no obtiene automáticamente acceso a la red interna real.

Existen básicamente dos topologías para implementar esto. Con **un solo firewall**, el mismo equipo tiene una interfaz hacia Internet, una hacia la DMZ y una hacia la red interna, y es él quien aplica todas las reglas de filtrado entre las tres zonas:
![[Pasted image 20260908204843.png|center|231]]
Con **dos firewalls**, en cambio, la DMZ queda encerrada entre dos equipos distintos: uno mirando hacia Internet y otro mirando hacia la red interna, de forma que un atacante que comprometa el firewall externo todavía tiene que atravesar un segundo firewall independiente para llegar a la red interna:
![[Pasted image 20260908204922.png|center|230]]

Existe un problema de side channel attack, ya que los servidores pueden hablar entre sí. Para corregir este problema se introducen **jump servers** como único punto de entrada administrativo.