## Valuación de Futuros

Comenzamos el repaso con el ejercicio 3, cuyo objetivo es determinar el precio de un futuro a partir de los flujos de efectivo de hoy y de dentro de un año. Las posiciones son las siguientes:
- Compramos un activo en $\$300$.
- Nos comprometemos a vender el activo a un precio $F_0$.
- Pagamos un costo de almacenaje de $\$6$ a período vencido.
- Tomamos un préstamo de $\$300$ para comprar el activo, a una tasa libre de riesgo de $8\%$ anual.

Comprar el activo es una **posición larga**, con la que ganamos si el activo sube. Hoy desembolsamos $\$300$ y dentro de un año tendremos el activo, cuyo valor desconocemos y llamamos $S_t$. Comprometernos a vender, ya sea con un futuro o con un forward, es una **posición corta**. Hoy no pagamos nada (deberíamos dejar alguna garantía, pero no la consideramos) y dentro de un año el flujo es $F_0 - S_t$, de modo que ganamos si $S_t$ es menor que $F_0$ y perdemos si es mayor.

Como no vendemos el activo ahora, debemos almacenarlo, y ese costo de $\$6$ se paga al final. Por último, para no invertir nada tomamos un préstamo por $\$300$, y dentro de un año devolvemos el capital más el $8\%$ de interés, es decir, $\$324$. Los flujos de cada operación son:

| **Operación** | **Hoy** | **1 año** |
| :---: | :---: | :---: |
| Comprar activo | $(300)$ | $S_t$ |
| Compromiso a vender | $-$ | $F_0 - S_t$ |
| Almacenaje | $-$ | $(6)$ |
| Tomo préstamo | $300$ | $(324)$ |
| **Total** | 0 | $F_0 - 6 - 324$ |

Si hoy no invertimos nada, en equilibrio tampoco deberíamos ganar nada, por lo que el flujo al final debe ser cero. El $S_t$ se cancela, así que el resultado no depende del valor futuro del activo y solo depende del precio del futuro:
$$0 = F_0 - 6 - 324 \implies F_0 = \$330$$
Este es el **precio de equilibrio** del futuro. Si $F_0$ fuera $\$340$, ganaríamos $\$10$ sin invertir nada. Sin embargo, esta oportunidad no duraría mucho tiempo, porque todos harían lo mismo. Todos comprarían el activo, por lo que su precio subiría y la devolución del préstamo sería mayor. A su vez, todos se comprometerían a vender para cobrar esos $\$340$, lo que haría bajar el precio del futuro. En definitiva, a través del mercado los precios se equilibrarían.

---
## Protective Put

El segundo tema son las opciones. En el ejercicio 1, la cotización de las acciones de Robito el 2 de enero de 2001 es de $\$1{,}675$. Un inversor posee 1.000 acciones y, ante la incertidumbre del mercado bursátil y con el fin de no correr riesgos, compra opciones de venta con vencimiento en junio, pagando una prima de $\$0{,}10$ por opción, con un precio de ejercicio de $\$1{,}70$ por acción. Resolvemos el ejercicio para una acción, y luego alcanza con multiplicar por 1.000.

Graficamos la ganancia y la pérdida de cada posición para distintos valores de la cotización. Con el activo tenemos una posición larga, por lo que ganamos si sube, y el resultado es la diferencia entre $S_t$ y $\$1{,}675$. Con el put, si el activo sube por encima de $\$1{,}70$ no ejercemos el derecho y perdemos la prima de $\$0{,}10$. Si el activo baja, lo ejercemos, y lo que ganamos es el precio de ejercicio menos el precio del activo menos la prima:
$$X - S_t - P_p = 1{,}7 - S_t - 0{,}1$$
El put queda hecho cuando el activo vale $\$1{,}60$. Para obtener la resultante, que se conoce como **Protective Put**, pensemos qué ocurre si el precio del activo es cero. Por el activo perdemos $\$1{,}675$ y por el put ganamos $\$1{,}60$, lo que da una pérdida de $\$0{,}075$. Esa pérdida se mantiene constante hasta $\$1{,}70$, y por encima de ese valor el activo sube mientras el put queda horizontal, de modo que empezamos a ganar cuando la cotización supera $\$1{,}775$:
```tikz
\begin{document}
\begin{tikzpicture}[x=9cm,y=9cm]
  % Ejes
  \draw[->] (1.15,0) -- (2.08,0) node[right] {$S_t$};
  \draw[->] (1.15,-0.56) -- (1.15,0.52) node[above] {G/P};

  % Activo
  \draw[black, thick] (1.15,-0.525) -- (2,0.325);
  \node[black, left] at (1.93,0.40) {Activo};
  \node[black, left] at (1.93,0.33) {$S_t-1{,}675$};

  % Put
  \draw[blue, thick] (1.15,0.45) -- (1.7,-0.1) -- (2,-0.1);
  \node[blue, right] at (1.24,0.44) {$X-S_t-P_p$};
  \node[blue, right] at (1.24,0.37) {$1{,}7-S_t-0{,}1$};
  \node[blue, below] at (1.92,-0.1) {$-0{,}1$};

  % Protective Put
  \draw[red, thick] (1.15,-0.075) -- (1.7,-0.075) -- (2,0.225);
  \node[red, right] at (2,0.225) {Protective Put};
  \node[red, left] at (1.15,-0.075) {$-0{,}075$};

  % Marcas en el eje de cotización
  \draw (1.2,-0.012) -- (1.2,0.012);
  \node[above] at (1.2,0.012) {$1{,}2$};
  \fill[blue] (1.6,0) circle (2pt);
  \node[below left] at (1.6,-0.003) {$1{,}6$};
  \draw (1.675,-0.012) -- (1.675,0.012);
  \node[above] at (1.66,0.05) {$1{,}675$};
  \draw[dashed] (1.7,0) -- (1.7,-0.1);
  \node[below] at (1.7,-0.105) {$1{,}7$};
  \fill[red] (1.775,0) circle (2pt);
  \node[below right] at (1.775,-0.005) {$1{,}775$};
\end{tikzpicture}
\end{document}
```

