## Capa Física

La **capa física** es el soporte físico para entablar comunicaciones. El **medio de coaxil** tiene un core de cobre con un material aislante y otro conductor de malla trenzada que cubre ese material. Esto es contenido por una capa protectora de plástico. Tiene una característica importante que es la inmunidad al ruido.

El **Unshielded Twisted Pair (UTP)** consiste en dos hilos de un material de cobre que funcionan de manera diferencial. Es muy poco inmune al ruido, ya que no tiene la malla que veíamos antes. Para mejorar la supervivencia se lo trenza.

La **fibra óptica** consiste en un filamento de vidrio del grosor de un cabello o de un polímero con características similares al vidrio de la frecuencia a la que transmite. El transporte de información se realiza según dos modos:
- **Multimodo**: Se utiliza para cortas distancias (menores a 1Km), y se idetnfican mediante una cobertura exterior de color naranja.
- **Monomodo**: Se utiliza para distancias largas (mayores a 1Km), y se identifican mediante una cobertura exterior de color amarillo.

Los **cables submarinos** son la misma fibra monomodo que vimos recién pero con embañado mecánico que, según la zona a instalar, es más o menos gordo. 

Los **medios no guiados** transportan ondas electromagnéticas sin usar un conductor físico, propagando la señal a través del aire o del vacío a la velocidad de la luz. El espectro para medios no guiados se divide en tres rangos principales según el uso y comportamiento de la onda:
- **Microondas ($2\text{ GHz}$ a $40\text{ GHz}$):** Se utilizan para enlaces punto a punto terrestres (entre torres de telecomunicación) o enlaces satelitales, requiriendo alineación precisa y línea de vista despejada.
- **Ondas Radioeléctricas ($30\text{ MHz}$ a $1\text{ GHz}$):** Tienen un comportamiento omnidireccional, lo que significa que la señal se propaga en todas direcciones. Por esta razón, son ideales para esquemas de difusión masiva (broadcast), como la radio FM y la televisión abierta.
- **Infrarrojo ($3 \times 10^{11}\text{ Hz}$ a $2 \times 10^{14}\text{ Hz}$):** No pueden atravesar paredes ni objetos sólidos, por lo que su uso queda relegado a aplicaciones locales de corto alcance y dentro de entornos cerrados, como mandos a distancia.

Los **radioenlaces de microondas terrestres** son sistemas de comunicación inalámbrica punto a punto que utilizan ondas electromagnéticas de alta frecuencia para transmitir datos a través de la atmósfera.

En las **comunicaciones inalámbricas por satélite**, los sistemas se clasifican según la altitud de su órbita con respecto a la Tierra:
- **GEO (Geostationary Earth Orbit):** Aporx. $36.000\text{ km}$. El periodo orbital coincide con la velocidad de rotación terrestre y por ende permanece en una posición fija. Facilita la comunicación sin necesidad de mover las antenas receptoras.
- **MEO (Medium Earth Orbit):** Entre $10.000\text{ km}$ y $20.000\text{ km}$. No giran a la misma velocidad angular que la Tierra y son menos comunes para telecomunicaciones convencionales.
- **LEO (Low Earth Orbit):** De $5.000\text{ km}$ o menos. Al estar tan cerca de la Tierra, se desplazan a gran velocidad y requieren antenas motorizadas con capacidad de seguimiento o la creación de constelaciones.

Las **VSAT (Very Small Aperture Terminals)** utilizan antenas parabólicas mucho más compactas, de entre $1\text{ m}$ y $2\text{ m}$ de diámetro (las otras eran muy caras). No cuentan con la potencia suficiente para comunicarse directamente entre sí, y por ende, el enlace siempre debe realizarse mediante el esquema: VSAT $\rightarrow$ Satélite $\rightarrow$ VSAT. Para superar la falta de potencia de las antenas pequeñas y permitir la comunicación entre diferentes terminales: VSAT origen $\rightarrow$ Satélite $\rightarrow$ Hub $\rightarrow$ Satélite $\rightarrow$ VSAT destino.

