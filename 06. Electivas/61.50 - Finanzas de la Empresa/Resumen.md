## Valor Financiero

Podemos definir el **flujo** mediante la siguiente ecuación:
$$\text{Flujo}= +GON-\Delta BU-\Delta KT$$
Donde:
- $GON$: Ganancias Operativas Netas - Utilidades antes de restarles intereses pero después de descontarles los Impuestos a las Ganancias.
- $\Delta BU$: Cambios en el Nivel de los Bienes de Uso.
- $\Delta KT$: Cambios en el Nivel de Capital de Trabajo. Se refiere al dinero efectivo + cuentas por cobrar - cuentas por cobrar + inventarios. 

Las utilidades no son flujo porque contienen las amortizaciones.

El valor de un activo, empresa o inversión a partir de flujos de caja se calcula mediante el **Descuento de Flujos de Caja (DCF, Discounted Cash Flow)**. Este método estima el valor presente de los ingresos futuros esperados, ajustados por el valor del dinero en el tiempo. La fórmula es:
$$\text{Valor} = \sum_{t}^{\infty} \frac{\text{Flujos}_t}{(1+r)^t}$$
Si le llamamos $E$ al equity y $D$ a debt, el valor de mercado de la deuda, hacemos un promedio ponderado para calcular el **costo del dinero (Weighted Average Cost of Capital)**:
$$WACC=\frac{E}{E+D}\times Ke+\frac{D}{E+D}\times Kd\times(1-T)$$
Generalmente, el costo de la deuda ($Kd$) es menor que el costo del capital propio ($Ke$), dado que los acreedores asumen un riesgo menor que los accionistas. Además, la deuda genera un **escudo fiscal**, ya que los intereses son deducibles del Impuesto a las Ganancias ($1 - T$).

Si la empresa incluye además **acciones preferentes** ($P$), la fórmula general del WACC con sus tres componentes es:
$$WACC = W_d \cdot Kd(1 - T) + W_p \cdot Kp + W_e \cdot Ke$$
Donde:
- **$W_d, W_p, W_e$**: ponderaciones o pesos de cada fuente.
- $Kd(1 - T)$ (Deuda after-tax)
- $Kp$ (Acciones preferentes)
- $Ke$ (Acciones ordinarias / Equity)

Con esto, ahora podríamos pensar cuánto valor se gana en un período de tiempo. La métrica se conoce como **Economic Value Added (EVA)**. Se usa al principio del período para presupuestar o al final para controlar y comparar las espectativas. 
$$EVA= +UON-WACC\times TOC$$
Donde:
- $UON$: Utilidad Operativa Neta y se refiere a las utilidades antes de restarles intereses pero después de descontarles los impuestos a las ganancias. El costo de intereses se incluye en el WACC.
- $TOC$: Se refiere al capital operativo total, o sea al capital de trabajo operativo más los bienes de uso. En otras palabras, al (dinero en efectivo + cuentas por cobrar - cuentas por pagar + inventarios) + los bienes de uso.

El **ROE (Return on Equity o Rentabilidad del Patrimonio Neto)** mide la eficiencia con la que una empresa genera ganancias a partir del capital aportado por los accionistas.
$$ROE=\frac{\text{Utilidad Neta}}{\text{Patrimonio Neto}}$$
Se la puede descomponer en la ecuación de DuPont:
$$\begin{gathered} \left( \frac{\text{Utilidad neta}}{\text{Ventas}} \right) \times \left( \frac{\text{Ventas}}{\text{Activo}} \right) \times \left( \frac{\text{Activo}}{\text{Patrimonio Neto}} \right) \\[2ex]
\text{Margen} \times \text{Rotación} \times \text{Multiplicador} \end{gathered}$$
Donde:
- **Margen de Ganancia**: refleja la eficiencia operativa y la capacidad de la empresa para transformar ventas en ganancias finales. 
- **Rotación de Activos**: mide la eficiencia con la que la firma utiliza sus activos para generar ventas. 
- **Multiplicador del Capital**: representa el nivel de apalancamiento financiero; muestra cuánto del activo total está financiado por deuda vs. patrimonio propio.

---
## Análisis Financiero

