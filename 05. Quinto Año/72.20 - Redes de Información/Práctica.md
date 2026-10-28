## Protocolo

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

---
## BGP

[[AGREGAR LA CLASE PRACTICA DE BGP]]

---
## AWS

Un **proveedor de servicios cloud** es una compañía que nos brinda servicios de cómputo on demand. La idea es poder utilizar servicios para nuestra aplicación sin tener que administrar la infraestructura que hay detrás. En lugar de comprar el hardware, configurarlo, deployarlo, administrarlo y mantenerlo, contratamos al cloud provider para que se encargue de todo eso y nos ofrezca una interfaz para modificar y administrar esos servicios.

**AWS** es el cloud provider más grande y es el que vamos a usar en la práctica. La mayoría de los conceptos que veamos tienen un servicio u objeto equivalente en **GCP** (la nube de Google), por lo que, más allá de que la consola sea distinta, las ideas se trasladan de una plataforma a otra.

---
## Infraestructura Global de AWS

La nube de AWS está dividida en **regiones**, que son ubicaciones geográficas completamente aisladas e independientes entre sí y que agrupan una serie de datacenters. Hay regiones en Estados Unidos, Canadá, México, Brasil, Europa, China, Australia, etc. (no hay una en Argentina). Dividir la nube en regiones tiene varias ventajas:
- **Aislar fallas**, ya que al ser independientes, si una región se ve afectada el resto sigue funcionando y no existe un single point of failure global. Por ejemplo, durante la guerra en Medio Oriente se dio de baja una región (la de Bahrain) porque uno de sus datacenters fue afectado.
- **Reducir la latencia**, porque tenemos los recursos más cerca de los usuarios.
- **Cumplir con los requisitos legales** de cada país, como las leyes de protección de datos. Si operamos en un país con este tipo de regulaciones, usamos regiones dentro de ese país.

También existen **regiones especializadas**, como **GovCloud** o la de China, que solo pueden ser utilizadas por ciertas entidades. Por ejemplo, en GovCloud solo ciudadanos estadounidenses pueden hacer deployments o acceder a los logs, por lo que cualquier otra persona necesita de un operador intermediario.

Todos los recursos que creemos (salvo algunas excepciones que son globales) pertenecen a una región, y no se replican automáticamente entre regiones. Si la región se ve afectada, nuestro recurso también. Si necesitamos que la aplicación esté distribuida en varias regiones, lo tenemos que hacer manualmente, AWS no lo hace por nosotros. Por la misma razón, en la consola siempre trabajamos dentro del contexto de una región, y si cambiamos de región dejamos de ver los recursos creados en la anterior.

Dentro de cada región tenemos como mínimo tres **availability zones (AZs)**, aunque puede haber más (North Virginia, por ejemplo, tiene seis). Cada AZ está compuesta por uno o más datacenters físicos aislados entre sí que forman un único **datacenter lógico**. La AZ es la mayor granularidad que podemos elegir, es decir, elegimos en qué AZ corre nuestro recurso pero no en qué datacenter dentro de ella.

Los datacenters están conectados por redes de muy baja latencia y cada uno tiene alimentación, refrigeración y seguridad física independientes. Además, las AZs de una región están separadas por un máximo de 100 km. Deben estar lo suficientemente alejadas como para que una catástrofe (natural, una guerra, etc.) no afecte a varias al mismo tiempo, pero lo suficientemente cerca como para mantener una latencia de un solo dígito (en milisegundos).

>[!TIP] Importante
>Todo en AWS está pensado para ser tolerante a errores. La jerarquía es Región → Availability Zones (mínimo 3) → uno o más datacenters físicos por AZ, vistos como un único datacenter lógico.

Además de regiones y AZs, AWS tiene otros componentes de infraestructura:
- **Local Zones**, que son como mini availability zones que extienden a una región madre para tener ciertos recursos más cerca de los usuarios. Ofrecen solo algunos servicios básicos (generalmente de cómputo y algunas bases de datos), no el catálogo completo. Están conectadas directamente con la región, por lo que sirven cuando necesitamos baja latencia, y también para cumplir regulaciones locales. Por ejemplo, hay una en Buenos Aires. Son más caras y más limitadas.
- **AWS Outposts**, donde AWS instala servidores en nuestro propio datacenter. En la práctica es como tener una availability zone propia corriendo servicios de AWS. Está pensado para empresas muy grandes.
- **Edge Locations**, que se usan para casos de uso que necesitan estar muy cerca de los usuarios y ser muy rápidos, como **CDN** (Content Delivery Network), firewalls (**WAF**) y servicios de DNS. Con una CDN guardamos contenido (imágenes, videos) cerca de los usuarios para no tener que viajar hasta la región; por ejemplo, el contenido de un bucket de **S3** (servicio de almacenamiento de objetos, es decir, archivos) se descarga mucho más rápido si usamos edge locations. Con WAF podemos filtrar el tráfico antes de que entre a la región, rechazándolo mucho más rápido.

