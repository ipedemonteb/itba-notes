## Unidad 1 - Introducción

La **inteligencia artificial** es entonces un sistema que sensa, procesa y actúa de manera que es adecuada en un contexto físico y temporal particular. Requiere una corporización para manifestarse con claridad y es un continuo, un ”moving goalpost”. Presenta Autonomía como un comportamiento emergente y manifiesta una conciencia, que se materializa como comportamientos que representan un conocimiento sobre su propia existencia, en relación al contexto físico y temporal, y una diferenciación en relación a los otros.

---
## Unidad 2 - Agentes y Ambientes

El **agente** es entonces todo aquello que puede considerarse que percibe y responde o actúa en un ambiente, de forma independiente (autónomo). Tenemos distintos tipos según su comportamiento y su conocimiento.
- Racional
- Omnisciente
- Con estado interno (basados en modelos) o sin (reactivos)

Un **ambiente** es un conjunto de componentes que conforman al entorno del problema. Pueden contener uno o más agentes. Aquí también podemos diferenciar distintos tipos según sus características.
- Totalmente vs Parcialmente Observable
- Determinístico vs Estocástico (vs Estratégico)
- Episódico vs Secuencial
- Estático vs Dinámico (vs Semidinámico)
- Discreto vs Continuo
- Conocido vs Desconocido
- Individual vs Multiagente
- Adversarial vs Colaborativo

---
## Unidad 3 - Métodos de Búsqueda

Antes de comenzar, debemos establecer las siguientes definiciones:
- **Estado**: Conjunto de valores del ambiente en un momento dado.
- **Acción**: Una función que toma un estado y retorna otro estado, si es aplicable.

Para definir correctamente un problema, se debe tener:
- **Estado Inicial**: Estado en el cual, generalmente, el problema no está resuelto.
- **Conjunto de Posibles Acciones**: Dado un estado particular $S$, retorna el conjunto de acciones que pueden ejecutarse en $S$.
- **Modelo de Transición**: Describe el efecto de aplicar $A$ (acción) a $S$ (estado).
- **Función de costo**: Determina el costo para el modelo de transición.
- **Condición de solución**: Función que nos indica si un estado $S$ es solución.

Tenemos distintas estrategias de búsqueda. Es **completa** si encuentra una solución (de existir y ser alcanzable), y es **óptima** si encuentra la solución alcanzable con menor costo. Un estado es **expandido** cuando dentro del método de búsqueda se le han aplicado todas las acciones aplicables, es decir que está explorado. Es importante no confundir nodo con estado. Un nodo contiene un estado. De esta forma, un estado puede estar representado en diferentes nodos.

Las **búsquedas desinformadas** no tienen más información de los estados que los que otorga la definición del problema. Sólo se distinguen estados "*goal*" de los que no lo son. Son poco eficientes en problemas donde podemos realizar estimaciones. Algunos algoritmos de este tipo de búsqueda son:
- BFS: expande los nodos de menor profundidad primero y encuentra la solución con menor profundidad.
- DFS: expande el nodo de mayor profundidad y suele ser de menor complejidad espacial.
- IDDFS: aplicación de DLS donde la profundidad varía según cierto criterio.
- Costo Uniforme: expande el nodo con menor costo acumulado.

Las **búsquedas informadas** tienen más información para comparar entre dos estados cuál es "mejor". Pueden estimar cuánto les falta para solucionar el problema, y la estimación a la solución desde un estado se llama **heurística**. La idea es pensar por qué no agarramos algo del problema sobre el que estamos trabajando y hacemos algún mecanismo para recorrer estados que no van a llegar a una solución.
. Algunos de ellos son:
- Greedy: Se comienza con el nodo raíz y se expande, y de los recién expandidos se calcula $h$. Luego, se toma el nodo con menor $h$ y se expande.
- A\*: Se basa en la función: $$f(n) = g(n) + h(n) \ | \ \text{costo} + \text{heurística}$$Ordena a los nodos en frontera según esta función. Si dos nodos tienen igual $f(n)$, se elige el nodo con menor $h(n)$.

Una heurística es **admisible** si nunca sobreestima el costo real ($h(a) ≤$ costo a la solución, para todo $a$). La heurística **perfecta** (que estima el costo real) se denomina heurística estrella : $h^*(n)$.

Definimos un algoritmo de búsqueda genérico de la siguiente forma. Dados un árbol de búsqueda $Tr$, un conjunto frontera $Fr$ y un conjunto de nodos explorados $Exp$, el procedimiento es:
1. Crear $Tr$, $Fr$ (y $Exp$) inicialmente vacíos.
2. Insertar nodo inicial $n_0$ en $Tr$ y $Fr$.
3. Mientras $Fr$ no esté vacía... (Paso 6 en caso de estar vacía)
	1. Extraer primer nodo de $Fr$ $\Rightarrow$ Nodo $n$
	2. Si es goal: Devolver la solución, formada por el arco entre la raíz $n_0$, y el nodo $n$ en $Tr$. Termina Algoritmo.
	3. Expandir el nodo $n$, generando los sucesores. Ingresar dichos sucesores en $Fr$ y colocarlos en $Tr$ como nodos sucesores de $n$. Agregar $n$ a $Exp$.