Definiciones importantes dentro del balance:
- **Lease payments**: cuotas periódicas fijas que la empresa está obligada a pagar por el arrendamiento o alquiler operativo y financiero de activos.
- **Required sinking fund payments**: pagos o aportes obligatorios comprometidos contractualmente para amortizar o cancelar gradualmente una deuda financiera a su vencimiento.
- **Cash and equivalents**: Representa el dinero disponible en caja y bancos.
- **Accounts receivable**: Crédito por ventas.
- **Inventories**: Bienes de Cambio
- **Total current assets**: todos los activos líquidos o que se espera convertir en efectivo, vender o consumir en un plazo.
- **Accounts payable**: Son las deudas u obligaciones a corto plazo contraídas con proveedores.
- **Notes payable**: Son compromisos de deuda a corto plazo.
- **Accruals**: Son gastos ya devengados o incurridos por la operación que aún no han sido efectivamente pagados al cierre del período (como sueldos, cargas sociales o impuestos a pagar).
- **Total common equity**: Es el valor contable del patrimonio neto correspondiente a los accionistas ordinarios.

Definiciones importantes dentro del cuadro de resultados:
- **Less interest**: Es el monto total pagado en concepto de intereses y cargos financieros por la deuda contraída con acreedores.
- **Net Income before preferred dividends**: Es la ganancia neta total generada por la empresa después de pagar todos los costos, intereses e impuestos.
- **Common dividends**: Es la porción de la ganancia neta que se distribuye efectivamente en efectivo a los tenedores de acciones ordinarias.

Tenemos las siguientes métricas de desempeño operativo:
- **Net Operating Working Capital (NOWC / Capital de Trabajo Operativo Neto)**: Fondos netos inmovilizados en la operación a corto plazo, descontando el crédito espontáneo sin costo financiero que otorgan los proveedores.
$$\begin{gathered} \text{NOWC} = \text{Activos Corrientes Operativos} - \text{Pasivos Corrientes sin Interés} \\[2ex] \text{NOWC} = (\text{Caja} + \text{Créditos por Ventas} + \text{Bienes de Cambio}) - (\text{Proveedores} + \text{Deudas Comerciales}) \end{gathered}$$
- **Total Operating Capital (TOC / Capital Operativo Total)**: Total de fondos propios y de deuda inmovilizados en la operación completa del negocio.
$$\begin{gathered} \text{TOC} = \text{NOWC} + \text{Bienes de Uso (Activo Fijo Neto)} \\[2ex] \text{TOC} = \text{Deuda Bancaria (D)} + \text{Patrimonio Neto (E)} \end{gathered}$$
- **Net Operating Profit After Taxes (NOPAT / GON / UON - Utilidad Operativa Neta)**: Ganancia operativa generada exclusivamente por la actividad del negocio.
$$\text{NOPAT} = \text{EBIT} \times (1 - \text{Tasa Impositiva})$$
- **Net Cash Flow (NCF / Flujo de Caja Neto de las Utilidades)**: Flujo de fondos contable básico generado por las operaciones del ejercicio.
 $$\text{NCF} = \text{Utilidad Neta (Net Income)} + \text{Amortizaciones / Depreciación}$$
- **Operating Cash Flow (OCF / Flujo de Caja Operativo)**: Efectivo generado por la actividad operativa pura antes de financiar nuevas inversiones de capital.
$$\text{OCF} = \text{NOPAT} + \text{Amortizaciones / Depreciación}$$
- **Free Cash Flow (FCF / Flujo de Fondos Libre)**: Flujo de caja verdaderamente libre que queda disponible para remunerar a acreedores (bancos) y accionistas.
$$\text{FCF} = \text{NOPAT} - \Delta\text{TOC} = \text{GON} - \Delta\text{BU} - \Delta\text{KT}$$

Luego, podemos enumerar distintos ratios financieros.

**Liquidity Ratios (Ratios de Liquidez)**: Advierten sobre el estado de la caja y la solvencia inmediata de la empresa para saber si puede afrontar sus vencimientos a corto plazo:
- **Current Ratio (Liquidez Corriente o Razón Corriente)**: Mide la capacidad global de la empresa para cubrir sus deudas a corto plazo con la totalidad de sus activos corrientes.
 $$\begin{gathered} \text{Current Ratio} = \frac{\text{Activo Corriente}}{\text{Pasivo Corriente}} \\[2ex] \text{Current Ratio} = \frac{\text{Caja} + \text{Créditos por Ventas} + \text{Bienes de Cambio}}{\text{Deuda Bancaria Corto Plazo} + \text{Proveedores} + \text{Deudas Comerciales}} \end{gathered}$$