El **Belio (B)** es una unidad logarítmica que expresa la relación entre dos magnitudes del mismo tipo, como la presión o la potencia respecto a un valor de referencia:
$$\text{Belio} = \log_{10}\left(\frac{\text{Magnitud}}{\text{Referencia}}\right)$$
En sistemas de transmisión, la ganancia o pérdida lineal en veces se define como la razón entre la potencia de salida ($P_o$) y la potencia de entrada ($P_i$):
$$\text{Ganancia (veces)} = \frac{P_o}{P_i}$$

---
## Cableado Estructurado

El **cableado estructurado** es un tendido de cables que provee voz, datos, video, audio, seguridad, control y monitoreo, en cualquier puesto de trabajo. El objetivo es justamente evitar el cableado independiente o propietario por cada servicio (telefonía, datos, monitoreo, etc.) y por proveedor.

El tramo que va desde la toma de usuario en la pared hasta el rack o armario de telecomunicaciones de esa misma planta, es el **tendido horizontal** (con un límite estricto de $100\text{m}$ por canal). Para interconectar los diferentes pisos con la sala de comunicaciones principal (MDF o Data Center), se utiliza el **tendido vertical**, el cual requiere medios de mayor capacidad y ancho de banda.

Historicamente, la infraestructura de cableado en edificios pasó por dos etapas:
- **Instalaciones Heterogéneas:** Redes separadas para voz y datos. 
- **Instalaciones Homogéneas:** Red unificada bajo un mismo estándar.

El cable **Unshielded Twisted Pair (UTP)** que vimos previamente es el medio de cobre estándar utilizado en redes LAN y cableado horizontal. El **cable directo** se utiliza para interconectar dispositivos que operan en diferentes capas de red, como un servidor a un switch o un switch a un router. En cambio, el **cable cruzado** se emplea tradicionalmente para conectar dispositivos que operan en el mismo nivel o que comparten la misma configuración de pines de transmisión y recepción.

Los **conectores** de cobre más comunes son el **RJ-11**, utilizado históricamente en telefonía analógica con 4 o 6 posiciones, y el **RJ-45**, el estándar indiscutido para redes de datos (Ethernet).

El **rack** o gabinete de telecomunicaciones es la estructura metálica estandarizada diseñada para alojar y organizar los equipos de red, paneles de conexiones (patch panels), servidores y sistemas de energía (UPS). La altura útil y la capacidad de los racks se miden en **Unidades de Rack (U o RU)**. Todos los equipos para montaje en rack (como un switch estándar de $1\text{U}$ o un servidor de $2\text{U}$ a $4\text{U}$) respetan esta modularidad vertical y los orificios normalizados en los rieles.

La **patchera de cobre (Patch Panel)** es el elemento pasivo modular (típicamente de $1\text{U}$ o $2\text{U}$ con 24 o 48 puertos) que sirve como punto de terminación y ordenamiento de todo el cableado horizontal que llega al rack. En su vista posterior, los cables UTP rígidos que vienen desde los puestos de trabajo se conectan de forma directa y permanente sin ficha RJ-45. En su vista frontal, cada cable queda expuesto a través de una boca hembra RJ-45 numerada y rotulada.  La patchera se interconecta a los switches mediante cables de parcheo cortos y flexibles  llamados **patch cords**. 

La **roseta** es la caja plástica superficial ubicada en el área de trabajo donde finaliza el extremo de usuario del cableado horizontal. En su interior aloja uno o más conectores hembra, sirviendo como punto de interfaz físico y estandarizado para que el usuario conecte su computadora, teléfono IP o dispositivo de red.

El **piso técnico (Raised Floor)** es una estructura modular sobreelevada mediante pedestales metálicos sobre la losa original, creando una cámara de aire subterránea por donde pueden realizarse tendidos de cables. Las **bandejas de cableado aéreo (Overhead Cabling Trays)**, por el contrario, consisten en sistemas de rejillas o canalizaciones metálicas suspendidas del techo o ancladas por encima de la parte superior de los racks.