---
## Costos y Alta Disponibilidad

Hay dos cosas que siempre tenemos que tener presentes al diseñar una arquitectura en la nube.

La primera es **considerar el costo de los servicios**. Antes de usar un servicio tenemos que revisar cuánto va a costar según el uso que esperamos darle y evaluar si hay alguna forma más barata de hacerlo. Los precios de cloud no parecen altos al principio, pero se acumulan muy rápido. Para esto AWS provee una **calculadora de precios**, donde elegimos el servicio, su configuración y el uso esperado, y nos devuelve el costo mensual y anual.

Hay una parte de la industria que considera que los precios de cloud se fueron de las manos y que, para ciertos casos de uso, conviene volver a **on-premise**. El ejemplo más conocido es el de **37signals**, la empresa de DHH (creador de Ruby on Rails), que gastaba alrededor de 280 mil dólares por mes en AWS. Solo en OpenSearch gastaban 43 mil dólares por mes, así que invirtieron 150 mil dólares en hardware propio y recuperaron la inversión en tres meses, ahorrando luego unos 40 mil dólares mensuales. Esto aplica a casos muy particulares, pero muestra lo fácil que es terminar con una factura enorme al ir conectando servicios.

La segunda es pensar siempre en **alta disponibilidad**. Vamos a querer diseñar nuestras aplicaciones para que se ejecuten en **múltiples availability zones**, de forma que si cae una AZ la aplicación siga funcionando. Esta es la regla número uno de resiliencia en AWS. Siempre nos preguntamos qué pasaría si falla un componente, si eso tira abajo toda la aplicación y cuánto dinero nos costaría por segundo tenerlo caído.

>[!TIP] Importante
>Siempre hay un trade-off entre alta disponibilidad y costos, ya que la alta disponibilidad es más cara. Debemos buscarla en los recursos que realmente la necesiten, no duplicar todo porque sí.

---
## VPC y Subredes

La **VPC (Virtual Private Cloud)** es el componente más básico de redes en AWS. Es una red virtual privada que nos permite aislar nuestros recursos, es decir, una red que es solo nuestra y en la que solo nosotros controlamos qué entra y qué sale. Al crearla definimos su bloque de direcciones, por ejemplo `10.0.0.0/16`.

Dentro de la VPC tenemos **subnets**, que no son más que un rango de IPs perteneciente a una availability zone. Básicamente es el ejercicio de subnetting que ya vimos, partimos la red de la VPC en subredes (por ejemplo, varias `/24`).

En AWS no existen tipos de subred, pero sí podemos catalogarlas como:
- **Subredes públicas**, que son accesibles desde internet.
- **Subredes privadas**, que no son accesibles desde internet.
- Otras categorías más especiales, como las **aisladas** (sin ningún acceso a internet) o las que solo son accedidas desde una VPN.

Lo que define si una subred es pública o privada es su **route table** (tabla de ruteo), que contiene las reglas que indican a dónde enviar el tráfico. Si la tabla tiene una ruta hacia internet a través de un Internet Gateway, la consideramos pública; si no, es privada. Todas las route tables tienen una **ruta local implícita** que permite que cualquier recurso de la VPC se comunique con cualquier otro recurso de la misma VPC, sin importar la subnet en la que esté. Lo que bloquea la comunicación entre recursos de una misma VPC son los security groups, no el ruteo.

Para comunicar nuestra VPC con otras redes usamos **gateways**. Los dos principales son:
- **Internet Gateway**, que conecta la VPC a internet de forma **bidireccional**, es decir, desde internet se puede acceder a la VPC y desde la VPC se puede acceder a internet. Se asocia a la VPC.
- **NAT Gateway**, que permite una comunicación **unidireccional**, es decir, que los recursos dentro de la VPC se conecten a internet sin quedar expuestos, de modo que desde internet no se pueda acceder a ellos. Se crea en una subnet, y esa subnet debe ser **pública**, porque el NAT Gateway necesita salir a internet a través del Internet Gateway. Además, necesita una IP pública (Elastic IP).