- **Quick Ratio (Prueba Ácida o Liquidez Ácida)**: Mide la solvencia más inmediata al excluir los inventarios (Bienes de Cambio) por ser el activo corriente menos líquido y más difícil de convertir rápidamente en efectivo.
 $$\begin{gathered} \text{Quick Ratio} = \frac{\text{Activo Corriente} - \text{Bienes de Cambio (Inventarios)}}{\text{Pasivo Corriente}} \\[2ex] \text{Quick Ratio} = \frac{\text{Caja} + \text{Créditos por Ventas}}{\text{Pasivo Corriente}} \end{gathered}$$

**Asset Management Ratios (Ratios de Operación / Gestión de Activos)**: Miden la eficiencia con la que la empresa gestiona sus recursos y activos en el día a día.
- **Inventory Turnover (Rotación de Inventario)**: Mide cuántas veces al año rota o se comercializa el inventario total.
$$\text{Inventory Turnover} = \frac{\text{Ventas}}{\text{Bienes de Cambio (Inventarios)}}$$
- **Days Sales of Inventory (DSI / Días de Inventario o Permanencia de Stock)**: Mide cuántos días promedio pasa la mercadería almacenada antes de venderse.
$$\text{DSI} = \frac{\text{Bienes de Cambio (Inventarios)}}{\text{Ventas}} \times 365 = \frac{365}{\text{Inventory Turnover}}$$
- **Days Sales Outstanding (DSO / Plazo Medio de Cobranza o Días de Cobro)**: Refleja el plazo promedio en días que demora la empresa en cobrar sus facturas vendidas a crédito.
$$\text{DSO} = \frac{\text{Créditos por Ventas (Cuentas por Cobrar)}}{\text{Ventas Anuales}} \times 365$$
- **Fixed Asset Turnover (Rotación de Bienes de Uso / Activo Fijo)**: Mide la eficiencia en la utilización de la infraestructura, maquinarias y bienes de uso para generar ventas.
$$\text{Fixed Asset Turnover} = \frac{\text{Ventas}}{\text{Bienes de Uso Netos (Activo Fijo)}}$$
- **Total Asset Turnover (TATO / Rotación del Activo Total)**: Indica el volumen de ventas generado por cada peso invertido en activos totales (componente central del modelo DuPont).
$$\text{Total Asset Turnover} = \frac{\text{Ventas}}{\text{Activo Total}}$$

**Debt Management Ratios (Ratios de Endeudamiento / Apalancamiento)**: Evalúan en qué medida la empresa utiliza el apalancamiento financiero para financiar sus operaciones, así como su solvencia y capacidad para cumplir con sus obligaciones a largo plazo:
- **Debt Ratio (Razón de Endeudamiento o Nivel de Deuda)**: Porcentaje del total de activos financiado a través de deuda con terceros.
$$\text{Debt Ratio} = \frac{\text{Pasivo Total (o Deuda Financiera Total)}}{\text{Activo Total}}$$
- **Times Interest Earned (TIE / Cobertura de Intereses)**: Capacidad de la ganancia operativa para hacer frente al pago periódico de intereses devengados por deudas bancarias y financieras.
$$\text{Times Interest Earned (TIE)} = \frac{\text{EBIT (Resultado Operativo)}}{\text{Intereses Pagados (Cargos Financieros)}}$$
- **EBITDA Coverage Ratio (Índice de Cobertura de Cargos Fijos / EBITDA)**: Cobertura integral del flujo operativo bruto antes de alquileres sobre la totalidad de los compromisos fijos obligatorios anuales.
$$\text{EBITDA Coverage Ratio} = \frac{\text{EBITDA} + \text{Alquileres}}{\text{Intereses} + \text{Alquileres} + \dfrac{\text{Devolución de Préstamos (Cuotas)} + \text{Dividendos Preferidos}}{1 - T}}$$