La **montante** es el conducto o pozo vertical de la infraestructura de un edificio destinado al paso y soporte ordenado de los cables de datos y telecomunicaciones entre los distintos pisos. Permite interconectar los armarios de distribución de cada planta con la sala principal de equipos de forma protegida.

En un cableado estructurado como el de la imagen, podemos distinguir las siguientes partes:
![[Pasted image 20260813182554.png|center|209]]
1. **Conexión al Dispositivo Final**: el dispositivo es lo que conocemos como estación de trabajo, y puede ser una desktop, una laptop, etc. Se conoce como Work Area (WA). Lo que nos importa es conocer qué cantidad de estaciones de trabajo vamos a necesitar. Contemplan espacios de entre $4\text{m}^2$ y $10\text{m}^2$.
2. **Cableado Horizontal**: son las conexiones rojas que van desde la estación de trabajo hacia el rack 3, que es la sala de telecomunicaciones de piso. Para estas conexiones, generalmente se utiliza cobre y son menores a $100\text{m}$. De ellos, se considera que $90\text{m}$ son de conexión permanente, para así dejar $5\text{m}$ extra de cada lado para futuras necesidades. 
3. **Sala de Telecomunicaciones (TR)**: es donde vamos a tener nuestros racks. Llega el cable proveniente de la roseta y se conecta a una patchera por la parte trasera. Por la parte delantera se utiliza un patch cord corto para conectarse a un switch. Contienen el tráfico acumulado de todas las estaciones de trabajo de ese piso.
4. **Cableado Vertical**: son las conexiones que permiten conectar las salas de telecomunicaciones entre distintos. Se utiliza fibra por las distancias y porque no tiene interferencia, además de ser más rápida. Se quiere conectar los switches de acceso a uno de distribución. Estas conexiones se conocen como uplinks.![[Pasted image 20260811202312.png|center|268]]
5. **Servidores**: se encuentran en el Equipment Room (ER), y es donde van a estar los racks grandes. Cada uno va a tener su propio switch (Switch ToR) que se va a conectar a todos los servidores que contiene dentro. Estos se pueden conectar directo a los switches core, aunque puede haber una capa intermedia si estos últimos no tienen puertos suficientes para todos los ToRs.![[Pasted image 20260813190859.png|center|227]]
6. **Routers y Switches**: es donde se encuentran los switches de las capas de distribución y los core, además de routers que permiten la conexión a internet. Suelen enocontrarce también en el ER.
7. **Conexión externa**: es la conexión entrante y saliente del edificio hacia los proveedores de servicios, como por ejemplo el ISP. El espacio se conoce como Entrance Facilities (EF).

---
## Redes

Un **hub** es un dispositivo de capa 2 que permite aumentar las conexiones de dispositivos terminales a un servicio de red. Replica las tramas que recibe por todas las otras interfaces que tiene, sin ningún tipo de criterio.

Un **puente (bridge)** es un dispositivo de red que se utiliza para interconectar dos segmentos LAN, dividiendo dominios de colisión y filtrando el tráfico al decidir qué tramas se reenvían entre interfaces en función de las direcciones MAC.

Un **switch** consiste en un puente de más de dos puertos. Es un conector similar al hub, pero que posee un poco de inteligencia. Puede construir una **MAC Address Table**, y maneja Unicast, Broadcast y Multicast.
- **Switch Layer 2 - Unmanaged**: Solo conmuta tramas por dirección MAC en un único dominio de difusión predeterminado.
- **Switch Layer 2 - Managed**: Permite configurar parámetros avanzados como VLANs, priorización de tráfico (QoS), seguridad de puertos (Port Security) y prevención de bucles mediante Spanning Tree (STP).
- **Switch Layer 3**: Switch multicapa que cuenta con funciones de enrutamiento IP por hardware (Capa 3), permitiendo rutear tráfico entre diferentes VLANs a velocidad de cable (wirespeed) sin depender de un router externo.

