Hostear en Cloud vs On Premise
- Marco regulatorio (data residency --> donde se deben guardar los datos por ley)
- Temas normativos que hacen a la seguridad física de los datos (cajas cofres por ejemplo)
- Costos, pero traen un tradeoff, porque bajan los costos operativos pero sube el costo total
- Latencia

Opciones para Hostear:
- Cloud
- On Premise - si pongo mis equipos en un datacenter es también on premise

Errores:
- Colas con Response Request. Es decir, en una operacion request response (en 5seg me tenes que decir si entro o fallo) que es sincronico, no podemos tener una cola en el medio, porque no tiene como volver la informacion del resultado de la operacion.
- Escalamiento horizontal sin load balancer
- Cachear datos que no deben ser cacheados
- Olvidarse entidades externas
- Tener en cuenta la transacccionalidad, cómo se guarda y donde
- Usar bases OLAP para transaccionar
- Managability tiene que ver con la salud del sistema, no un administrador del sistema que puede dar de baja usuarios

Para guardar logs: una variante de stack ELC ? No lo vimos

Si tenemos auditability, los logs se tiene que guardar en un lugar distinto al de la operatoria normal y con un control de accesos distintos. 

Ejercicio de Banco para Pymes tiene customizability. Hay que especificar cómo se va a mostrar y dónde se va a guardar. Hay que mantener separada la data transaccional de la de configuración.

Para mi: Ver despues limitaciones de todas las soluciones estudiadas, como por ejemplo websocket... cuánto tolera. Agregar VPN también.

Reliability vs Availability: el reliability requere que la availability se mantenga a lo largo del tiempo. Debemos considerar qué pasa con la operatoria a lo largo del tiempo. Recordemos que availability se mide estadísticamente, vimos que es mediante 9s. Reliability es más estricto, porque se habla de que algo funcionará de manera initerrumipdo garantizando 

Interoperability habla de como de manera transparente se opera con distintos sistemas. Si definimos qué hacemos cuando uno se cae, eso es funcionalidad del sistema. Fault tolerance habla de como sigo operando a pesar de que una parte del sistema esté caída. El ejemplo clásico es un sistema de millas. No voy a frenar una compra por esto, después veo cómo lo compenso.

Un **riesgo** es una situación posible, probable y mi sistema no lo resuelve. 

Caché -> qué guardo y cuándo se invalida.

En las operaciones para coordenadas, si aplico trigonometría aparece un montón de error. Puede haber punto flotante.

Conceptual Integrity --> No entra en el parcial

Los websockets funcionan de manera statefull, por lo que traen riesgos para availability y para fault tolerance, porque se puede morir la instancia que esta manejando la request y nadie toma esa conexion. --> Buen tradeoff para poner

Entonces, para transaccionalidad, usar request response (creo que entendi asi - 20:39hs)

Accessibility:
- Probar con distintos usuarios
- Internacionalización
- Diseños HCI
- Alt en imagénes para lectores de pantalla
- Lectores de pantalla