**Profitability Ratios (Ratios de Rentabilidad)**: Miden la capacidad global del negocio para generar utilidades y rendimientos netos a partir de sus ventas, de los activos invertidos y del capital aportado por los accionistas:
- **Profit Margin (Margen Neto o Margen de Utilidad)**: Porcentaje final de las ventas que se convierte en ganancia neta para los accionistas ordinarios tras cubrir costos, gastos, intereses e impuestos.
$$\text{Profit Margin} = \frac{\text{Utilidad Neta (Net Income)}}{\text{Ventas}}$$
- **Basic Earning Power (BEP / Capacidad Básica de Ganancia o Rentabilidad Operativa del Activo)**: Eficiencia operativa pura de los activos totales para generar ganancias antes del efecto de las deudas y los impuestos.
$$\text{Basic Earning Power (BEP)} = \frac{\text{EBIT (Resultado Operativo)}}{\text{Activo Total}}$$
- **Return on Assets (ROA / Rentabilidad sobre Activos Totales)**: Rendimiento neto generado sobre la totalidad de los recursos o activos de la firma.
$$\text{ROA} = \frac{\text{Utilidad Neta (Net Income)}}{\text{Activo Total}}$$
- **Return on Equity (ROE / Rentabilidad sobre el Patrimonio Neto)**: Rentabilidad neta generada sobre los fondos propios aportados por los accionistas comunes (capital social más utilidades acumuladas).
$$\text{ROE} = \frac{\text{Utilidad Neta (Net Income)}}{\text{Patrimonio Neto Total (Capital Social} + \text{Utilidades Acumuladas)}}$$
- **Return on Invested Capital (ROIC / Rentabilidad sobre el Capital Invertido)**: Rentabilidad operativa neta generada sobre la totalidad del capital operativo fondeado, independientemente de su estructura de financiamiento. Es la tasa que se compara contra el WACC para evaluar la creación de valor en el EVA ($ROIC > WACC$).
$$\text{ROIC} = \frac{\text{NOPAT (Utilidad Operativa Neta)}}{\text{Capital Operativo Total (TOC)}}$$

**Market Value Ratios (Ratios de Valor de Mercado)**: Relacionan el precio de las acciones de la empresa con sus métricas contables y financieras para evaluar cómo el mercado de capitales percibe el valor y las perspectivas futuras de la firma:
- **Price-to-Earnings Ratio (P/E o PER / Razón Precio-Ganancia)**: Múltiplo que indica cuántos pesos pagan los inversores por cada peso de beneficio neto generado.
$$\text{P/E Ratio} = \frac{\text{Precio de Mercado por Acción}}{\text{Beneficio por Acción (BPA / EPS)}} \quad \text{donde } \text{BPA} = \frac{\text{Utilidad Neta}}{\text{Cantidad de Acciones}}$$
- **Price-to-Cash Flow Ratio (P/CF / Razón Precio-Flujo de Caja)**: Relación entre la cotización de mercado de la acción y el flujo de fondos contable que genera por título.
$$\text{Price-to-Cash Flow} = \frac{\text{Precio de Mercado por Acción}}{\text{Flujo de Caja por Acción (NCF / Cantidad de Acciones)}}$$
- **Market-to-Book Ratio (M/B / Razón Mercado a Libros)**: Compara la valuación de mercado de la acción frente a su valor contable en libros. Muestra si el mercado confía en que la empresa generará valor sobre su capital contable.
$$\text{Market-to-Book Ratio (M/B)} = \frac{\text{Precio de Mercado por Acción}}{\text{Valor Libros por Acción (VPA / BVPS)}} \quad \text{donde } \text{VPA} = \frac{\text{Patrimonio Neto}}{\text{Cantidad de Acciones}}$$

---
## Acciones y Bonos

El **valor presente (VP)** es la suma de los flujos futuros descontados a una tasa que refleja el riesgo y el costo de oportunidad.
$$VP=\sum_{t=1}^n\frac{\text{Flujo}_t}{(1+r)^t}$$
El **valor** es el precio que un inversor perfectamente informado tendría que pagar en un mercado competitivo.

Las **acciones (comunes)** son instrumentos de renta variable, los emiten las empresas para financiar proyectos y los compran inversores para multiplicar sus ahorros. Su precio puede calcularse como el valor presente de los dividendos que se pronostica que se distribuirán. Los dividendos asumimos que se reciben por tiempo infinito, ya que la acción no tiene un plazo de vencimiento. Para calcular el valor de perpetuidades y acciones:
$$\sum_{t=1}^{\infty} \frac{D}{(1+r)^t} = \frac{D}{(1+r)^1} + \frac{D}{(1+r)^2} + \frac{D}{(1+r)^3} + \dots = \frac{D}{r}$$
En los casos donde los flujos futuros crecen de manera constante a una tasa $g$ (growth) en cada período:
$$\sum_{t=1}^{\infty} \frac{D_0 (1+g)^t}{(1+r)^t} = \frac{D_1}{(1+r)^1} + \frac{D_2}{(1+r)^2} + \frac{D_3}{(1+r)^3} + \dots = \frac{D_1}{r - g}$$