De esta forma, la route table de la subred pública tiene una ruta `0.0.0.0/0 → Internet Gateway`, mientras que la de la subred privada tiene `0.0.0.0/0 → NAT Gateway`. Una subred cuya tabla solo tiene la ruta local no puede ni conectarse a internet ni ser accedida desde internet (es una subred aislada).

>[!WARNING] Costos
>El NAT Gateway es muy caro, alrededor de 32 dólares por mes más cargos por gigabyte transferido. Hay que borrarlo apenas deje de ser necesario.

Que un recurso esté en una subnet pública no significa que esté automáticamente disponible en internet. Para eso necesita tener una **IP pública**. Las IPs públicas en AWS se cobran, en especial las fijas, que se pagan por cada hora de uso. Una IP fija en AWS es una **Elastic IP**, y como hay muy pocas IPv4 disponibles en el mundo, la cantidad por región está muy limitada (por defecto, 5). Asignarle una IP fija a un recurso no es un caso de uso tan común.

>[!WARNING] Corrección
>En clase quedó en duda si un recurso de una subnet pública necesita su propia IP pública para salir a internet. En realidad sí la necesita. El Internet Gateway no tiene una IP pública propia, sino que traduce la IP privada de cada recurso a la IP pública que tiene asociada. Un recurso en una subnet pública sin IP pública no puede ni acceder a internet ni ser accedido desde internet. Por eso el NAT Gateway también necesita su propia IP pública.

Cuando creamos una cuenta, AWS crea una **default VPC** que tiene una subnet pública por cada availability zone de la región, comparten una misma route table con salida al Internet Gateway, y no tiene subnets privadas ni NAT Gateway.

---
## EC2

Para correr nuestra aplicación necesitamos instancias de cómputo, que en AWS son las instancias de **EC2**. Una EC2 no es más que una máquina virtual. Hay diferentes tipos de instancias según el propósito:
- **Optimizadas para cómputo**, con mucha CPU y quizás menos RAM.
- **Optimizadas para memoria**, al revés que las anteriores.
- **De propósito general**, que son las que usamos generalmente para aplicaciones normales o microservicios.

Dentro de cada tipo hay **series**. Las más comunes son:
- **Serie M**, de propósito general, pensadas para tráfico predecible donde priorizamos la estabilidad. Son un poco más caras, pero muy estables y buenas para tráfico productivo. Se cobran por segundo de ejecución.
- **Serie T**, que se usan para ambientes no productivos o con menor tráfico, que generalmente es estable pero puede tener algunos picos. Usan un sistema de **CPU credits**, en el que la instancia acumula créditos mientras está en idle o con bajo consumo, y cuando su consumo supera un threshold empieza a gastar esos créditos. Si se le acaban, AWS hace **throttling** de la instancia y podemos tener problemas, como que la aplicación se caiga por falta de procesamiento.

>[!WARNING] Corrección
>En clase se dijo que al quedarse sin créditos la aplicación se puede caer por no tener suficiente memoria. En realidad, el sistema de créditos de las instancias T solo afecta a la CPU; la memoria asignada no cambia.

Dentro de cada serie hay distintos **tamaños**, que se repiten entre series y definen cuántas vCPUs y cuánta RAM tiene la instancia, además del ancho de banda de red, el tipo de storage, etc. Elegimos la instancia según lo que necesite nuestra aplicación para el tráfico que va a recibir.

Al crear una EC2 tenemos que elegir una **AMI (Amazon Machine Image)**, que es una imagen con cierto software y configuración ya instalados. Es como elegir el sistema operativo y las aplicaciones o configuraciones con las que arranca la instancia, es decir, el punto de partida. Por ejemplo, si nuestra aplicación funciona sobre un Ubuntu plano, elegimos la AMI de Ubuntu; si necesitamos Nginx, podemos buscar una AMI que ya lo tenga instalado y configurado. Es un concepto similar al de las imágenes de Docker. Existe un **marketplace** de AMIs pagas y gratuitas, oficiales y no oficiales, de partners y de la comunidad. Es importante conocer el **username por defecto** de cada AMI, ya que es el que usamos para conectarnos por SSH (en la de Amazon Linux es `ec2-user`).