Con el gráfico contestamos las preguntas del ejercicio. Los resultados por acción de cada punto son los siguientes:

| **Punto** | **Decisión** | **Activo** | **Put** | **Resultado** |
| :---: | :---: | :---: | :---: | :---: |
| a) $S_t = 1{,}2$ | Ejerce put | $-0{,}475$ | $+0{,}4$ | $-0{,}075$ |
| b) $S_t = 1{,}2$ sin opciones | $-$ | $-0{,}475$ | $-$ | $-0{,}475$ |
| c) $S_t = 2$ | No ejerce | $0{,}325$ | $-0{,}1$ | $0{,}225$ |
| d) $S_t = 1{,}2$ | Vende opciones | $-0{,}475$ | $0{,}35$ | $-0{,}125$ |

- **Punto a**: si la cotización se sitúa en $\$1{,}20$, el inversor ejerce el put. Por el activo pierde $\$0{,}475$ y por el put gana $0{,}5 - 0{,}1 = 0{,}4$, con lo que el resultado es la pérdida de $\$0{,}075$ que habíamos anticipado.
- **Punto b**: si no hubiera comprado las opciones, la pérdida sería la del activo, $\$0{,}475$.
- **Punto c**: con una cotización de $\$2$ no ejerce. Gana $\$0{,}325$ por la acción y pierde la prima, por lo que la ganancia es de $\$0{,}225$. Sin el put hubiera ganado más, pero el put no se compra para eso, sino para evitar o morigerar la pérdida.
- **Punto d**: las opciones también se pueden vender en el mercado. Por el activo sigue perdiendo lo mismo, y por el put gana $\$0{,}35$, ya que la vende en $\$0{,}45$ y la había comprado en $\$0{,}10$. No le conviene venderla, le conviene esperar, porque la opción está barata. Debería valer por lo menos $\$0{,}50$, que es lo que podría obtener ejerciéndola en ese momento.

En cuanto a las ventajas y desventajas de la estrategia, limita la pérdida a cambio de resignar parte de la ganancia. Podemos preguntarnos además por qué no se compró un put con precio de ejercicio de $\$1{,}675$. Si baja el precio de ejercicio el call sube pero el put baja, por lo que ese put debería haber tenido una prima menor. Posiblemente no hubiera puts con ese precio de ejercicio en esa serie, o su prima no fuera menor a $\$0{,}075$, que es la pérdida máxima que ya se obtiene con el put de $\$1{,}70$.

---
## Opciones Reales

El siguiente tema son las **opciones reales**, donde aplicamos la valuación de opciones financieras para evaluar las opciones que tienen las empresas en sus proyectos, como ampliarse, abandonar el proyecto o cambiarlo. En una primera aproximación podemos resolver estos problemas con **árboles de decisión**, que es lo que vamos a hacer en los ejercicios. Las alternativas son la fórmula de Black y Scholes o el modelo binomial.

En el ejercicio 5, Magno Charter es una nueva compañía fundada para ofrecer un servicio de vuelo para ejecutivos. Los datos, con montos en miles de dólares, son:
- Hay una probabilidad de $40\%$ de que la demanda sea baja el primer año.
- Si la demanda inicial es baja, hay una probabilidad de $70\%$ de que siga siendo baja. Si es alta, hay una probabilidad de $80\%$ de que siga siendo alta.
- Un turbopropulsor nuevo cuesta $\$400$.
- Un avión de segunda mano con motor de combustión cuesta $\$200$, tiene menor capacidad y es menos atractivo para los clientes.
- El año próximo se podrá comprar otro avión de combustión por $\$100$, lo que da la idea de empezar con un avión chico y ampliarse si la demanda es alta.
- La TREMA es de $10\%$.