El **rendimiento total** de una acción se define como la rentabilidad obtenida durante un período determinado en relación con el precio pagado al inicio.
$$\text{Rentabilidad Acción} = \frac{(P_1 - P_0) + D_1}{P_0}$$
Podemos hacer la siguiente reestructuración de estas fórmulas:
$$r_s = \frac{D_1}{P_0} + g = \frac{(P_1 - P_0) + D_1}{P_0} = \frac{D_1}{P_0} + \frac{P_1 - P_0}{P_0}$$
- **Rendimiento por Dividendos (Dividend Yield)**: Es el primer término, $\frac{D_1}{P_0}$, y mide el ingreso en efectivo generado directamente por la distribución de ganancias en relación con el precio inicial de la acción.
- **Ganancias de Capital (Capital Gains)**: Es el segundo término, $\frac{P_1 - P_0}{P_0}$, y mide el cambio porcentual en el valor de cotización de la acción entre el precio final $P_1$ y el precio inicial $P_0$.

El **modelo de valuación de empresas** consiste en:
1. Determinar el valor de la firma:
$$\text{Valor de la Firma} = \sum_{t=1}^{n} \frac{\text{Flujo Operativo}_t}{(1 + \text{WACC})^t}$$
2. Calcular el valor del equity:
$$\text{Valor del Equity} = \text{Valor de la Firma} - \text{Valor de la Deuda}$$
3. Divvidir el valor total del equity entre la cantidad total de acciones comunes:
$$\text{Precio por Acción} = \frac{\text{Valor del Equity}}{\text{Número de Acciones Comunes}}$$

Los **bonos** son títulos de deuda emitidos por Estados o empresas para financiarse, con el compromiso de abonar intereses y devolver el capital en plazos fijados. La **amortización de capital** define el esquema mediante el cual un bono devuelve el monto principal invertido a lo largo de su vida útil.
$$P = \sum_{t=1}^{n} \frac{C_t}{(1 + r)^t}$$
Donde:
- $P$: precio o valor presente del bono en el momento actual.
- $C_t$: flujo de caja total generado en el período $t$, incluyendo pagos de cupones y amortizaciones de capital.
- $r$: tasa de descuento o rendimiento requerido por el mercado en función del riesgo del emisor.
- $n$: cantidad total de períodos comprendidos desde la fecha actual hasta el vencimiento final.

El **rendimiento de un bono** se mide mediante la **Tasa Interna de Retorno (TIR)**, conocida en el ámbito financiero internacional como Yield to Maturity (YTM). A diferencia de la valuación donde se busca determinar el valor del activo a partir de una tasa dada, en este caso el precio de mercado es un dato conocido y la TIR representa la verdadera incógnita a despejar. La fórmula matemática para calcular el rendimiento del bono es: $$P = \sum_{t=1}^{n} \frac{C_t}{(1 + \text{TIR})^t}$$
Los bonos pueden emitirse:
- **A la par** (Tasa Cupón = YTM → Precio = Valor Nominal): El bono paga exactamente el interés que el mercado exige.
- **Sobre la par** (Tasa Cupón > YTM → Precio > Valor Nominal): El cupón del bono es más tentador que el mercado, por lo que cotiza más caro.
- **Bajo la par** (Tasa Cupón < YTM → Precio < Valor Nominal): El cupón del bono se quedó corto frente al mercado, por lo que debe venderse más barato para ser atractivo.

La **duration** de un bono representa el promedio ponderado del tiempo que tarda un inversor en recuperar el dinero invertido, funcionando como un punto de equilibrio en el eje temporal donde se conceptualiza la concentración de todos los flujos de fondos futuros.

---
## Teoría de Cartera

La **esperanza matemática** ($\mu$ o $E[R]$) es el rendimiento esperado de una inversión (promedio ponderado por probabilidad):
$$\mu = \sum_{i=1}^n p_i \cdot R_i$$

El **riesgo de un activo individual** está representado por la dispersión o volatilidad de sus retornos alrededor de la media. Se mide cuantitativamente con la **varianza ($\sigma^2$)** y, fundamentalmente, con el **desvío estándar ($\sigma$)**, que expresa el riesgo en las mismas unidades porcentuales que el retorno:
$$\sigma^2 = \sum_{i=1}^n p_i \cdot (R_i - \mu)^2 \quad \Longrightarrow \quad \sigma = \sqrt{\sigma^2}$$