Las EC2 están **separadas del storage**. Para almacenamiento usamos **volúmenes**, que tienen distintos tamaños y tipos.

>[!TIP] Importante
>Como el cómputo y el storage están separados, podemos tener una instancia apagada que no consume nada, pero su volumen sigue existiendo y ocupando espacio físico en AWS, por lo que nos siguen cobrando por él.

---
## Security Groups

Los **security groups** son la forma de controlar el tráfico de los recursos de AWS. Definen qué tráfico de entrada (inbound) y de salida (outbound) está permitido para los recursos asignados a ellos. Son **stateful** y no son más que una serie de reglas que podemos asignar a los recursos que queramos (un recurso puede tener varios security groups). En las reglas podemos elegir el protocolo, el puerto, el origen o destino (una IP, un rango o un recurso), etc. Por ejemplo, podemos permitir que a una instancia solo le llegue tráfico por el puerto 80.

Funcionan como un firewall alrededor de los recursos, con una gran diferencia: las reglas son solo de **allow**. Es una **allowlist**, no una blocklist. Todo lo que no está permitido explícitamente queda bloqueado, pero no podemos crear reglas que bloqueen tráfico.

Si queremos que dos instancias se comuniquen, tenemos que configurar ambos lados, permitiendo la salida desde la instancia 1 hacia la 2 en el security group de la primera, y la entrada desde la instancia 1 en el security group de la segunda.

Lo más poderoso de los security groups es que también sirven como **identificador de un grupo de recursos**. Podemos usar un security group como origen o destino en las reglas de otro. Por ejemplo, si tres instancias de nuestra aplicación comparten un security group y necesitan acceder a una base de datos, la base de datos puede tener su propio security group que solo permita tráfico entrante desde el security group de las aplicaciones. Así no tenemos que especificar la IP de cada recurso (que además puede cambiar), y si agregamos nuevas instancias con ese security group, automáticamente quedan incluidas.

>[!TIP] Importante
>Los security groups se comparten entre cosas que son básicamente iguales, como las réplicas de una misma aplicación. Recursos distintos (una aplicación y una base de datos, o dos aplicaciones diferentes) deben tener security groups distintos, aunque hoy tengan las mismas reglas, porque si mañana cambiamos las reglas de uno no queremos afectar al otro. Todo recurso que creemos debería tener un security group asignado.

---
## RDS

**RDS** es el servicio de bases de datos relacionales **manejado** por AWS (Postgres, MySQL, etc.). Que sea manejado significa que no tenemos que administrar las instancias que corren internamente, y además nos provee muchas funcionalidades extra, como manejar los upgrades, hacer migraciones de datos o automatizar los backups. En lugar de levantar una EC2, ponerle un storage, instalarle la base de datos y administrarla a mano, AWS hace todo eso por nosotros.

La base de datos va en una subred **privada**, ya que no tiene que ser accesible desde internet, y tiene su propio security group.

Para alta disponibilidad, RDS ofrece la funcionalidad **Multi-AZ**. No tenemos que crear dos RDS a mano, definir cuál es primario y cuál réplica, mantener la replicación y hacer el failover manualmente cuando uno se cae. Con solo activar una opción, AWS mantiene automáticamente una copia de la base de datos en otra availability zone. Nosotros lo vemos como un único RDS con un único endpoint, y si la AZ del primario se cae, AWS redirige automáticamente el tráfico a la copia y la convierte en primaria.

>[!WARNING] Corrección
>En clase se dijo que Multi-AZ es más barato que tener dos RDS corriendo. En realidad, una instancia Multi-AZ cuesta aproximadamente el doble que una Single-AZ, ya que AWS mantiene una instancia standby completa. El ahorro está en que no tenemos que encargarnos de la replicación ni del failover.

---
## Arquitectura en Capas

Una primera arquitectura posible es en **dos capas**, con la aplicación (EC2) en una subred pública y la base de datos (RDS) en una subred privada. La aplicación se puede comunicar con la base de datos por dos motivos: la ruta local implícita de la route table y que el security group de la aplicación tiene una salida hacia el security group de RDS (y este permite esa entrada).