Para garantizar alta disponibilidad y evitar SPOFs, cada switch de la capa de acceso cuenta con un doble enlace ascendente (uplink) conectado en paralelo hacia ambos switches de distribución.

Todos estos componentes son necesarios porque se trabaja sobre un **medio compartido**. Se necesita gestionar este medio porque no se pueden tener enlaces individuales con los distintos dispositivos finales. Si no se gestiona, ocurren las colisiones de tráfico.

El **Stacking de Switches** es una tecnología que permite unir físicamente múltiples switches para que operen y se comporten como un único switch lógico dentro de la red. La interconexión física del stacking se realiza habitualmente en **topología en anillo**, cerrando el circuito con un cable entre el primer y el último switch para garantizar redundancia y tolerancia a fallos en caso de que un enlace o equipo caiga.

Una **VLAN (Virtual Local Area Network)** es una tecnología que permite segmentar una red física en múltiples redes lógicas independientes, definiendo dominios de broadcast acotados y garantizando la separación y seguridad del tráfico entre diferentes áreas o servicios. Al utilizar stacking, una misma VLAN puede extenderse a través de múltiples switches físicos dentro de la matriz.

En un puerto configurado como **VLAN Untagged** (puerto de acceso), los dispositivos finales no reconocen ni gestionan etiquetas de VLAN, simplemente transmiten y reciben tramas estándar de Ethernet. En una interfaz configurada como **VLAN Tagged** los extremos son conscientes de la pertenencia a múltiples redes y requieren que las tramas incluyan explícitamente el encabezado VLAN Tag. Un puerto en modo **VLAN Trunk** está diseñado para transportar el tráfico de múltiples VLANs a través de un único enlace físico mediante el etiquetado de tramas.

El  **Spanning Tree Protocol (STP)** es un protocolo que detecta caminos redundantes y bloquea lógicamente determinados puertos para mantener una topología libre de bucles, activándolos automáticamente solo en caso de que falle un enlace activo. El objetivo de STP es construir una topología lógica en forma de árbol deshabilitando los enlaces redundantes para evitar bucles. Para ello, todos los switches participan en la elección de un nodo central llamado **Root Bridge**, el cual se define a partir del Bridge ID de menor valor. Una vez establecido el nodo raíz, cada switch no-root selecciona un único **Root Port**, que corresponde a la interfaz física con el menor costo de enlace para alcanzar al Root Bridge. Finalmente, los enlaces sobrantes que podrían generar loops se colocan en estado bloqueado.

El **diseño tradicional de datacenters** utiliza una arquitectura jerárquica pensada para centralizar el flujo de datos hacia el exterior (tráfico Norte-Sur). Los servidores dentro de cada rack se conectan a los ToR en Capa 2, los cuales concentran su tráfico en switches de agregación intermedios, para finalmente confluir en los switches de núcleo (Core en Capa 3). 

La **arquitectura moderna Spine-Leaf** está diseñada para optimizar el tráfico Este-Oeste (East/West), es decir, la comunicación intensiva y horizontal directa entre servidores dentro del data center. En este esquema de dos niveles, los servidores se conectan a los switches de acceso (Leaf, L2/L3) y cada uno de estos se enlaza de forma directa con absolutamente todos los switches centrales (Spine, L3), sin conexiones entre spines ni entre leafs. 

**Power over Ethernet (PoE)** es una tecnología estandarizada bajo la norma IEEE 802.3af que permite suministrar energía eléctrica a través de los mismos pares de cobre del cable de red utilizados para la transmisión de datos.

Un **router** es un dispositivo de red de Capa 3 cuya función principal es conectar redes distintas y gestionar el reenvío de paquetes entre ellas en función de sus direcciones IP de destino. En la práctica, se utiliza típicamente como el equipo de borde que interconecta una LAN con una WAN.