Si lo que se quiere es medir la relación entre los retornos de dos activos, es necesario trabajar con la **covarianza** y el coeficiente de correlación. 
- **Covarianza positiva**: si los dos activos están positivamente relacionados entre sí (tienden a moverse en la misma dirección).
- **Covarianza negativa**: si se encuentran negativamente relacionados entre sí (tienden a moverse en direcciones opuestas).

El **coeficiente de correlación** normaliza la covarianza dividiéndola por el producto de los desvíos estándar de ambos activos. Su fórmula es:
$$ \rho_{xy} = \frac{\operatorname{Cov}(R_x, R_y)}{\sigma_x \cdot \sigma_y} $$
* $\rho_{xy}$: coeficiente de correlación entre los retornos de los activos $x$ e $y$.
* $\operatorname{Cov}(R_x, R_y)$: covarianza entre los retornos del activo $x$ y el activo $y$.
* $\sigma_x, \sigma_y$: desviación estándar (volatilidad) de los retornos de los activos $x$ e $y$.

El **rendimiento esperado** del portfolio (forma general) es:
$$
\mu_p = W_1 \cdot \mu_1 + W_2 \cdot \mu_2
$$
La **fórmula general de la volatilidad** de un portfolio de 2 activos se simplifica mucho cuando uno de ellos es libre de riesgo ($σ_2 = 0$):
$$
\sigma_p = \sqrt{(W_1 \cdot \sigma_1)^2 + 2 \cdot W_1 \cdot \sigma_1 \cdot W_2 \cdot \sigma_2 \cdot \rho + (W_2 \cdot \sigma_2)^2}
$$

La pendiente $(\mu_1 - r_f) / \sigma_1$ es el "precio del riesgo", es decir, cuánto rendimiento adicional exige el mercado por cada unidad extra de desvío estándar. A esta recta se la llama **Línea del Mercado de Capitales (LMC)**, y describe el mejor rendimiento esperado alcanzable para cada nivel de riesgo, combinando el activo libre de riesgo con el portfolio riesgoso.

La **diversificación** consiste en tener muchos activos riesgosos en vez de concentrar toda la inversión en uno solamente. Debemos diferenciar:
- **Riesgo Diversificable**:
	- A medida que la correlación varía de uno a cero el porcentaje de riesgo no diversificable cae, y el número de activos necesario para diversificar se incrementa.
	- Sinónimos: riesgo individual, riesgo específico, riesgo irrelevante.
- **Riesgo No Diversificable**:
	- Existe un valor asintótico para el menor riesgo que el portfolio puede contener, y no se puede diversificar por debajo de ese valor.
	- Sinónimos: riesgo de mercado, riesgo relevante, riesgo sistemático.
	- Costo de reducirlo: se puede reducir el riesgo del portfolio diversificando las inversiones a muy bajo costo (de transacción), pero no eliminarlo del todo.

Un **portfolio eficiente** se define como aquel que ofrece al inversor la mayor tasa esperada de rendimiento a un nivel de riesgo específico. Los **portfolios subóptimos** son aquellos donde existe otra combinación con el mismo riesgo pero mayor rendimiento esperado. Ningún inversor racional los elegiría.

El **Capital Asset Pricing Model (CAPM)** es una teoría sobre los precios de equilibrio en los mercados para activos riesgosos. La medida de riesgo relevante ahora de un activo será su **Beta ($\beta$)** e indica cuánto tiene que cambiar el rendimiento esperado del activo ($R_i$) cuando cambia el rendimiento del mercado ($R_m$).
- $β = 1$: el activo se eleva y desciende a la misma velocidad que el mercado.
- $β ≥ 1$ - activo agresivo: el activo se eleva y desciende a mayor velocidad que el mercado.
- $β ≤ 1$ - activo defensivo: el activo se eleva y desciende a menor velocidad que el mercado.