Esta arquitectura no está mal, pero enciende algunas alarmas. Si tenemos múltiples instancias de la aplicación, todas estarían en la subred pública, cada una con su IP pública (que se paga), y tendríamos que ser muy cuidadosos con el security group de cada una, porque un error podría exponer las instancias a internet sin control.

La solución es una arquitectura en **tres capas**:
1. **Subred pública**, con los recursos que pueden ser accedidos desde internet.
2. **Subred privada**, con los recursos que queremos proteger de internet pero que necesitan conectarse a internet (por ejemplo, para consumir una API externa), a través del NAT Gateway. Acá va la aplicación.
3. **Subred aislada**, con los recursos que ni necesitan ser accedidos desde internet ni acceder a internet. Su route table solo tiene la ruta local. Acá va el RDS.

La ventaja es que cada recurso queda **lo más aislado posible por defecto**. Si nos equivocamos en un security group de la aplicación y permitimos acceso desde cualquier IP, solo van a poder acceder IPs de nuestra propia red, porque está en una subred privada. Si nos equivocamos en el security group del RDS, solo podrá ser accedido desde la VPC, y quien acceda no podrá conectarse a internet. Los security groups se suman encima, pero el default ya es seguro.

La cantidad de capas depende de la aplicación. Si es una sola instancia, probablemente la pongamos en una subred pública y listo; a medida que la arquitectura crece, vamos a querer tener las cosas lo más aisladas posible.

---
## Load Balancers

Con la aplicación en una subred privada, el problema es cómo llegar a ella desde internet. Para eso usamos un **load balancer**, que distribuye el tráfico entre ciertos **targets**. El load balancer recibe el tráfico público y lo distribuye entre las instancias privadas, que usan el RDS como storage, y el RDS solo puede ser accedido por servicios internos. Cada elemento queda lo más seguro posible por defecto.

El load balancer tiene una dirección pública (en realidad, AWS nos da un nombre DNS) y se asocia a las **subredes públicas** que elijamos. Aunque lo asociemos a varias subredes, nosotros vemos un único load balancer lógico; AWS internamente crea objetos en cada una de esas subredes, que funcionan como el load balancer "físico". Puede ser **internet-facing**, para exponer la aplicación a internet, o **interno**, para servicios internos.

El load balancer también tiene su propio security group, distinto al de las aplicaciones, ya que tiene reglas diferentes (acepta tráfico público, mientras que las aplicaciones aceptan tráfico del load balancer y quizás de otros servicios internos en otros puertos).

Existen distintos tipos de load balancers:
- **Application Load Balancer (ALB)**, que trabaja en capa 7 (HTTP/HTTPS). Permite rutear según el host, un header o el path. Es el que más nos interesa para aplicaciones web.
- **Network Load Balancer (NLB)**, que trabaja en capa 4 (TCP/UDP).
- **Gateway Load Balancer**, que trabaja en capa 3 (IP).

>[!WARNING] Corrección
>En clase se mencionó SSH como protocolo del ALB. En realidad, el ALB solo maneja HTTP y HTTPS (y gRPC); para otros protocolos sobre TCP, como SSH, se usa un NLB.

El load balancer redirige el tráfico a un **target group**, que puede estar formado por instancias, IPs o funciones Lambda. Para saber si un target está disponible para recibir tráfico, el load balancer corre **health checks** contra un endpoint de cada instancia. Podemos configurar cada cuánto se ejecutan, cuántos éxitos o errores consecutivos se necesitan para considerarla healthy o unhealthy, el timeout y el endpoint (lo lógico es un endpoint como `/ping` donde la aplicación responda que está viva). Por defecto, el health check se ejecuta cada 30 segundos, espera un 200 en menos de 5 segundos y necesita 5 éxitos consecutivos para considerar healthy a la instancia. Si una instancia falla los health checks, el load balancer deja de enviarle tráfico.

---
## Arquitectura Multi-AZ

Si toda nuestra arquitectura está en una única availability zone y esa AZ se cae, la aplicación queda completamente caída. Para solucionarlo, agregamos una segunda AZ y **duplicamos los recursos**, con una subred pública, una privada y una aislada en cada AZ, cada una con su propio rango de IPs.