Una **WAN (Wide Area Network)** es una red de telecomunicaciones que interconecta múltiples redes locales (LAN) a través de grandes distancias geográficas. Existen distintos tipos de WAN:
- **Línea dedicada**: Enlace punto a punto exclusivo y privado provisto por la operadora de telecomunicaciones.
- **Multiprotocol Label Switching (MPLS)**: Red privada virtual gestionada por el ISP que utiliza etiquetas para conmutar paquetes de forma rápida. 
- **Banda ancha (DSL/Cable/Fibra)**: Conexiones de acceso a Internet estándar y de bajo costo. Se utilizan habitualmente en oficinas remotas o sucursales pequeñas.
- **Wireless (4G/5G)**: Conectividad inalámbrica celular (a través de redes públicas de operadoras o redes 5G privadas). Se emplea principalmente como enlace de respaldo (backup) ante caídas de la línea principal o para brindar acceso en ubicaciones temporales y de difícil despliegue físico.

Los proveedores de telecomunicaciones comercializan diferentes modalidades de vínculos WAN según el nivel de control, el ancho de banda y la infraestructura requerida:
- **Punto a Punto**: Enlace directo y dedicado entre dos ubicaciones mediante la instalación de un router en cada extremo.
- **LAN to LAN**: Interconexión transparente de redes de área local ubicadas en sitios remotos a través del backbone del proveedor. 
- **Fibra oscura**: Arrendamiento de filamentos de fibra óptica ya tendidos e instalados físicamente por la empresa de telecomunicaciones que se encuentran sin iluminar (sin equipamiento óptico activo conectado). El cliente adquiere el derecho de uso exclusivo y aporta sus propios transmisores y switches para gestionar el protocolo, la velocidad y la capacidad total del enlace.

**Wi-Fi (Wireless Fidelity)** es la tecnología estándar de redes locales inalámbricas (WLAN) regida por la familia de normas IEEE 802.11x. En los **medios compartidos**, el emisor chequea y, si está libre el medio, transmite. Esto tiene dos problemas principales:
- **Problema Near-Far**: Ocurre cuando dos emisores transmiten hacia el receptor simultáneamente y , por las diferencia de distancias, la señal del nodo más cercano arriba con una potencia significativamente superior, saturando el receptor y enmascarando por completo la señal débil del nodo lejano.
- **Problema Hidden Node**: Sucede cuando dos estaciones están dentro del rango de cobertura del Access Point pero fuera del alcance mutuo. Al no poder escucharse entre sí, ambas asumen que el canal está libre e inician transmisiones en paralelo hacia el AP, provocando colisiones destructivas en el receptor. 

---
## Protocolos de Ruteo

Un **Sistema Autónomo (AS)** es un conjunto de redes administradas por el mismo ente. Rige una sola política de ruteo.  NO necesariamente es un ISP. 
![[Pasted image 20260819103846.png|center|380]]

El objetivo de un protocolo de ruteo es crear una **tabla de ruteo** con "costos" mínimos para llegar a destino. Cada protocolo define ese costo utilizando variables específicas. En un esquema de **enrutamiento distribuido**, no existe una entidad centralizada que calcule la topología completa, sino que cada router procesa de forma autónoma la información de la red.

Los **EGP (Exterior Gateway Protocol)** se suelen usar al cambiar de países, o empresas, por ejemplo. Debemos pensar que, para que entre en juego su utilización, debemos estar hablando de un cambio grande o significativo. 
- **Path Vector Routing**: Es un protocolo basado en tres pilares:
	- **Ruteo por Path:** Los anuncios incluyen el path que decidió el router y sirve para detectar loops. 
	- **Ruteo Jerárquico:** Se rutea dentro de los AS y fuera de los AS de manera independiente. 
	- **Direccionamiento Topológico:** Se asignan ruteo por bloques de direcciones. 