Estamos valuando un proyecto que tiene adentro una opción de ampliarse. Hoy debemos tomar una decisión, que se representa con un cuadrado, entre tres alternativas: comprar el turbopropulsor, comprar el avión de combustión o no hacer nada. Una vez comprado el avión empezamos a operar, y en el primer año pueden darse dos escenarios, que se representan con un círculo: demanda alta (DA) con probabilidad $0{,}6$ o demanda baja (DB) con probabilidad $0{,}4$. En el segundo año vuelve a haber dos posibilidades, con las probabilidades condicionales del enunciado. Con el avión de combustión, si en el primer año la demanda fue alta, aparece una nueva decisión, que es comprar o no un segundo avión por $\$100$. La rama descartada aparece punteada en el árbol:
```tikz
\begin{document}
\begin{tikzpicture}[dec/.style={draw, minimum size=0.9cm}, ev/.style={draw, circle, minimum size=0.9cm, inner sep=1pt}]
  % Encabezados
  \node at (0,9.6) {Hoy};
  \node at (4.2,9.6) {1 a\~no};
  \node at (8.5,9.6) {A\~no 2};

  % Nodos
  \node[dec] (R) at (0,1) {};
  \node[ev] (T) at (3,5.5) {};
  \node[ev] (C) at (3,-4) {};
  \node[ev] (T1) at (8.5,7.5) {810};
  \node[ev] (T2) at (8.5,3.5) {(200)};
  \node[dec] (D) at (5.8,-1.75) {};
  \node[ev] (C1) at (8.5,0) {660};
  \node[ev, gray] (C2) at (8.5,-3.5) {360};
  \node[ev] (C3) at (8.5,-7) {90};

  % Alternativas de hoy
  \draw (R) -- node[above, sloped] {Turbo $-400$} (T);
  \draw (R) -- node[above, sloped] {Comb. $-200$} (C);
  \draw (R) -- (0,-2) node[below] {NHN};

  % Primer año
  \draw (T) -- node[above, sloped] {DA 0,6 \ 200} (T1);
  \draw (T) -- node[below, sloped] {DB 0,4 \ 100} (T2);
  \draw (C) -- node[above, sloped] {DA 0,6 \ 100} (D);
  \draw (C) -- node[below, sloped] {DB 0,4 \ 0} (C3);

  % Decisión de ampliarse
  \draw (D) -- node[above, sloped] {2$^{\circ}$ Comb.} node[below, sloped] {$-100$} (C1);
  \draw[gray, dashed] (D) -- node[below, sloped] {No Comb.} (C2);

  % Segundo año, turbopropulsor
  \draw (T1) -- node[above, sloped] {DA 80\%} (11.5,8.5) node[right] {1.000};
  \draw (T1) -- node[below, sloped] {DB 20\%} (11.5,6.5) node[right] {50};
  \draw (T2) -- node[above, sloped] {DA 30\%} (11.5,4.5) node[right] {500};
  \draw (T2) -- node[below, sloped] {DB 70\%} (11.5,2.5) node[right] {(500)};

  % Segundo año, combustión
  \draw (C1) -- node[above, sloped] {DA 80\%} (11.5,1) node[right] {800};
  \draw (C1) -- node[below, sloped] {DB 20\%} (11.5,-1) node[right] {100};
  \draw[gray, dashed] (C2) -- node[above, sloped] {DA 80\%} (11.5,-2.5) node[right] {400};
  \draw[gray, dashed] (C2) -- node[below, sloped] {DB 20\%} (11.5,-4.5) node[right] {200};
  \draw (C3) -- node[above, sloped] {DA 30\%} (11.5,-6) node[right] {300};
  \draw (C3) -- node[below, sloped] {DB 70\%} (11.5,-8) node[right] {0};
\end{tikzpicture}
\end{document}
```

El árbol se resuelve hacia atrás (roll back), calculando primero el valor esperado de cada nodo del segundo año. Por ejemplo, para el turbopropulsor con demanda alta tenemos $0{,}8 \times 1.000 + 0{,}2 \times 50 = 810$. En la decisión de ampliarse, con una TREMA de $10\%$ conviene invertir $\$100$ para tener $\$660$ en lugar de $\$360$. Luego calculamos el VAN de cada avión:
$$\begin{gathered}
VAN_{TP} = -400 + 0{,}6\left(\frac{200}{1{,}1} + \frac{810}{1{,}1^2}\right) + 0{,}4\left(\frac{100}{1{,}1} - \frac{200}{1{,}1^2}\right) = 81 \\[2ex]
VAN_{CB} = -200 + 0{,}6\left(\frac{100-100}{1{,}1} + \frac{660}{1{,}1^2}\right) + 0{,}4\left(\frac{0}{1{,}1} + \frac{90}{1{,}1^2}\right) = 157
\end{gathered}$$
Por lo tanto, conviene comprar el avión de combustión con la opción de ampliarse. Para estimar cuánto vale esa opción, primero sacamos el VAN sin opción, que no incluye la ampliación:
$$VAN_{CB\ \text{sin opción}} = -200 + 0{,}6\left(\frac{100}{1{,}1} + \frac{360}{1{,}1^2}\right) + 0{,}4 \cdot \frac{90}{1{,}1^2} = 62{,}8$$
La opción le da mayor valor al proyecto. Sin embargo, para medir cuánto agrega no restamos $62{,}8$, sino $81$, porque si no tuviésemos la opción hubiéramos elegido el turbopropulsor, cuyo VAN es mayor. Entonces, la opción de ampliarse vale aproximadamente:
$$\text{Opción} = 157 - 81 = 76$$