4. Reordenar $Fr$ según un criterio dado (depende del método de búsqueda).
5. Ir al Paso 3. Si $Fr$ está vacía en el Paso 3, no existe solución alcanzable.

>[!INFO] Cuándo Usarlos
>Los métodos de búsqueda son particularmente efectivos para resolver problemas que pueden modelarse mediante un conjunto de estados concretos y acciones que permiten transicionar entre ellos, donde el objetivo es encontrar una secuencia de pasos que lleve desde un estado inicial hasta una solución óptima. Estos métodos son fundamentales cuando se busca optimizar el costo de una solución, ya sea minimizando el uso de recursos, el tiempo de procesamiento o la cantidad de acciones necesarias.

---
## Unidad 4 - Algoritmos de Mejoramiento Iterativo

Un **algoritmo de mejoramiento iterativo** parte de una solución y busca (mediante perturbaciones a una solución inicial) una solución mejor en cada paso. El propio algoritmo es el encargado de ir mejorando la solución y lo hace en cada paso, no en cada corrida. 

**Hill Climbing** es un algoritmo de mejoramiento iterativo que mantiene una sola solución actual y la va mejorando con cambios pequeños. Se parte de una solución candidata $s$ y, en cada paso, se miran sus vecinos (soluciones obtenibles con un cambio pequeño) y se mueve al vecino que mejora el valor de una función de evaluación $f(s)$. 
- **Simple Hill Climbing**: Elige la primera solución de la frontera con mejor valuación que el estado actual.
- **Steepest Hill Climbing**: Siempre elige la solución de la frontera con mejor valuación que el estado actual.
-  **Stochastic Hill Climbing**: Elige al azar una solución de la frontera y, en base a que tan buena es, decide si moverse o elegir otra.

**Simulated Annealing** es una variante de Hill Climbing pensada para evitar quedar atrapado en máximos locales. La idea central es que, además de aceptar movimientos que mejoran $f(s)$, a veces también acepta movimientos que empeoran (bajar en el gráfico), pero lo hace de manera controlada: al principio es "más permisivo" y con el tiempo se vuelve "más estricto".

**Beam Search** es una estrategia de búsqueda que, en vez de seguir una sola solución como Hill Climbing, mantiene varios candidatos a la vez. En cada iteración, expande esos candidatos generando sucesores, evalúa qué tan buenos son con una función $f(s)$, y se queda solo con los $k$ mejores para continuar al siguiente paso. Ese $k$ es el beam width.  **Stochastic Beam Search** selecciona los $k$ con una probabilidad proporcional a su valoración $f(s)$.

>[!INFO] Cuándo Usarlos
>Conviene utilizar estos algoritmos en problemas donde el espacio de estados es excesivamente grande o incluso infinito, lo que hace que realizar un barrido completo del árbol de búsqueda sea computacionalmente inviable. Son especialmente efectivos cuando se opera bajo restricciones de memoria, ya que su consumo de recursos es muy bajo al no requerir el almacenamiento de rutas exploradas. Resultan apropiados para escenarios donde no interesa encontrar un camino específico hacia una meta, sino maximizar o minimizar una función de evaluación que determine qué tan buena es una configuración particular entre una gran cantidad de variables.

---
## Unidad 5 - Aprendizaje por Refuerzo

El **aprendizaje por refuerzo** es un tipo de aprendizaje automático donde el modelo aprende a partir de la interacción con un entorno: un agente toma acciones, el entorno cambia y el agente recibe una recompensa (o castigo). El objetivo es aprender una política de decisiones que maximice la recompensa total a largo plazo, como en juegos, robótica o control.

En cada instante $t$, el agente observa el estado $S_t$, que resume "cómo está" la situación actual (por ejemplo, la posición en un juego o las variables de un sistema). Con esa información, elige una acción $A_t$ y la ejecuta sobre el entorno. Luego, el entorno responde con dos cosas: un nuevo estado $S_{t+1}$, que refleja cómo cambió la situación, y una recompensa $R_{t+1}$, que es una señal numérica de qué tan buena fue esa acción en ese contexto. 

>[!WARNING] Cuidado
>La recompensa puede ser "engañosa" a corto plazo: a veces conviene aceptar una recompensa menor ahora para lograr una mayor después. Por eso el agente necesita explorar y aprender regularidades del entorno, estimando qué consecuencias tienen sus acciones a futuro, y no simplemente repetir lo que dio buen resultado una sola vez.