**BGP (Border Gateway Protocol)** es el protocolo estándar de vector de trayectoria diseñado para interconectar ASs a escala global. Sus sesiones de vecindad se configuran de manera puramente manual y corren sobre TCP por el puerto `179` para garantizar una transmisión confiable de los anuncios de enrutamiento. 

BGP debe su éxito y predominio en Internet a su capacidad para aplicar **políticas de tránsito** altamente configurables, en lugar de limitarse a criterios rígidos de rendimiento técnico. Estas políticas se definen por razones de seguridad, motivos políticos o conveniencia económica.

El mecanismo fundamental de BGP para evitar bucles (loops) de enrutamiento se basa en la inspección de `AS-PATH`:
- Descarte por coincidencia de ASN
- Invariabilidad de la ruta

Los **Interior Gate Protocol (IGP)** se utilizan dentro de un Sistema Autónomo, por lo que están diseñados para redes pequeñas, e incluye protocolos como RIP, OSPF, iBGP, EIGRP. Estos protocolos no se preocupan por enrutamiento hacia entidades externas al sistema autónomo. Se pueden clasificar en:
- **Link-State Routing**: Cada router construye una visión completa e idéntica de la topología de la red para luego calcular de forma independiente los caminos más cortos hacia cada destino.
	- OSPF
	- IS-IS
- **Protocolos de Vector Distancia**: Cada nodo conoce la red únicamente a través de los anuncios que intercambia de forma periódica o disparada por eventos exclusivamente con sus vecinos directos ("ruteo por rumor").
	- RIPv1
	- IGRP

Podemos comparar:

|                                         **Link State**                                          |                    **Distance Vector**                     |
| :---------------------------------------------------------------------------------------------: | :--------------------------------------------------------: |
|         Cada router comparte el mapa completo que tiene de la red con todos los routers         |   Cada router comparte su tabla de ruteo con sus vecinos   |
| Las decisiones de ruteo, se toman con todo el mapa completo de la red (mas reliable y accurate) | Las decisiones de ruteo, se basan en información limitada  |
|                                      Difícil de configurar                                      |                    Fácil de configurar                     |
|                                       Convergencia rápida                                       |                       Converge lento                       |
|          Su métrica esta dada por multiples factores: bandwith, delay en un link, etc           | Su métrica es la cantidad de saltos entre origen y destino |
|                                Preferible para networks grandes                                 |              Preferible para networks chicas               |

La **IANA (Internet Assigned Numbers Authority)** es el organismo responsable de la coordinación global del direccionamiento en Internet, encargado de asignar bloques de **[[06. Capa de Red|direcciones IP]]** (IPv4 e IPv6) y **números de sistemas autónomos (ASN)**.

En el ecosistema global de Internet, los Sistemas Autónomos se estructuran en tres tipos según su conectividad y políticas de tránsito:
- **Red Stub**: Posee una única conexión hacia la red BGP (un solo ISP). Al ser un extremo de la topología sin caminos alternativos, no transporta tráfico de terceros; solo origina y recibe paquetes propios.
- **Red Multiconexión**: Cuenta con múltiples conexiones hacia diferentes Sistemas Autónomos para redundancia y balanceo de carga. Sin embargo, no actúa como red de paso: rechaza el reenvío de paquetes cuyo origen y destino pertenezcan a ASs externos ajenos a su red.
- **Redes de Tránsito**: Infraestructuras diseñadas para transportar tráfico de terceros entre distintos Sistemas Autónomos. Aplican políticas y restricciones de enrutamiento y cobran comercialmente por el servicio de tránsito IP prestado.

El **mecanismo de BlackHole** en BGP es una técnica utilizada para mitigar ataques DDoS. Consiste en anunciar una ruta específica para la dirección IP de la víctima de modo que el tráfico entrante sea redirigido hacia una interfaz nula o destino de descarte (`Null0`). El mecanismo opera anunciando una ruta de host específica para la IP víctima bajo ataque:
1. Publicación de máscara específica
2. Soporte del Carrier/ISP
3. Descarte en el borde