>[!WARNING] Cuidado
>El enunciado indica el flujo del turbopropulsor con demanda baja en el primer año como ($100.000$), entre paréntesis, es decir, negativo. En clase se lo tomó como $+100$, y así están calculados los valores de arriba. Si fuera $-100$, resulta $VAN_{TP} = 8{,}3$, la mejor alternativa sin opción pasa a ser el avión de combustión con $62{,}8$ y la opción vale $94{,}2$. La decisión no cambia.

El punto B plantea una **opción de abandono**, que se asemeja a un put, es decir, a una opción de venta. La ampliación que vimos recién se asemeja en cambio a un call, porque debemos poner cierto valor para tener derecho a que los flujos de fondos cambien, mientras que ahora recibimos un cierto valor si ejercemos la opción. Si la demanda es baja en el primer año, agregamos al final de ese año la decisión de vender el avión, recibiendo $\$300$ por el turbopropulsor o $\$100$ por el de combustión. Con el turbopropulsor comparamos $\$300$ contra $-\$200$ dentro de un año, y conviene vender. Con el de combustión comparamos $\$100$ contra $\$90$ dentro de un año, y también conviene vender. En rojo aparecen las decisiones agregadas:
```tikz
\begin{document}
\begin{tikzpicture}[dec/.style={draw, minimum size=0.9cm}, ev/.style={draw, circle, minimum size=0.9cm, inner sep=1pt}]
  % Encabezados
  \node at (0,9.6) {Hoy};
  \node at (4.2,9.6) {1 a\~no};
  \node at (8.5,9.6) {A\~no 2};

  % Nodos
  \node[dec] (R) at (0,1) {};
  \node[ev] (T) at (3,5.5) {};
  \node[ev] (C) at (3,-4) {};
  \node[ev] (T1) at (8.5,7.5) {810};
  \node[dec, red] (A1) at (5.8,3.5) {};
  \node[ev, gray] (T2) at (8.5,3.5) {(200)};
  \node[dec] (D) at (5.8,-1.75) {};
  \node[ev] (C1) at (8.5,0) {660};
  \node[ev, gray] (C2) at (8.5,-3.5) {360};
  \node[dec, red] (A2) at (5.8,-7) {};
  \node[ev, gray] (C3) at (8.5,-7) {90};

  % Alternativas de hoy
  \draw (R) -- node[above, sloped] {Turbo $-400$} (T);
  \draw (R) -- node[above, sloped] {Comb. $-200$} (C);
  \draw (R) -- (0,-2) node[below] {NHN};

  % Primer año
  \draw (T) -- node[above, sloped] {DA 0,6 \ 200} (T1);
  \draw (T) -- node[below, sloped] {DB 0,4 \ 100} (A1);
  \draw (C) -- node[above, sloped] {DA 0,6 \ 100} (D);
  \draw (C) -- node[below, sloped] {DB 0,4 \ 0} (A2);

  % Decisión de vender
  \draw[red] (A1) -- (7.3,5.2) node[above] {Vender $+300$};
  \draw[red, dashed] (A1) -- node[below] {No Vender} (T2);
  \draw[red] (A2) -- (7.3,-5.3) node[above] {Vender $+100$};
  \draw[red, dashed] (A2) -- node[below] {No Vender} (C3);

  % Decisión de ampliarse
  \draw (D) -- node[above, sloped] {2$^{\circ}$ Comb.} node[below, sloped] {$-100$} (C1);
  \draw[gray, dashed] (D) -- node[below, sloped] {No Comb.} (C2);

  % Segundo año, turbopropulsor
  \draw (T1) -- node[above, sloped] {DA 80\%} (11.5,8.5) node[right] {1.000};
  \draw (T1) -- node[below, sloped] {DB 20\%} (11.5,6.5) node[right] {50};
  \draw[gray, dashed] (T2) -- node[above, sloped] {DA 30\%} (11.5,4.5) node[right] {500};
  \draw[gray, dashed] (T2) -- node[below, sloped] {DB 70\%} (11.5,2.5) node[right] {(500)};

  % Segundo año, combustión
  \draw (C1) -- node[above, sloped] {DA 80\%} (11.5,1) node[right] {800};
  \draw (C1) -- node[below, sloped] {DB 20\%} (11.5,-1) node[right] {100};
  \draw[gray, dashed] (C2) -- node[above, sloped] {DA 80\%} (11.5,-2.5) node[right] {400};
  \draw[gray, dashed] (C2) -- node[below, sloped] {DB 20\%} (11.5,-4.5) node[right] {200};
  \draw[gray, dashed] (C3) -- node[above, sloped] {DA 30\%} (11.5,-6) node[right] {300};
  \draw[gray, dashed] (C3) -- node[below, sloped] {DB 70\%} (11.5,-8) node[right] {0};
\end{tikzpicture}
\end{document}
```