Un **Proceso de Decisión de Markov (MDP)** es el modelo matemático estándar para describir problemas de decisión secuenciales en aprendizaje por refuerzo. Se define como $(S,A,R,p,γ)$:
- $S$: conjunto finito de estados posibles del entorno.
- $A$ es el conjunto finito de acciones que el agente puede tomar.
- $R$: conjunto (finito) de recompensas posibles.
- $p$: es la probabilidad conjunta: $p(s',r|s,a)$. Significa: estando en $s$ y haciendo $a$, cuál es la probabilidad de terminar en el estado siguiente $s'$ y recibir recompensa $r$. 
- $γ∈[0,1]$: factor de descuento. Controla cuánto valen las recompensas futuras respecto de las inmediatas. 
	- $γ≈0$: agente cortoplacista.
	- $γ≈1$: agente previsor, planifica más a largo plazo.

>[!TIP] Propiedad de Markov
>Establece que para predecir lo que pasa después, solo importa el estado actual y la acción actual, no toda la historia previa.

El agente toma decisiones siguiendo una **política**, una regla que, dado el estado actual, asigna una probabilidad a cada acción posible. 
$$\pi : \mathcal{S} \times \mathcal{A} \rightarrow [0, 1] \qquad \sum_{a \in \mathcal{A}} \pi(a \mid s) = 1 \quad \forall s \in \mathcal{S}$$
La idea de la **Generalized Policy Iteration (GPI)** es que siempre se alterna entre dos procesos que se retroalimentan. En evaluación, se toma una política $π$ fija y se calcula qué tan buena es ($v_π$: valor por estado o $q_π$: valor por estado–acción). Luego viene la actualización: usando $v_π$ o $q_π$, se construye una política nueva $π'$ que sea mejor que la anterior, típicamente eligiendo en cada estado la acción que maximiza el valor esperado.

En **programación dinámica** aplicada a MDPs se parte de que la dinámica del entorno es completamente conocida. Eso significa que, para cualquier estado y acción, se conoce la distribución de probabilidad de los posibles estados siguientes y recompensas. Con ese modelo explícito, no hace falta aprender por prueba y error; se puede calcular de forma exacta qué conviene hacer mediante expectativas.

La idea de **Monte Carlo** en aprendizaje por refuerzo es aprender valores (típicamente $Q(s,a)$ o $V(s)$) mirando episodios completos: el agente ejecuta una política $π$, observa la secuencia de estados, acciones y recompensas, y con eso estima qué tan buena fue cada decisión en promedio. Como no se conoce el "valor esperado" teórico, se usa el retorno real como una muestra; repitiendo muchos episodios, el promedio de esos retornos converge al valor esperado gracias a la **ley de los grandes números**.

**Q-Learning** propone aprender valores de acción $Q(s,a)$ sin tener que esperar a que termine un episodio. La idea es que el agente, mientras interactúa, actualiza su estimación en cada paso usando la información disponible hasta ese momento. En lugar de calcular el retorno completo $G_t$ mirando todo el futuro (como en Monte Carlo), usa una aproximación "de un paso" que combina recompensa inmediata y una estimación del mejor futuro posible. Notemos que aprende con un objetivo que también está siendo aprendido, lo cual puede generar más varianza o inestabilidad si no se maneja bien. 

>[!INFO] Cuándo Usarlo
>El aprendizaje por refuerzo resulta fundamental en problemas de toma de decisiones secuenciales donde no se dispone de un conjunto de datos etiquetados con la respuesta correcta, sino que el sistema debe aprender a través de la interacción directa con un entorno. Su uso es especialmente efectivo cuando la señal de aprendizaje consiste en una recompensa o castigo que puede ser demorada, lo que obliga al agente a evaluar no solo el beneficio inmediato, sino el impacto acumulado de sus acciones a futuro para maximizar su rendimiento a largo plazo

---
## Unidad 6 - Algoritmos Genéticos

Un **algoritmo genético** se entiende como un método de optimización y adaptabilidad inspirado en la selección natural. En vez de construir un plan exacto para llegar a una meta, se trabaja con una función de aptitud que mide qué tan buena es cada solución, y se intenta mejorar esa aptitud a lo largo del tiempo. La mecánica se organiza en **generaciones**. Se parte de una población inicial de soluciones y luego se repite un ciclo.

La primera componente de estos algoritmos es el **genotipo**, que define cómo se codifican las soluciones. Está conformado por el *locus* (posición donde se guarda un gen/atributo),  el *cromosoma* (representación completa de una solución candidata), el *fenotipo* (solución interpretada en el dominio real) y los *alelos* (valores posibles que puede tomar un locus).

La **población inicial** es el punto de partida de un algoritmo genético: un conjunto de soluciones candidatas que el método va a ir mejorando generación tras generación. Esa población tiene un tamaño $N$. Un $N$ más grande suele dar más cobertura del espacio de búsqueda, pero también aumenta el costo computacional porque hay que evaluar más individuos.

La **función de fitness o aptitud** es una función de evaluación de los individuos. Representa que tan bien está un individuo en la evaluación del problema. Se define:
$$p(i) = \frac{f(i)}{\sum_{j=1}^{N} f(j)} \qquad f(i) : \text{Fitness}$$

La **selección** define quiénes pasan a reproducirse o a sobrevivir hacia la próxima generación. Busca favorecer a los individuos con mayor aptitud para que la población mejore, pero además mantener algo de diversidad. El **crossover (cruza)** es el operador que toma dos padres, los empareja y recombina sus genes para producir hijos. Los cruces de uno/dos puntos tienden a preservar bloques contiguos de genes (lo que a veces es bueno si esos bloques funcionan bien juntos). En el cruce uniforme, como cada gen se elige casi independientemente, se rompen esos bloques con facilidad; eso aumenta exploración y diversidad, pero también puede destruir combinaciones de genes que eran valiosas como conjunto.

Se define **mutación** como una variación en la información genética que se almacena en el cromosoma. Para que la mutación sea más eficiente, una correcta arquitectura y separación de genes es necesaria. La correcta configuración es esencial para evitar una convergencia prematura. Algunas de las causas son:
- Una presión de selección muy alta.
- Una probabilidad de mutación muy baja.
- Un tamaño de población muy escaso.

La **supervivencia** en algoritmos genéticos es el mecanismo que define qué individuos pasan a formar parte de la siguiente generación después de haber evaluado aptitudes y generado descendencia mediante cruza y mutación. La **brecha generacional** es un parámetro $G\in[0,1]$ que indica qué fracción de la población se renueva en cada generación.

Los **criterios de corte** son las reglas que determinan cuándo dejar de iterar en un algoritmo genético. Como estos métodos no garantizan encontrar el óptimo global, en la práctica se necesita una condición clara para frenar. Un **esquema** es una forma de describir un patrón parcial que comparten varios cromosomas: en vez de fijar todos los genes, se fijan solo algunas posiciones y se deja el resto como "comodines". El **orden de un esquema** mide cuánta información fija contiene ese patrón. Se define como la longitud del esquema menos la cantidad de comodines.

>[!INFO] Cuándo Usarlos
>Conviene usar algoritmos genéticos en problemas de optimización compleja con espacios de búsqueda masivos donde los métodos deterministas resultan ineficientes. Son ideales cuando existen múltiples óptimos locales, ya que el uso de una población y la mutación permiten explorar diversas regiones en paralelo y escapar de estancamientos. También son recomendables para problemas que requieren adaptabilidad ante cambios en el tiempo o que permiten paralelismo masivo al evaluar soluciones de forma independiente.

---
## Unidad 7 - Aprendizaje Automático

El **aprendizaje automático** se define bajo un enfoque libre de modelo como la capacidad de determinar el mapeo o la relación funcional entre un conjunto de entradas $X$ y sus respectivas salidas $Y$. El objetivo es que, mediante la observación de datos, el sistema logre configurar estos parámetros de manera que pueda predecir o clasificar correctamente nuevas entradas basándose en patrones identificados previamente. 

Este ajuste de parámetros se lleva a cabo a través de un **proceso de optimización**, el cual busca encontrar la configuración interna que minimice la diferencia entre la salida predicha y la salida real. El problemas básico de la optimización es encontrar la combinación de los parámetros para una función que hacen que esta sea lo más grande o más chica posible.

El **procedimiento general de optimización** es un proceso iterativo diseñado para aproximarse de manera sucesiva al valor mínimo de una función de costo. El algoritmo comienza en un punto inicial $x_k$ , que actúa como la posición actual en el espacio de búsqueda. A partir de este punto, el sistema debe determinar una dirección de movimiento $d_k$  que apunte hacia una zona de menor costo y calcular una longitud de paso $α_k$, la cual define qué tan grande será el desplazamiento en esa dirección. Esta elección es crítica, ya que una dirección incorrecta o un paso excesivamente largo pueden alejar al sistema del objetivo o causar inestabilidad en la convergencia. La actualización del sistema se realiza mediante la regla matemática $x_{k+1} = x_k + α_kd_k$, donde el nuevo punto se convierte en la base para la siguiente iteración. Este ciclo se repite hasta que el algoritmo alcanza un criterio de parada.

La **tasa de aprendizaje (o learning rate)** es un parámetro  que determina qué tan grande es el paso que damos en la dirección seleccionada hacia el mínimo.
- Si $\alpha_k$ es demasiado grande: El algoritmo da pasos gigantes. Esto puede provocar que "salte" por encima del mínimo, oscile de un lado a otro e incluso diverja.
- Si $\alpha_k$ es demasiado pequeño: El algoritmo avanza de forma extremadamente lenta   y requerirá una enorme cantidad de iteraciones y tiempo de cómputo.

El **método del gradiente descendiente** es una técnica de optimización de primer orden muy importante en el entrenamiento de modelos de inteligencia artificial. Su principio se basa en que el gradiente de una función, $\nabla f(x_k)$, señala la dirección de máximo crecimiento en un punto determinado. Por lo tanto, para minimizar una función de costo, el algoritmo debe moverse en el sentido opuesto al gradiente, lo que se define formalmente como la **dirección de búsqueda** $d_k =−\nabla f(x_k)$. Este desplazamiento asegura que, en cada iteración, el sistema baje por la pendiente más pronunciada hacia el valor mínimo.

El **método del gradiente descendiente con momentum** introduce un término regularizador que consiste en tomar la dirección de descenso como una combinación lineal entre el gradiente actual y las direcciones calculadas en pasos anteriores. Al incorporar esta "memoria" del movimiento, el sistema logra amortiguar los cambios bruscos de dirección y acelerar la convergencia en el sentido correcto.

Para transformar un problema de aprendizaje en una tarea de optimización técnica, es fundamental establecer una métrica que cuantifique la discrepancia entre las $p$ observaciones de entrenamiento y nuestra función aproximada $g(\cdot)$, definiendo así el error acumulado que el algoritmo deberá minimizar.

El **Gradiente Descendiente Estocástico** es un método orientado a funciones de error. En términos matemáticos, el estimador del gradiente es el promedio de los gradientes individuales de cada observación del conjunto de entrenamiento, lo cual representa la dirección ideal para reducir el error total. $\frac{1}{p} \sum_{\mu=1}^{p} \nabla_w E(\xi^\mu, \mathbf{w}^t)$ es un estimador de la esperanza del gradiente, dado un conjunto de entrenamiento. La diferencia con el método de gradiente descendiente es que en el Estocástico, solamente una parte de los datos se utiliza para calcular la dirección de descenso en cada paso.

---
## Unidad 8 - Redes Neuronales

Una **red neuronal** es un tipo de algoritmo de aprendizaje automático que está modelado según la estructura y función del cerebro humano. Consiste en una gran cantidad de nodos de procesamiento interconectados (neuronas) que trabajan juntos para procesar y analizar datos. Cada neurona recibe uno o más inputs, los procesa utilizando un conjunto de pesos aprendidos y produce y una salida que se transmite a otras neuronas en la red. 

El modelo del **perceptrón** se inspira en las neuronas del mundo real. ![[Pasted image 20260712185941.png|center|291]]La **función de activación** va a determinar si se dispara el estímulo o no, evaluando la suma ponderada de las entradas de la neurona y transformándola en una salida que indica el grado de activación.
$$\begin{aligned} O &= \theta\left(\sum_{i=1}^{n} x_i w_i - u\right) \\[2ex] \theta(x) &= \begin{cases} 1 & x \ge 0 \\ 0 & \text{en otro caso} \end{cases} \end{aligned}$$

El **hiperplano de separación** es una frontera geométrica fundamental en los modelos de clasificación, como el perceptrón, cuya función principal es dividir un conjunto de datos en dos clases distintas. El mecanismo de clasificación opera mediante la proyección de los datos sobre este hiperplano. Matemáticamente, el modelo calcula una combinación lineal de las entradas ($x$) multiplicadas por sus respectivos pesos sinápticos ($w$), sumando además un término de umbral o bias ($w_0$). Si el resultado de esta proyección es positivo, el dato se asigna a una clase; si la proyección es negativa, se asigna a la clase opuesta. 

El **Perceptrón Simple (Escalón)** sirve exclusivamente para resolver problemas de clasificación binaria que sean linealmente separables. Su función es encontrar un hiperplano que divida perfectamente dos clases de datos.

Lo que hicimos hasta ahora es **aprendizaje**. Refiere al proceso de entrenar un perceptrón sobre un conjunto de datos, con el objetivo de minimizar el error o la función de costo de la red sobre las entradas del conjunto de datos. La **generalización** refiere a la habilidad del perceptrón de desempeñarse correctamente sobre datos que no fueron alimentados durante el entrenamiento.

El **Perceptrón Simple Lineal** representa una evolución del modelo básico diseñada para problemas donde el objetivo no es separar categorías, sino realizar una regresión o ajuste de datos. En este esquema, ya no se busca una frontera que divida clases, sino encontrar los valores de los pesos ($w$) que definan un hiperplano capaz de ajustarse lo mejor posible a la distribución de los puntos en el espacio. La diferencia fundamental respecto al perceptrón tradicional radica en su función de activación, que en este caso es la función identidad. Esto implica que la salida de la neurona ya no es binaria (1 o -1), sino que puede tomar cualquier valor dentro de los números reales. $$
O(h) = \theta(h(x)) = \displaystyle\sum_{i=1}^{n} x_i \cdot w_i + w_0
$$
La diferencia fundamental respecto al perceptrón tradicional radica en su función de activación, que en este caso es la función identidad. Esto implica que la salida de la neurona ya no es binaria (1 o -1), sino que puede tomar cualquier valor dentro de los números reales. Para entrenar este modelo, se define una función de error cuadrático que mide la discrepancia entre la salida real y la esperada; el objetivo del aprendizaje es minimizar este error acumulado. Para lograr este ajuste, se aplica un procedimiento de optimización basado en el descenso del gradiente, donde los pesos se actualizan de manera iterativa. La regla de actualización calcula la variación de cada peso en función de la tasa de aprendizaje, la entrada recibida y el error detectado. $$\begin{gathered}E(O) = \frac{1}{2} \sum_{\mu=0}^{p-1} (\zeta^{\mu} - O^{\mu})^2 \\ \Delta w = -\eta \frac{\partial E}{\partial w} = \eta(\zeta^{\mu} - O^{\mu})\theta'(h)x^{\mu} \end{gathered}$$

El **Perceptrón Simple No Lineal** se utiliza en escenarios donde no es posible ajustar los datos mediante una línea recta, requiriendo en su lugar el uso de una función de naturaleza no lineal. La diferencia fundamental con respecto al modelo lineal radica en el cambio de la función de activación, sustituyendo la identidad por funciones de tipo *sigmoideo*, como la *tangente hiperbólica* (tanh) o la *función logística*. La regla de actualización de los pesos sinápticos se ajusta para incluir la derivada de la función de activación elegida. Esto permite que el entrenamiento siga siendo un proceso iterativo basado en el descenso del gradiente, con la ventaja de que el sistema puede emplear cualquier función de activación siempre y cuando sea derivable.
$$\begin{gathered}
O = \theta\left( \sum_{i=0}^{n} x_i \cdot w_i \right) \qquad \begin{array}{ll} \theta(x) = \tanh(\beta x) & Im = (-1, 1) \\ \theta(x) = \frac{1}{1+\exp^{-2\beta x}} & Im = (0, 1) \end{array} \\[2ex]
\Delta w = -\eta \frac{\partial E}{\partial w} = \eta \displaystyle\sum_{\mu=0}^{p-1} (\zeta^{\mu} - O^{\mu}) \theta'(h) x^{\mu}
\end{gathered}
$$

El **Perceptrón Multicapa (MLP)** representa la evolución del modelo conexionista hacia estructuras capaces de resolver problemas que no son linealmente separables. Su concepto fundamental se basa en la combinación de múltiples neuronas organizadas en capas, donde la suma de sus funciones individuales permite representar y aproximar comportamientos complejos que un perceptrón simple no podría abordar por sí solo. El **Teorema de Aproximación Universal** establece que una red neuronal con al menos una capa oculta, que contenga un número finito de neuronas y funciones de activación no lineales (como *sigmoide* o *ReLU*), puede aproximar cualquier función continua con alta precisión.

El procesamiento de la información ocurre mediante un mecanismo llamado **feed-forward pass**, en el cual los datos viajan desde la entrada a través de las capas intermedias hasta generar un resultado final. Para que la red aprenda, se requiere minimizar una función de error ajustando los pesos sinápticos en la dirección opuesta al gradiente. Es aquí donde toma relevancia el **backpropagation**,  un algoritmo que permite calcular de manera eficiente el gradiente del error respecto a cada peso de la red, incluso en las capas ocultas donde no se dispone de un valor esperado ($\zeta$) directo. Su fundamento es la regla de la cadena del cálculo diferencial: dado que el error de la red depende de la salida, que a su vez depende de las capas ocultas, que a su vez dependen de los pesos, es posible descomponer esa dependencia en un producto de derivadas parciales y así "repartir" el error hacia atrás, capa por capa.

Ahora, tenemos que ver de qué manera podemos medir el desempeño de nuestro modelo. La **Matriz de Confusión** es una tabla que permite evaluar el desempeño de un algoritmo de clasificación. 
![[Pasted image 20260712201424.png|center|329]]
Notemos que vamos a querer maximizar la diagonal de la figura anterior, porque son los casos donde se detectan correctamente los positivos y negativos verdaderos. Para evaluar la clasificación, existen una serie de métricas estándar que ya están definidas, como por ejemplo Accuracy ($\frac{\text{TP}+\text{TN}}{\text{TP}+\text{TN}+\text{FN}+\text{FP}}$) o Precision ($\frac{\text{TP}}{\text{TP}+\text{FP}}$).

El **underfitting** ocurre cuando un modelo es demasiado simple para capturar la estructura subyacente de los datos, como una línea recta intentando explicar un patrón que claramente es ondulado. En este estado, el modelo presenta un sesgo (bias) alto, lo que significa que ni siquiera logra aprender bien del dataset de entrenamiento y, por lo tanto, tendrá un desempeño pobre tanto en la práctica como con datos nuevos.

El **overfitting** es el problema opuesto, donde el modelo es tan complejo que, en lugar de aprender el patrón general, termina "memorizando" el ruido y las fluctuaciones aleatorias del dataset de entrenamiento. El gran riesgo aquí es que el modelo pierde su capacidad de generalización; cuando le presentes datos nuevos que no estaban en esa "foto" exacta, fallará estrepitosamente porque aprendió detalles irrelevantes en lugar de la tendencia real.
![[Pasted image 20260712202352.png|center|349]]
El overfitting puede deberse a diversos factores:
- Conjunto de datos de entrenamiento no balanceado.
- Pocos registros en el conjunto de entrenamiento.
- Conjunto de datos de entrenamiento con mucho ruido.

Como resumen, podemos tomar los siguientes casos:
![[Pasted image 20260712202621.png|center|308]]

Una de las cosas a realizar antes de entrenar, es un procesamiento de los datos donde se suele realizar una **normalización**. Una técnica es future scaling, que consiste en escalar la data en un intervalo $[a;b]$. Otra opción es **estandarizar**, que consiste en tomar las variables del conjunto $P=\{X_1,…, X_p\}$ y calcular los siguientes estadísticos unidimensionales. Cada $X_i$ tiene $n$ registros.

|                              MEDIA                               |                         DESVÍO ESTÁNDAR                         |                VARIABLE ESTANDARIZADA                |
| :--------------------------------------------------------------: | :-------------------------------------------------------------: | :--------------------------------------------------: |
| $\overline{X}_i = \frac{1}{n} \displaystyle\sum_{j=1}^{n} X_i^j$ | $s_i^2 = \frac{1}{n} \displaystyle\sum_{j=1}^{n} (X_i^j - X_i)$ | $\widetilde{X}_i = \frac{X_i - \overline{X}_i}{s_i}$ |

Sirve por ejemplo cuando se tienen unidades o magnitudes diferentes en distintas variables. 

La **regularización** es un conjunto de técnicas diseñadas para reducir el error de test (o validación). La **Brecha de Generalización** es la distancia vertical entre ambas curvas. Si la brecha es pequeña, indica que el modelo se comportará de forma similar con datos nuevos que con los de entrenamiento. Si la brecha es grande, es el síntoma claro de Overfitting. El **Punto Óptimo de Capacidad** es el momento exacto en el que el modelo ha dejado de ser demasiado simple (bajo sesgo), pero aún no ha empezado a volverse "paranoico" con el ruido de los datos (baja varianza).

**Data Augmentation** es un conjunto de técnicas utilizadas para incrementar artificialmente el tamaño y la diversidad de un conjunto de datos de entrenamiento sin necesidad de recolectar datos nuevos reales. **L2 Penalty Norm / Weight Decay** es otra técnica de regularización fundamental que consiste en modificar la función de costo original ($E$) agregándole un término que "castiga" a los pesos grandes.

---
## Unidad 9 - Aprendizaje No Supervisado

En el **aprendizaje no supervisado**, la variable de respuesta no es información disponible. Puede resolver problemas menos definidos mediante Clustering, Asociación y Reducción de Dimensionalidad. Para saber si los resultados que obtenemos son significativos, se construyen modelos de predicción, que constan de estrategias para obtener características o patrones y sacar conclusiones.

El **clustering** consiste en agrupar observaciones de forma tal que el grado de similitud entre miembros de un mismo grupo sea lo más fuerte posible. Implica identificar similitudes entre los datos y asignarlos a un grupo (cluster). La **asociación** consiste en encontrar relaciones entre los atributos del conjunto de datos. Utiliza memorias asociativas, que consisten en el almacenamiento y recuperación de información por asociación con otros datos. Un ejemplo es el Modelo de Hopfield. La **reducción de la dimensionalidad** proyecta el conjunto de datos en un espacio menor, dejando de lado las características menos relevantes.

La **Red de Kohonen** es una red de una sola capa, en forma de grilla bidimensional ($k\times k$) y en la que cada neurona está conectada a todas las componentes de un vector de entrada n-dimensional.
![[Pasted image 20260712213255.png|center|292]]

Las neuronas están conectadas con sí mismas positivamente y también con las neuronas vecinas, donde el vecindario es de radio $R$. A lo largo del tiempo (épocas), algunas unidades toman un nivel de activación mayor mientras que el nivel de las demás se anula. Entonces, las neuronas compiten unas con otras. Dada la unidad de entrada $x$, la neurona que tenga vector de pesos $w$ "más parecido" a $x$ será ganadora. El objetivo es que finalmente sólo una de las de salida se active. Las demás son forzadas a valores de respuesta mínimos. Esto permite agrupar los datos que se introducen en la red. Los datos similares son clasificadas formando parte de la misma categoría o grupo y deben activar la misma neurona de salida.

Si las variables de un conjunto de datos están muy correlacionadas entonces posee información redundante. El objetivo del método de **Principal Component Analysis (PCA)** es eliminar la redundancia. La idea es transformar el conjunto de variables original en otro conjunto. Tendrá variables que son combinaciones lineales de las anteriores pero no están correlacionadas entre sí. Entonces, dadas $p$ variables originales, se desean encontrar $q<p$ variables que sean combinaciones lineales de las $p$ originales, recogiendo la mayor parte de la información o variabilidad de los datos.  Para evitar el problema se deben **estandarizar** las variables cuando calculamos las componentes principales. De esta manera las magnitudes de los valores numéricos de las variables originales serán comparables.

Oja demostró que si se toma un perceptrón simple y se ignora el valor esperado $\zeta^{\mu}$, el vector de pesos resultante $w^{\text{final}}$ serı́a un punto sobre la dirección de máxima variación de los datos (la primer componente principal). Pero el problema es que no converge porque el $\Delta w$ va aumentando en cada paso y se hace tan grande que produce que el algoritmo sea inestable. Para solucionarlo, propuso normalizar los pesos ($\vert{}\vert{}w\vert{}\vert{}=1$) en cada paso. Al aproximar matemáticamente esta normalización usando un desarrollo de Taylor para ahorrar cálculo, llegó a su famosa regla:$$\Delta w_i = \eta (O x_i - O^2 w_i)$$El término negativo ($-O^2 w_i$) actúa como un "freno" que evita que los pesos exploten. Gracias a esto, el algoritmo se estabiliza y los pesos terminan convergiendo al autovector con mayor autovalor, que es justamente la dirección de la primera componente principal.

La **Regla de Sanger** es una extensión de la regla de Oja. Mientras que esta última permite extraer únicamente la primera componente principal, la regla de Sanger utiliza un mecanismo de ortogonalización que permite a una red de múltiples neuronas extraer de forma ordenada las primeras $k$ componentes principales (PCA) de los datos. 

El **Modelo de Hopfield** es un modelo que almacena información en la red y la asocia con patrones que tiene almacenados. Entonces, consiste en almacenar un conjunto de $p$ patrones tal que cuando se presenta un nuevo patrón $P_{in}$, la red responda con el patrón almacenado $P_{out}$ que más se parece a $P_{in}$. Es una red recurrente, ya que existe retroalimentación entre las neuronas, están todas conectadas entre sí (a diferencia de las redes feed-forward). No se conectan consigo mismas. Son binarias, y el conjunto de input y output permitido es {-1, 1} (activo o inactivo). Todas las neuronas están en una sola capa de entrada y salida.  

Como ya vimos, cada neurona tiene 2 estados, activo ($S_i=+1$) o inactivo ($S_i=-1$). Para una red de $N$ neuronas el estado queda representado por el vector de estados $S = [S_1, S_2, … ,S_N]$. Esto es lo que vamos a actualizar con Hopfield, y es una diferencia clave con lo que veníamos estudiando, ya que ahora $W$ se mantendrá fijo. Dados los patrones almacenados $\xi^\mu$, $\mu = 1, \dots, p$, presentamos un nuevo patrón $\zeta$. Como dijimos, queremos encontrar el patrón almacenado más cercano a $\zeta$ (usando redes neuronales). Para esto, primero buscamos los pesos sinápticos $w_{ij}$, $i = 1, \dots, N$, $j = 1, \dots, N$. Vamos a tener un peso para cada neurona, es decir que $w_{ij}$ va a ser el peso que va de la neurona $i$ a la $j$. Entonces, $w_{ji}$ va a ser igual a $w_{ij}$, porque la red es simétrica, y $w_{ii}$ va a ser cero por lo que vimos antes. Entonces, el **Modelo de Hopfield** es una red neuronal que cumple las siguientes características:
* Cada neurona $i$ es un perceptrón simple con la función de activación escalón $(1, -1)$.
* Cada par de neuronas $(i, j)$ se conectan por el peso sináptico $w_{ij}$.

Las limitaciones de Hopfield  son:
- El número máximo de patrones que puede almacenar es igual al $15\%$ del número de neuronas de la red. Es decir, $p≤0.15∗N$, donde $N$ es la dimensión de los patrones.
- Los patrones deben ser "más o menos" ortogonales.
- La Función de Energía $H$ puede tener otros mínimos locales que no son los patrones almacenados, llamados estados espurios. También son atractores, por lo que puede desembocar en ciclos.

---
## Unidad 10 - Deep Learning

**Deep Learning** es un desarrollo de ciencias de la computación, pero a la vez muy interdisciplinario, con bases biomiméticas que utiliza una estructura jerárquica aglomerativa. En concreto es una tecnología revolucionaria que hoy está en el núcleo y centro de la frontera digital y que se caracteriza por haber logrado avance en áreas como Computer Vision, Natural Language Processing (NLP) y Speech Recognition. El área actual de Deep Learning está caracterizada por cuatro pilares:
- Deep, Profundidad: Múltiples Niveles de Composición.
- Feature Learning: Aprendizaje de la Representación.
- Datasets masivos y estandarizados.
- GPUs, Graphic Processing Units, hardware especializado para el procesamiento paralelo de multiplicación de matrices.