En equilibrio, el premio por riesgo esperado de un activo $i$ es proporcional a su $\beta$:
$$ R_i - r_f = (R_m - r_f) \cdot \beta_i $$
Esta es la forma de "premio por riesgo". A esta ecuación se la conoce como **Línea del Mercado de Valores**. Podemos despejar y obtener el rendimiento esperado que exige el mercado a este activo:
$$ R_i = r_f + (R_m - r_f) \cdot \beta_i $$
Donde:
- $R_i$ (Rendimiento del Activo): Rendimiento esperado o exigido para el activo $i$ en función del riesgo sistemático asumido.
- $r_f$ (Tasa Libre de Riesgo): Rentabilidad de un activo libre de riesgo de impago (típicamente bonos del Tesoro de EE.UU.), que compensa el valor del dinero en el tiempo.
- $R_m$ (Riesgo de Mercado): Rendimiento esperado de la cartera de mercado en su conjunto. Representa el retorno global del mercado y determina, junto a $r_f$, la prima por riesgo ($R_m - r_f$).

---
## Planificación Financiera

El primer paso para armar un pronóstico de ventas consiste en estimar la **tasa de crecimiento histórico**. Existen métodos que van desde lo simple hasta lo complejo:
- Tasa de Crecimiento Anual Promedio (Average annual growth rate): Promedio aritmético de las tasas de variación anual (10,3%).
- Tasa de Crecimiento Anual Compuesto: Tasa geométrica de crecimiento acumulado (9,9%). En Excel se calcula con la función `=TASA()` (`RATE`).
- Regresión Lineal: para proyectar ventas futuras a partir de los datos históricos

El **método del porcentaje de ventas** asume que varias partidas de los estados financieros son directamente proporcionales a las ventas. También asume que la **depreciación** es proporcional a la planta y equipo neto. 
- **Costs / Sales:** Eficiencia operativa; indica qué porcentaje de cada peso vendido se consume en costos operativos antes de amortizaciones.
- **Depreciation / Net plant & equip.:** Tasa de desgaste contable del activo fijo; mide la velocidad con la que se amortiza la maquinaria e infraestructura instalada.
- **Cash / Sales:** Eficiencia de liquidez operativa; refleja la cantidad mínima de caja inmediata retenida por cada peso generado en ventas.
- **Accounts Rec. / Sales:** Política de crédito comercial; expone la porción de ventas que aún queda inmovilizada pendiente de cobro a clientes.
- **Inventory / Sales:** Eficiencia en gestión de inventario; señala el volumen de stock inmovilizado necesario para respaldar el nivel de actividad comercial.
- **Net plant & equip. / Sales:** Intensidad de capital; determina la cantidad de inversión en activos fijos requerida para sostener un peso de ventas.
- **Accounts Pay. / Sales:** Financiamiento espontáneo comercial; mide el apalancamiento operativo obtenido a través de los plazos otorgados por proveedores.
- **Accruals / Sales:** Financiamiento operativo devengado; representa pasivos espontáneos no facturados (como cargas laborales o impuestos) generados por la operatoria diaria.
- **Long-term bonds / Operating assets:** Estructura de financiamiento a largo plazo; define qué porcentaje de los activos productivos se cubre con deuda financiera estructurada.

El **Additional Funds Needed (AFN)** es el monto de financiamiento externo (vía nueva deuda o emisión de acciones) que la empresa debe salir a conseguir para financiar el aumento proyectado de sus activos, luego de descontar los pasivos operativos espontáneos y las ganancias retenidas que generará el propio negocio. Hay una forma no exacta de realizar el cálculo:
$$\text{AFN} = \Delta\text{Activos Requeridos} - \Delta\text{Pasivos Espontáneos} - \Delta\text{Utilidades Retenidas}$$
Desagregando cada componente según los ratios respecto a las ventas:
$$\text{AFN} = \left(\frac{A^*}{S_0}\right)\Delta S - \left(\frac{L^*}{S_0}\right)\Delta S - (M \cdot S_1 \cdot RR)$$
Donde:
- $A^*$: activos operativos que varían con ventas.
- $S_0$: ventas del año base.
- $\Delta S$: incremento en ventas ($S_1 - S_0$).
- $L^*$: pasivos corrientes espontáneos (proveedores y gastos devengados).
- $M$: margen neto ($\frac{\text{Utilidad Neta}}{\text{Ventas}}$).
- $RR$: tasa de retención ($1 - \text{Payout}$).

Con esto, podemos obtener también la **Tasa de Crecimiento Autosostenible** ($g$ para $\text{AFN} = 0$). Reordenando la ecuación:
$$g = \frac{M \cdot RR}{\left(\frac{A^*}{S_0} - \frac{L^*}{S_0}\right) - (M \cdot RR)}$$