Con esta decisión, los VAN de cada alternativa pasan a ser:
$$\begin{gathered}
VAN_{TP} = -400 + 0{,}6\left(\frac{200}{1{,}1} + \frac{810}{1{,}1^2}\right) + 0{,}4 \cdot \frac{100+300}{1{,}1} \\[2ex]
VAN_{CB} = -200 + 0{,}6\left(0 + \frac{660}{1{,}1^2}\right) + 0{,}4 \cdot \frac{100}{1{,}1}
\end{gathered}$$
Igual que antes, podemos evaluar la opción de venta. Esta agrega valor al proyecto, y su valor es la diferencia entre el nuevo VAN, que va a ser mayor que 157, y esos 157.

---
## Estructura de Capital

El ejercicio 7 trata sobre la estructura de capital de una empresa cuyo $EBIT$ actual es de 19.000, con una tasa de impuesto a las ganancias $\alpha$ de $30\%$, un costo de la deuda de $15\%$ y 20.000 acciones. Queremos llevar el endeudamiento a $40\%$. Como el enunciado no indica que cambie el activo, suponemos que tomamos deuda y recompramos acciones:

| | **Hoy** | **Propuesta** |
| :---: | :---: | :---: |
| Activo | 100.000 | 100.000 |
| Deuda | 20.000 | 40.000 |
| Patrimonio neto | 80.000 | 60.000 |