Analizando cada componente:
- El **load balancer** no se duplica, sino que se asocia a las subredes públicas de ambas AZs. Sigue siendo un único load balancer.
- Las **instancias de la aplicación** sí o sí tienen que estar duplicadas, con al menos una en cada AZ. Si la aplicación es **stateless** (todo el estado está en la base de datos), podemos tener tantas instancias como queramos sin problema. Esa es la práctica común, ya que un servicio que guarda estado no se puede escalar.
- El **RDS** se resuelve con la funcionalidad Multi-AZ, sin tener que crear otro a mano.
- Las instancias de la aplicación comparten un **único security group**, ya que son réplicas y tienen el mismo tráfico de entrada y salida. Así, si queremos cambiar las reglas, lo hacemos en un solo lugar.
- El **NAT Gateway**, lo correcto es tener uno por AZ, porque si se cae la AZ donde está perdemos la salida a internet desde las subredes privadas de la otra AZ.

En resumen, lo que nos importa es tener al menos dos copias de cada recurso en AZs distintas. Algunos servicios de AWS ya tienen una funcionalidad Multi-AZ que mantiene esas copias por nosotros.

---
## Implementación en la Consola

Al implementar la arquitectura en la consola de AWS, hay algunos detalles de configuración a tener en cuenta:
- La VPC se puede crear sola (y luego crear a mano cada subnet, route table y gateway) o con el **wizard**, que crea la VPC, las subnets (públicas y privadas, en múltiplos de la cantidad de AZs), las route tables, el Internet Gateway y opcionalmente el NAT Gateway. El wizard crea una route table por cada subnet privada y una única compartida para las públicas.
- El NAT Gateway puede ser **zonal**, donde elegimos en qué subnet pública vive, o **regional** (nuevo), que pertenece a la VPC y que AWS distribuye internamente entre AZs, de forma similar al Internet Gateway. Luego de crearlo, hay que agregar en las route tables privadas la ruta hacia el NAT Gateway; sin ella, la subred privada se comporta como aislada (por ejemplo, no podemos instalar paquetes en las instancias).
- Los **VPC endpoints** permiten conectarse de forma privada a servicios como S3, sin necesitar IPs públicas ni salida a internet.
- Conviene usar **tags** en los recursos (por ejemplo, `project: demo1`) para luego poder filtrarlos y borrarlos.
- El **key pair** son las claves que usamos para conectarnos por SSH a las instancias (se descarga un `.pem`).
- Por defecto, los security groups permiten toda la salida. En las reglas de entrada conviene limitar todo lo posible, idealmente a nuestra propia IP, porque lo que queda público eventualmente alguien lo encuentra.

Para conectarnos por SSH a instancias que están en subredes privadas, una opción clásica es un **bastión**, que es una instancia en una subred pública a la que nos conectamos para estar dentro de la red, y desde ella accedemos a los recursos internos. La ventaja frente a hacer públicos los recursos es que el bastión se puede limitar mucho, con distintos usuarios para saber quién se conectó y qué hizo, y controlando qué protocolos y recursos se pueden usar. Hoy en día AWS ofrece otros servicios para conectarse a las instancias, pero el bastión es la opción más básica. En nuestro caso, el bastión tiene una Elastic IP, su security group permite SSH de entrada solo desde nuestra IP y de salida solo hacia el security group de las web apps, y el security group de las web apps permite SSH de entrada desde el security group del bastión. Para conectarnos usamos SSH agent forwarding:
- `chmod 400 <key>.pem`, que restringe los permisos de la clave (si no, `ssh-add` se queja).
- `ssh-add <key>.pem`, que registra la clave en nuestro agente SSH local.
- `ssh-add -l`, que lista las claves registradas en el agente.
- `ssh -A ec2-user@<IP pública del bastión>`, que se conecta al bastión permitiendo que use nuestro agente local, por lo que desde ahí podemos hacer `ssh ec2-user@<IP privada de la instancia>`.

Para el load balancer, su security group permite HTTP de entrada y HTTP de salida hacia el security group de las web apps, y el de las web apps debe permitir HTTP de entrada desde el security group del load balancer. Si nos olvidamos de esta última regla, los health checks nunca pasan y las instancias aparecen como unhealthy. Una vez que las instancias están healthy, al acceder al DNS del load balancer vemos que las respuestas alternan entre las instancias. Si detenemos una, después de suficientes health checks fallidos el load balancer deja de enviarle tráfico.

>[!INFO]
>Una EC2 es como una computadora física. Si se reinicia, los procesos que levantamos a mano no vuelven a correr, por lo que conviene registrar los servicios (como Nginx) para que arranquen automáticamente al iniciar la máquina.