La **Distancia Administrativa (AD)** es el criterio utilizado por un router para seleccionar la mejor ruta hacia un destino cuando este es aprendido simultáneamente a través de diferentes protocolos de enrutamiento o fuentes administrativas. Define el grado de confiabilidad de la fuente mediante un valor entero entre `0` y `255`.

**IGRP (Interior Gateway Routing Protocol)** es un protocolo de enrutamiento interior por vector de distancia desarrollado por Cisco. Su principal innovación fue la implementación de una métrica compuesta. Luego, Cisco desarrolló **EIGRP (Enhanced Interior Gateway Routing Protocol)**, un protocolo de enrutamiento por vector de distancia avanzado (o híbrido) sin clase. A diferencia de su antecesor, elimina por completo las actualizaciones periódicas por broadcast: los routers solo envían actualizaciones parciales y dirigidas en el momento exacto en que se produce una modificación en la topología.

---
## Wide Area Network (WAN)

Una **WAN (Wide Area Network)** es una red de telecomunicaciones diseñada para interconectar múltiples redes locales (LAN) dispersas en distintas ciudades, países o continentes. Puede ser pública (Internet) o privada. Esta última se puede clasificar en:
- **Dedicada:** Consiste en otorgar un porción de la red para uso exclusivo de un cliente. Tiene muy poco overhead pero es más caro.
- **Switched**: La infraestructura del proveedor es compartida con otros clientes que tenga de manera segura.
	- **Circuit-Switched**: Establece dinámicamente una conexión dedicada para voz o datos entre un emisor y un receptor. Se establece la conexión previamente a comenzar cualquier comunicación. 
	- **Packet-Switched**: Es un circuito virtual punto a punto establecido utilizando la red de un proveedor, que permite a múltiples clientes compartir sus recursos. 

Existen dos tipos de redes:
- **Redes Broadcast** (Generalmente LAN): Como por ejemplo el Wi-Fi, donde todos nos conectamos.
- **Redes Punto a Punto** (Generalmente WAN): Las puntas normalmente son routers o switches, no computadoras.

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
- **Cola Personalizada**: Aplica Round-Robin para alternar de forma cíclica entre distintas colas. El administrador puede definir qué tipo de tráfico se asocia a cada una y otras reglas.
- **Weighted Fair Queueing (WFQ)**: Crea dinámicamente una cola separada para cada flujo de tráfico individual. El algoritmo busca la equidad al balancear flujos de poco caudal frente a transferencias masivas.

La **clasificación de tráfico** permite identificar y categorizar los paquetes según criterios como listas de control de acceso (ACL por IP y puerto), el puerto físico del switch o el tipo de aplicación. Una vez clasificado el flujo, el router o switch procede al etiquetado insertando marcas en la cabecera del paquete en Capa 2 o Capa 3 para que los dispositivos subsiguientes reconozcan su prioridad sin reanalizarlo.
- **Capa 3**: Se implementa sobre la cabecera IPv4 redefiniendo el antiguo campo ToS (Type of Service) bajo el estándar DSCP (Differentiated Services Code Point).
- **Capa 2**: La priorización está orientada a entornos LAN y opera a nivel MAC mediante el estándar IEEE 802.1p, el cual se inserta dentro del encabezado de VLAN.

En la configuración de un **Firewall/Router**, las reglas de filtrado permiten controlar el flujo de tráfico entre diferentes zonas de la red definiendo una acción específica (Allow, Deny o Discard). Para cada regla se establecen la zona de origen y destino, el servicio o protocolo de aplicación involucrado, y los criterios de origen, destino y usuarios autorizados. 

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

Los **carriers** son los operadores de telecomunicaciones propietarios de las redes troncales de Internet, y son los responsables del transporte de datos. No nos podemos desentender de ellos, porque a la larga alguien debe brindar conectividad hacia donde el ISP no llega, como por ejemplo hasta Japón.

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
	- Red donde se interconecta con otras redes (ISPs/IXP)
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