El precio por acción es el patrimonio neto dividido el número de acciones:
$$PPA = \frac{E}{\#} = \frac{80.000}{20.000} = \$4$$
El punto A pide la mayor tasa que estaríamos dispuestos a pagar por la nueva deuda para que, sin que todavía haya aumentado el $EBIT$, la **utilidad por acción (UPA)** no caiga. Calculamos la UPA actual armando el estado de resultados:

| **Concepto** | **Monto** |
| :---: | :---: |
| EBIT | 19.000 |
| Intereses ($15\%$ de 20.000) | (3.000) |
| Utilidad antes de impuestos | 16.000 |
| Impuesto a las ganancias ($30\%$) | (4.800) |
| Utilidad neta | 11.200 |

Entonces la UPA es $11.200 / 20.000 = \$0{,}56$ por acción, y queremos que no caiga. Para la nueva estructura el $EBIT$ sigue siendo 19.000, y debemos restarle los intereses actuales y los de la nueva deuda de 20.000, a una tasa $i_N$. El número de acciones también cambia, porque recompramos acciones por 20.000, que suponemos a $\$4$ cada una:
$$0{,}56 = \frac{(19.000 - 3.000 - i_N \times 20.000)(1-0{,}3)}{20.000 - \frac{20.000}{4}}$$
El denominador resulta 15.000, y despejando obtenemos la mejor tasa que podríamos negociar para que la UPA no caiga:
$$\frac{0{,}56 \times 15.000}{0{,}7} = 16.000 - i_N \times 20.000 \implies i_N = 20\%$$
El punto B pide graficar la curva UPA en función del $EBIT$ para ambas estructuras. Con una tasa de $20\%$, las dos rectas se cruzan en el $EBIT$ actual, donde la UPA es la misma. La curva de mayor pendiente es la de la estructura propuesta, porque con el **apalancamiento financiero** se puede ganar mucho más, pero también se puede perder más:
```tikz
\begin{document}
\begin{tikzpicture}[x=1.5cm,y=1cm]
  % Ejes
  \draw[->] (-0.3,0) -- (6.4,0) node[right] {EBIT};
  \draw[->] (0,-2) -- (0,5.8) node[above] {UPA};

  % Estructura actual
  \draw[red, thick] (0,-0.525) -- (6,4.725);
  \node[red, right] at (6,4.5) {Actual};

  % Estructura propuesta
  \draw[blue, thick] (0,-1.633) -- (6,5.367);
  \node[blue, right] at (6,5.367) {Propuesta};

  % Punto de cruce
  \fill (3.8,2.8) circle (2.5pt);
  \draw[dashed] (0,2.8) -- (3.8,2.8);
  \draw[dashed] (3.8,0) -- (3.8,2.8);
  \node[left] at (0,2.8) {$0{,}56$};
  \node[below] at (3.8,0) {19.000};
\end{tikzpicture}
\end{document}
```

En el punto C, creemos que el mercado percibirá a la empresa como más riesgosa y que el **PER** caerá un $20\%$ al tomar la deuda, y buscamos la tasa que necesitamos para que el precio de la acción no caiga. El PER es el precio por acción dividido la UPA, y hoy vale:
$$PER = \frac{PPA}{UPA} = \frac{4}{0{,}56} = 7{,}14 \text{ años}$$
Con la caída de $20\%$, el nuevo PER es $0{,}8 \times 7{,}14 = 5{,}71$. Para que el precio siga siendo $\$4$, la UPA debe ser $4 / 5{,}71 = 0{,}7$, y reemplazando ese valor en la ecuación anterior obtenemos la tasa de interés máxima:
$$\frac{0{,}7 \times 15.000}{0{,}7} = 16.000 - i_N \times 20.000 \implies i_N = 5\%$$
¿Será posible conseguir esa tasa? Podrían haber bajado las tasas del mercado, pero si no bajaron no sería coherente conseguirla, porque la empresa hoy se endeuda al $15\%$ y ahora va a estar más endeudada, por lo que será más riesgosa. En teoría, la tasa debería subir.

---
## Modigliani y Miller

El ejercicio 8 tiene que ver con las proposiciones de Modigliani y Miller. El punto A consiste en calcular el costo del capital propio a través de la fórmula del WACC, para Aguas Claras S.A., con un WACC de $18\%$, un costo de la deuda antes de impuestos de $10\%$, un impuesto de $30\%$ y $D/E = 2$. Nos concentramos en el punto B. El $EBIT$ proyectado de la empresa Z alcanza los 3 millones, el rendimiento exigido a las acciones de una empresa igual pero sin deuda es de $15\%$, y la empresa tiene una deuda financiera de 10 millones a una tasa de $10\%$. Trabajamos con **perpetuidades**, es decir, estos valores se repiten todos los años.

Modigliani y Miller plantearon sus proposiciones sin impuestos y con impuestos. Sin impuestos, decían lo siguiente:
- **Proposición I**: el valor de la empresa no endeudada es igual al valor de la empresa endeudada, $V_U = V_L$. El endeudamiento no agrega valor, solo reparte la pizza de otra forma. En la empresa no endeudada todo es patrimonio neto y en la endeudada hay patrimonio neto y deuda, pero el tamaño de la pizza es el mismo.
- **Proposición II**: el costo del capital propio aumenta si la empresa tiene deuda, según $K_e = K_u + (K_u - i)\frac{D}{E}$, donde $K_u$ es el costo del capital propio de una empresa sin deuda.

```tikz
\begin{document}
\begin{tikzpicture}
  % Empresa no endeudada
  \draw (0,0) circle (1.4);
  \node at (0,0) {E};
  \node at (0,-1.8) {$V_U$};

  % Empresa endeudada
  \draw (4,0) circle (1.4);
  \draw (4,1.4) -- (4,-1.4);
  \node at (3.4,0) {E};
  \node at (4.6,0) {D};
  \node at (4,-1.8) {$V_L$};
\end{tikzpicture}
\end{document}
```

El valor de la empresa por el método del WACC es:
$$V = \sum_{j=1}^{n} \frac{FCFF_j}{(1+WACC)^j}$$
En este caso no hay impuestos, no hay variación del capital de trabajo y no hay inversiones, porque es una perpetuidad, de modo que el flujo de caja libre es de 3 millones. Para la empresa no endeudada, el WACC es directamente $K_u = 15\%$. Como trabajamos con una perpetuidad, el valor es el flujo dividido la tasa:
$$V_U = \frac{FCFF}{K_u} = \frac{3}{0{,}15} = 20 \text{ millones} = V_L$$
Según Modigliani y Miller, $V_L$ también debe ser 20 millones, pero ahora formados por 10 millones de deuda y 10 millones de patrimonio neto, cuando antes todo era patrimonio neto. Con la segunda proposición calculamos el costo del capital propio y luego el WACC:
$$\begin{gathered}
K_e = 0{,}15 + (0{,}15 - 0{,}1)\frac{10}{10} = 20\% \\[2ex]
WACC = K_e \frac{E}{E+D} + i(1-\alpha)\frac{D}{E+D} = 0{,}2 \times 0{,}5 + 0{,}1 \times 0{,}5 = 15\%
\end{gathered}$$
Verificamos que este sea el valor que debe ser, ya que el valor de la empresa es 20 y el flujo es 3, por lo que $20 = 3/WACC$ implica un WACC de $15\%$.

También podríamos calcular el patrimonio neto con el método del flujo de fondos a los accionistas. Recordemos que había tres métodos de valuación por flujo de fondos, **WACC**, **FTE (Flow to Equity)** y **APV**. El APV no lo usamos acá porque no hay impuestos. Con el FTE, los flujos para los accionistas se traen a hoy con la tasa que piden los accionistas:
$$E = \sum_{j=1}^{n} \frac{FCFE_j}{(1+K_e)^j}$$
Para pasar del $FCFF$ al $FCFE$ le restamos los intereses después de impuestos y le sumamos la variación de deuda, $FCFE = FCFF - Int(1-\alpha) + \Delta D$. Acá no hay impuestos ni variaciones de deuda, pero sí hay intereses, de modo que al flujo de 3 millones le restamos el $10\%$ de la deuda. Por ser una perpetuidad dividimos directamente por $K_e$:
$$E = \frac{3 - 0{,}1 \times 10}{0{,}2} = \frac{2}{0{,}2} = 10 \text{ millones}$$
El punto C considera que se cumple el mundo de Modigliani y Miller con impuestos, con un impuesto a las ganancias de $40\%$. Las proposiciones cambian de la siguiente manera:
- **Proposición I**: la empresa endeudada vale más que la no endeudada, por el **escudo impositivo** que generan los intereses de la deuda, $V_L = V_U + \alpha D$.
- **Proposición II**: $K_e = K_u + (K_u - i)(1-\alpha)\frac{D}{E}$.

Ahora tenemos un socio que se lleva el $40\%$ de las ganancias, el Estado. Como seguimos en una perpetuidad, podemos trabajar con la misma ecuación. $K_u$ no cambia, pero el flujo que queda ya no es de 3 millones, sino de 3 millones menos lo que se lleva el Estado:
$$\begin{gathered}
V_U = \frac{3 - 0{,}4 \times 3}{0{,}15} = \frac{1{,}8}{0{,}15} = 12 \text{ millones} \\[2ex]
V_L = 12 + 0{,}4 \times 10 = 16 \text{ millones}
\end{gathered}$$
De esos 16 millones, 10 corresponden a la deuda y 6 al patrimonio neto. El patrimonio neto es menor que en la empresa sin deuda porque los accionistas fueron reemplazados en parte por la deuda, pero el valor total de la empresa es mayor, porque el Estado se lleva menos:
```tikz
\begin{document}
\begin{tikzpicture}
  % Empresa no endeudada
  \draw (0,0) circle (1.6);
  \draw (90:1.6) -- (0,0) -- (-54:1.6);
  \node at (198:0.8) {E};
  \node at (18:0.9) {Estado};
  \node at (0,-2) {U};

  % Empresa endeudada
  \begin{scope}[shift={(5,0)}]
    \draw (0,0) circle (1.6);
    \draw (90:1.6) -- (0,0) -- (18:1.6);
    \draw (0,0) -- (198:1.6);
    \node at (144:0.9) {E};
    \node at (-72:0.8) {D};
    \node at (54:1) {Estado};
    \node at (0,-2) {L};
  \end{scope}
\end{tikzpicture}
\end{document}
```

Con la segunda proposición obtenemos $K_e$ y con él el WACC:
$$\begin{gathered}
K_e = 0{,}15 + (0{,}15 - 0{,}1)(1 - 0{,}4)\frac{10}{6} = 20\% \\[2ex]
WACC = 20\% \cdot \frac{6}{10+6} + 10\% \, (1-0{,}4)\frac{10}{10+6} = 11{,}25\%
\end{gathered}$$
Para comprobar que el WACC es el que debe ser, calculamos el valor de la empresa endeudada con el flujo de caja libre, que ahora es 3 millones menos lo que se lleva el Estado:
$$V_L = \frac{3 - 0{,}4 \times 3}{0{,}1125} = 16 \text{ millones}$$

---
## Valuación por APV

En el ejercicio 11, un fondo de inversión quiere adquirir una empresa de la que conoce el cierre de 2007 y la proyección hasta 2011, y luego de ese año los resultados se mantienen indefinidamente. Los datos son:
- Plazo de cobranza de 3 meses.
- Inversiones anuales iguales a las amortizaciones, de $\$150$.
- Deuda contraída al final de 2007 por $\$1.000$, a una tasa efectiva mensual de $0{,}9\%$, pagadera en cuatro cuotas anuales y sin nuevo endeudamiento proyectado.
- Beta no apalancada de $1{,}5$ y beta apalancada de $2$.
- Tasa libre de riesgo de $5\%$, prima de mercado de $6\%$ y tasa de impuesto a las ganancias de $35\%$.

El método **APV** divide el valor de la empresa en dos partes. La primera toma el flujo de fondos libre y lo trae a hoy con el costo de capital de una empresa sin deuda, lo que da el valor de la empresa no endeudada. A eso le agrega el VAN de la deuda, que es la sumatoria de los ahorros impositivos traídos a hoy con la tasa de interés de la deuda, porque ese flujo de fondos tiene un riesgo similar al que el banco le pide a la empresa:
$$V = \sum_{j=1}^{n} \frac{FCFF_j}{(1+K_u)^j} + \underbrace{\sum_{j=1}^{n} \frac{\alpha I_j}{(1+i)^j}}_{VAN_{Deuda}}$$

El valor de la empresa no endeudada se divide a su vez en el período de proyección explícita, en este caso de 2008 a 2011, y un **valor terminal** que tiene en cuenta todo lo que viene después. El valor terminal se calcula con el flujo del último año proyectado por uno más una cierta tasa de crecimiento, dividido $K_u - g$, y como ese valor está ubicado en 2011, luego lo traemos a hoy con cuatro años:
$$V_U = \sum_{t=1}^{4} \frac{FCFF_t}{(1+K_u)^t} + \frac{\frac{FCFF_{2011}(1+g)}{K_u - g}}{(1+K_u)^4}$$
Lo primero es calcular el flujo de caja libre de esos cuatro años, ya que 2007 es tiempo pasado:
$$FCFF = EBIT(1-\alpha) + A - \Delta K_{Top} - Inversiones_{BU}$$
Las amortizaciones y las inversiones son de 150 y se cancelan. Para la variación del capital de trabajo operativo, recordemos que este es igual a los activos corrientes operativos menos los pasivos corrientes operativos o, simplificando, cierto nivel de disponibilidades mínimas más los créditos más los bienes de cambio menos las deudas comerciales:
$$K_{Top} = AC_{op} - PC_{op} = D_{mín} + C + BC - DC$$
De estos componentes el enunciado solo nos permite calcular los créditos. Como el plazo de cobranza es de 3 meses y en el año hay cuatro períodos de 3 meses, los créditos al final de cada año son las ventas divididas 4:

| **Año** | **2007** | **2008** | **2009** | **2010** | **2011** |
| :---: | :---: | :---: | :---: | :---: | :---: |
| Ventas | 1.000 | 1.000 | 1.200 | 1.300 | 1.300 |
| EBIT | 350 | 330 | 520 | 610 | 600 |
| Créditos | 250 | 250 | 300 | 325 | 325 |
| $\Delta K_{Top}$ | $-$ | 0 | 50 | 25 | 0 |

Con estos valores calculamos el flujo de cada año:
$$\begin{gathered}
FCFF_{2008} = 330(1-0{,}35) + 150 - 0 - 150 = 214{,}5 \\[2ex]
FCFF_{2009} = 520 \times 0{,}65 - 50 = 288 \\[2ex]
FCFF_{2010} = 610 \times 0{,}65 - 25 = 371{,}5 \\[2ex]
FCFF_{2011} = 600 \times 0{,}65 = 390
\end{gathered}$$

Para descontar estos flujos necesitamos $K_u$, que no nos dan, y lo calculamos con **CAPM** usando la beta no apalancada, porque estamos ante una empresa sin deuda. La prima de mercado de $6\%$ ya es la diferencia entre el rendimiento de mercado y la tasa libre de riesgo:
$$K_u = R_f + \beta_u(R_m - R_f) = 5\% + 1{,}5 \times 6\% = 14\%$$
Como los resultados se mantienen constantes, $g$ vale cero y el valor terminal en 2011 es:
$$VT = \frac{390(1+0)}{0{,}14 - 0} = 2.785{,}7$$
Pasemos a la deuda. Si bien el enunciado indica sistema francés, en clase se aclaró que los $\$1.000$ se devuelven por el **método alemán**, con lo que las amortizaciones son todas iguales, de $\$250$. La tasa efectiva anual se obtiene de la mensual:
$$TEA = 1{,}009^{12} - 1 = 11{,}35\%$$
Con esa tasa calculamos los intereses sobre el saldo de cada año, y con ellos el ahorro de impuesto a las ganancias, que es el $35\%$ de los intereses:

| | **2008** | **2009** | **2010** | **2011** |
| :---: | :---: | :---: | :---: | :---: |
| Amortización | 250 | 250 | 250 | 250 |
| Intereses | $113{,}5$ | $85{,}1$ | $56{,}75$ | $28{,}37$ |
| Ahorro de IG | $39{,}7$ | $29{,}8$ | $19{,}9$ | $9{,}9$ |

No hay valor terminal de la deuda, porque la deuda se cancela. Sumando todo, el valor de la empresa es:
$$V = \frac{214{,}5}{1{,}14} + \frac{288}{1{,}14^2} + \frac{371{,}5}{1{,}14^3} + \frac{390 + 2.785{,}7}{1{,}14^4} + \frac{39{,}7}{1{,}1135} + \frac{29{,}8}{1{,}1135^2} + \frac{19{,}9}{1{,}1135^3} + \frac{9{,}9}{1{,}1135^4} \approx 2.621$$
El punto B pregunta cuánto embolsarían los dueños actuales con la venta, que es el patrimonio neto. Para calcularlo restamos al valor la deuda de hoy, $E = V - D = 2.621 - 1.000 = \$1.621$.

El punto C pregunta cómo influyen las utilidades operativas en el cálculo con APV. Influyen a través del flujo de caja libre, mientras que no influyen en el VAN de la deuda, que depende solo de los intereses y de la tasa de impuestos.

Por último, notemos que el enunciado también da una beta apalancada, que seguramente no va a coincidir con la que surge de la **ecuación de Hamada**. Esta ecuación permite llegar a la beta de una empresa con deuda partiendo de la beta de una empresa sin deuda:
$$\beta_L = \beta_U + \beta_U(1-\alpha)\frac{D}{E}$$
