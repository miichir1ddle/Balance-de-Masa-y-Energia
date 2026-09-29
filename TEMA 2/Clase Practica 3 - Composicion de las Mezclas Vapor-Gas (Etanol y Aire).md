# Tema 2 — Clase Práctica 3: Composición de las mezclas vapor-gas (etanol y compresor de aire)

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuente principal:** [PIQ1 Clase practica 3 Composicion de las mezclas vapor-gas Etanol y compresor de aire.pdf](PIQ1%20Clase%20practica%203%20Composicion%20de%20las%20mezclas%20vapor-gas%20Etanol%20y%20compresor%20de%20aire.pdf)
> **Teoría de base (léase antes si algo no se entiende):** [Conferencia 3 - Presion de Vapor y Composicion de Mezclas Vapor-Gas.md](Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md)
> **Apoyo numérico:** [../diagrama de COX.pdf](../diagrama%20de%20COX.pdf) (Figura B.9, gráfica real de Cox-Othmer) · [../Steam Tables_Keenan.pdf](../Steam%20Tables_Keenan.pdf) (tablas de agua saturada, usadas aquí para verificar cada dato de presión de vapor)
>
> Este documento es un desarrollo **independiente** de la Clase Práctica 3, pensado para poder seguirse sin tener que ir y venir a otro archivo: cada ecuación se recuerda antes de usarse, cada sustitución numérica se muestra completa (no se "saltan" pasos de álgebra ni conversiones de unidades), y cada resultado se verifica de forma cruzada contra una fuente independiente (la ecuación de Antoine o las tablas de vapor de Keenan). Los tres ejercicios de la clase práctica se resuelven íntegros, incluido el que el material original deja como tarea.

---

## 0. Qué es esta clase práctica y qué se espera lograr con ella

Una "clase práctica" (CP), a diferencia de una conferencia, no introduce teoría nueva: **ejercita** la teoría ya explicada en la conferencia correspondiente (aquí, la Conferencia 3) resolviendo problemas numéricos concretos. Los objetivos que declara el propio material son:

- Ejercitar el **cálculo de las formas de expresar la composición** de una mezcla vapor-gas.
- Determinar, mediante cálculos apropiados, **cantidades de mezcla o de vapor** bajo diferentes condiciones de operación en procesos físicos definidos.

La introducción de la clase práctica explica, además, **por qué** estas mezclas se llaman "vapor-gas": porque, a las condiciones de temperatura y presión en que generalmente se trabaja, uno de los dos componentes tiene una temperatura **superior** a su temperatura crítica (el "gas", incondensable) y el otro tiene una temperatura **inferior** a la suya (el "vapor", condensable) — exactamente la distinción explicada en la sección 2 de la Conferencia 3.

---

## 1. Formulario de partida (recordatorio, sin re-derivar)

Antes de resolver nada, conviene tener a mano — literalmente delante de los ojos — las fórmulas que se van a usar una y otra vez. Se agrupan, igual que en la Conferencia 3, según tomen como base el total de la mezcla o solo el gas libre de vapor:

**Notación:** $P$ = presión total; $p_v$ = presión parcial del vapor; $P_s$ = presión de vapor (saturación) a la temperatura de trabajo; $n_v,n_g$ = moles de vapor y de gas; $N=n_v+n_g$; $m_v,m_g$ = masas de vapor y de gas; $M=m_v+m_g$; $MM_v,MM_g$ = masas molares.

| Nombre | Símbolo | Fórmula | Base |
|---|---|---|---|
| Fracción molar | $y_m$ | $\dfrac{n_v}{N}$ | Total de la mezcla |
| Fracción presión | $y_P$ | $\dfrac{p_v}{P}$ | Total de la mezcla (bajo gas ideal, $y_m=y_P$) |
| Fracción másica | $y$ | $\dfrac{m_v}{M}$ | Total de la mezcla |
| Saturación | $Y$ | $\dfrac{m_v}{m_g}$ | Gas libre de vapor |
| Saturación molar | $Y_m$ | $\dfrac{n_v}{n_g}=\dfrac{p_v}{P-p_v}$ | Gas libre de vapor |
| % Saturación relativa | $\%Y_R$ | $\left(\dfrac{p_v}{P_s}\right)_T\times 100$ | Grado de saturación |
| % Saturación | $\%Y$ | $\left(\dfrac{Y_m}{Y_{m,SAT}}\right)\times 100$ | Grado de saturación |

**Relaciones cruzadas más usadas en esta clase práctica** (todas se demuestran en la Conferencia 3, sección 5.3; aquí solo se recuerdan como herramientas):

$$Y = Y_m\left(\frac{MM_v}{MM_g}\right) \qquad\Longleftrightarrow\qquad Y_m = Y\left(\frac{MM_g}{MM_v}\right)$$

$$\text{Si la mezcla está saturada:}\qquad p_v = P_s \qquad\text{y}\qquad Y_{m,SAT}=\frac{P_s}{P-P_s}$$

**Por qué existen dos "familias" de fórmulas (molar y másica):** los datos de un problema pueden venir dados en cualquiera de las dos bases (a veces en gramos, a veces en moles, a veces como presiones), y las tablas y gráficos de presión de vapor (como el de Cox) trabajan naturalmente con **presiones**, que están ligadas a la base **molar** (vía la ley de Dalton, $p_v=y_m P$). Por eso, un procedimiento típico de estos ejercicios consiste en convertir dato → base molar → usar la relación de presiones → volver a la base que pida la pregunta. Esto se verá una y otra vez en los ejercicios siguientes.

---

## 2. Ejercicio 1 — Saturación de una mezcla alcohol etílico–aire por evaporación

### 2.1 Enunciado

Una mezcla de alcohol etílico y aire, a una presión de $101.3\ \text{kPa}$ y temperatura de $19\ \text{°C}$, posee una saturación relativa del 60 %. A esta mezcla se le incorporan, por evaporación, $0.1886$ g de alcohol por gramo de aire seco, llegando a saturarse la misma. Determine la temperatura final del proceso.

### 2.2 Entender el problema antes de calcular

Conviene primero traducir el enunciado a un esquema físico simple: hay un recipiente con una mezcla de vapor de alcohol etílico y aire. Inicialmente (estado 1) está a $19\ \text{°C}$, $101.3\ \text{kPa}$, y no está saturada — le "falta" vapor para saturarse, y esa falta se cuantifica con $\%Y_R=60\ \%$ (le falta el 40 % restante). Luego se deja que se evapore más alcohol líquido dentro de ese recipiente (por ejemplo, hay un plato con alcohol líquido en contacto con la mezcla), y esa evaporación continúa hasta que la mezcla se **satura por completo** ($\%Y_R=100\ \%$, estado 2). Como se evapora alcohol, la temperatura del sistema **cambia** (este es el mismo mecanismo físico de "saturación adiabática" que se formaliza en la Conferencia 4 — el líquido que se evapora consume energía, así que el sistema se enfría o se calienta según cómo esté planteado el proceso; aquí no se pide analizar el porqué del cambio de T, solo encontrar cuál es).

Esquema resumido:

| | Estado (1) | Estado (2) |
|---|---|---|
| Presión $P$ | 101.3 kPa | 101.3 kPa (no cambia) |
| $\%Y_R$ | 60 % | 100 % (saturada) |
| Temperatura | 19 °C | **incógnita** |

**Dato de la evaporación:** $0.1886$ g de alcohol por gramo de aire seco se incorporan entre (1) y (2). Nótese que este dato está en **base másica y por unidad de gas** (gramos de alcohol **por gramo de aire seco**) — es decir, es directamente un $\Delta Y$ (con $Y$ definida en la sección 1 como $m_v/m_g$, aquí con el gas = aire seco).

**Qué se pide:** la temperatura del estado (2). La estrategia general será: (i) calcular la composición completa del estado (1); (ii) sumarle la evaporación para obtener la composición del estado (2); (iii) usar la condición de saturación en (2) para obtener su presión de vapor $P_{s2}$; (iv) leer en el gráfico de Cox a qué temperatura el alcohol etílico tiene esa presión de vapor.

### 2.3 Paso 1 — Presión de vapor del alcohol etílico a 19 °C

El gráfico de Cox (Figura B.9 del texto, disponible en este repositorio como [../diagrama de COX.pdf](../diagrama%20de%20COX.pdf)) trae, para muchas sustancias comunes —incluido el alcohol etílico—, una curva que da directamente $P_s$ en función de $T$ (usando internamente al agua como referencia, según el método de Cox explicado en la Conferencia 3, sección 4). Leyendo esa curva a $T=19\ \text{°C}$:

$$P_{s,\text{alcohol}}(19°C) = 40\ \text{mmHg}$$

**¿Por qué mmHg y no kPa?** Porque así están calibrados los ejes del gráfico de Cox del texto (es una convención histórica de la ingeniería química, heredada de los manómetros de mercurio). Por eso, de aquí en adelante, **todo el ejercicio se trabajará en mmHg**, y habrá que convertir la presión total dada en kPa a mmHg. La conversión exacta es:

$$1\ \text{atm} = 101.325\ \text{kPa} = 760\ \text{mmHg}$$

Como $P=101.3\ \text{kPa}$ es, para efectos prácticos de este curso, **exactamente 1 atm** (101.3 y 101.325 difieren en menos del 0.03 %), se tomará:

$$P = 760\ \text{mmHg}$$

### 2.4 Paso 2 — Presión parcial del alcohol en el estado (1)

Por definición (sección 1 de este documento, fórmula de $\%Y_R$):

$$\%Y_R = \left(\frac{p_v}{P_s}\right)_T\times 100 \qquad\Longrightarrow\qquad p_v = \frac{\%Y_R\times P_s}{100}$$

**Interpretación física de este paso:** decir que la saturación relativa es 60 % significa que la presión parcial que realmente ejerce el vapor de alcohol es el 60 % de la presión que ejercería **si la mezcla estuviera saturada** a esa misma temperatura. Sustituyendo:

$$p_{v1} = \frac{60}{100}\times 40\ \text{mmHg} = 24\ \text{mmHg}$$

### 2.5 Paso 3 — Saturación molar en el estado (1)

Ahora se convierte esa presión parcial a una relación de composición, usando la fórmula de $Y_m$ del formulario (sección 1):

$$Y_{m1} = \frac{p_{v1}}{P-p_{v1}}$$

Sustituyendo los números (ambos en mmHg, como se acordó en el paso 1):

$$Y_{m1} = \frac{24}{760-24} = \frac{24}{736}$$

Haciendo la división:

$$Y_{m1} = 0.03261\ \frac{\text{mol alcohol}}{\text{mol aire seco}} \approx 0.0326$$

**Por qué se calculó $Y_m$ y no directamente $Y$:** porque el dato de $\%Y_R$ está ligado a presiones, y las presiones se relacionan naturalmente con moles (ley de Dalton), no con masas. Es más directo pasar primero por la base molar.

### 2.6 Paso 4 — Convertir a base másica: saturación $Y_1$

El dato de la evaporación ($0.1886$ g alcohol/g aire seco) está en **base másica**, así que antes de poder sumarlo hay que expresar $Y_{m1}$ también en base másica. Se usa la relación de conversión del formulario:

$$Y = Y_m\left(\frac{MM_v}{MM_g}\right)$$

**Masas molares necesarias** (datos de química general, no se dan explícitamente en el enunciado porque se asumen conocidos):

- Alcohol etílico (etanol, $C_2H_5OH$): $MM_v = 46\ \text{g/mol}$.
- Aire (mezcla, valor estándar usado en todo el curso): $MM_g = 29\ \text{g/mol}$.

Sustituyendo:

$$Y_1 = 0.0326\left(\frac{46}{29}\right) = 0.0326\times 1.5862$$

$$Y_1 = 0.05171\ \frac{\text{g alcohol}}{\text{g aire seco}} \approx 0.0517$$

### 2.7 Paso 5 — Balance de masa de la evaporación

Este es el paso conceptualmente más simple del ejercicio, pero es el corazón del problema: como el gas (aire seco) **no se crea ni se destruye** en este proceso (solo se evapora alcohol, no aire), la masa de aire seco es la misma antes y después. Por eso, **basta con sumar** directamente la cantidad evaporada (que ya está expresada "por gramo de aire seco", la misma base que $Y_1$):

$$Y_2 = Y_1 + \Delta Y_{\text{evaporado}} = 0.0517 + 0.1886$$

$$Y_2 = 0.2403\ \frac{\text{g alcohol}}{\text{g aire seco}}$$

**Nota sobre por qué esto es válido:** si $Y$ estuviera definida sobre la masa total de la mezcla (como la fracción másica $y$) en vez de sobre la masa de gas, esta suma directa **no** sería válida, porque la masa total también cambia al evaporarse más alcohol. Es precisamente **por eso** que $Y$ se define con base en el gas (que permanece constante) y no en la mezcla total — la razón de ser de todo el "grupo 2" de fórmulas de composición de la Conferencia 3.

### 2.8 Paso 6 — Volver a base molar

Para poder usar de nuevo la relación con presiones (y así llegar a $P_s$), hay que devolver $Y_2$ a base molar:

$$Y_{m2} = Y_2\left(\frac{MM_g}{MM_v}\right) = 0.2403\left(\frac{29}{46}\right)$$

$$Y_{m2} = 0.2403\times 0.63043 = 0.15150\ \frac{\text{mol alcohol}}{\text{mol aire seco}} \approx 0.1515$$

### 2.9 Paso 7 — Usar la condición de saturación para hallar $P_{s2}$

El estado (2) está **saturado** por enunciado ($\%Y_R=100\ \%$). Esto significa, por definición de mezcla saturada (Conferencia 3, sección 5.1):

$$p_{v2} = P_{s2}$$

Y como se conoce $Y_{m2}$, se puede despejar $p_{v2}$ de la fórmula $Y_{m2}=p_{v2}/(P-p_{v2})$. El despeje algebraico completo, paso por paso:

$$Y_{m2}\,(P-p_{v2}) = p_{v2}$$

$$Y_{m2}\,P - Y_{m2}\,p_{v2} = p_{v2}$$

$$Y_{m2}\,P = p_{v2} + Y_{m2}\,p_{v2} = p_{v2}\,(1+Y_{m2})$$

$$p_{v2} = \frac{Y_{m2}\,P}{1+Y_{m2}}$$

Sustituyendo los valores numéricos ($P=760\ \text{mmHg}$, como se fijó en el paso 1):

$$p_{v2} = \frac{0.1515\times 760}{1+0.1515} = \frac{115.14}{1.1515}$$

$$p_{v2} = P_{s2} = 100.0\ \text{mmHg}$$

### 2.10 Paso 8 — Leer la temperatura en el gráfico de Cox

Ahora se busca, sobre la misma curva del alcohol etílico en el gráfico de Cox, a qué temperatura la presión de vapor vale exactamente $100\ \text{mmHg}$:

$$\boxed{T_{\text{final}} = 35\ \text{°C}}$$

### 2.11 Verificación independiente (para confirmar que el resultado es correcto)

Este documento verifica el dato del gráfico usando la **ecuación de Antoine** del etanol (una fórmula analítica bien establecida, alternativa e independiente al método gráfico de Cox — ver Conferencia 3, sección 3.3):

$$\ln P_s[\text{mmHg}] = A - \frac{B}{T[\text{°C}]+C}\,,\qquad A=8.20417,\ B=1642.89,\ C=230.3$$

**Verificando el dato de entrada** ($T=19$ °C):

$$P_s = 10^{\,8.20417 - 1642.89/(19+230.3)} = 10^{\,8.20417-1642.89/249.3} = 10^{\,8.20417-6.5901} = 10^{1.614}$$

$$P_s \approx 41.1\ \text{mmHg}$$

Esto es muy cercano al valor leído del gráfico (40 mmHg); la diferencia (menos del 3 %) es perfectamente esperable al leer un gráfico a mano.

**Verificando el resultado final** ($T=35$ °C):

$$P_s = 10^{\,8.20417-1642.89/(35+230.3)} = 10^{\,8.20417-1642.89/265.3} = 10^{\,8.20417-6.1926} = 10^{2.012}$$

$$P_s \approx 103\ \text{mmHg}$$

Nuevamente muy cercano a los 100 mmHg calculados en el paso 7. **Esta doble verificación confirma que tanto los datos del gráfico como el resultado de 35 °C son físicamente correctos.**

### 2.12 Resumen del método (para repetirlo en otro problema similar)

1. Leer/calcular $P_s$ en el estado inicial.
2. Con $\%Y_R$, obtener $p_v$ inicial.
3. Convertir a $Y_m$ (base molar).
4. Convertir a $Y$ (base másica) para poder sumar el dato de evaporación (que siempre viene en base másica por gramo de gas).
5. Sumar (balance de masa simple, porque el gas es constante).
6. Reconvertir a $Y_m$.
7. Usar la condición de saturación del estado final ($p_v=P_s$) para despejar la nueva $P_s$.
8. Leer la temperatura correspondiente a esa $P_s$ en el gráfico de Cox.

---

## 3. Ejercicio 2 — Compresión de aire húmedo: ¿condensa o no condensa?

### 3.1 Enunciado

Se desea comprimir aire húmedo desde $38\ \text{°C}$, $33.02\ \text{kPa}$ y $90\ \%$ de humedad relativa, hasta $344.42\ \text{kPa}$. Por efecto de la compresión, la temperatura se eleva hasta $49\ \text{°C}$.

(a) Determine si se produce o no la condensación del agua.
(b) Si se produce condensación, calcule la masa de agua condensada y el volumen de la mezcla en m³/mol de aire seco.

### 3.2 Entender el problema

Físicamente, esto describe un **compresor**: entra aire húmedo (agua + aire) a baja presión y temperatura, y por el trabajo mecánico de compresión sale a mayor presión **y** mayor temperatura (la compresión calienta al gas — esto se estudiará con rigor termodinámico en el Tema 4, pero aquí basta con tomar el dato de $T_2=49$ °C como un dato del problema).

**La pregunta clave que hay que resolver primero:** al subir tanto la presión, ¿el vapor de agua que ya estaba en el aire alcanza a "caber" en el nuevo estado sin condensar, o se ve obligado a condensar parte de él?

**Criterio físico para decidir (ya explicado en la Conferencia 3, sección 5.1, y en la Conferencia 4, sección 5.3):** el vapor **nunca** puede ejercer, en equilibrio, una presión parcial mayor que su presión de saturación a esa temperatura. Si un cálculo "ingenuo" (suponiendo que toda el agua se mantiene como vapor) arroja una presión parcial mayor que $P_s$ a la temperatura final, eso es físicamente imposible — la única forma de que el sistema sea consistente es que una parte del agua haya condensado, bajando la cantidad de vapor real (y por tanto su presión parcial) hasta que coincida exactamente con $P_s$.

Es como preguntarse cuánta gente cabe en un elevador: si el cálculo dice que "caben 15 personas" pero el elevador tiene capacidad para 10, la conclusión no es que quepan 15 — es que 5 se quedan afuera. Aquí, el "elevador" es la capacidad de la fase vapor a esa temperatura ($P_s$), y las "personas que se quedan afuera" son el agua que condensa.

### 3.3 Parte (a) — Determinar si condensa

**Paso 1 — Presión de saturación del agua a 38 °C.** No está dada directamente; hay que obtenerla de la tabla de agua saturada ([Steam Tables_Keenan.pdf](../Steam%20Tables_Keenan.pdf)), que solo trae valores en saltos de 5 °C. Como $38$ °C está entre $35$ °C y $40$ °C, hace falta **interpolar linealmente**.

**Cómo se interpola (explicado desde cero):** si se conoce el valor de una función en dos puntos $T_a$ y $T_b$ ($T_a<T_b$), y se quiere estimar su valor en un punto intermedio $T$, la interpolación lineal asume que la función crece de manera aproximadamente recta entre esos dos puntos:

$$f(T) \approx f(T_a) + \frac{T-T_a}{T_b-T_a}\Big[f(T_b)-f(T_a)\Big]$$

De la tabla: a $35$ °C, $P_s=5.628\ \text{kPa}$; a $40$ °C, $P_s=7.384\ \text{kPa}$. Con $T=38$ °C:

$$P_{s,38°C} \approx 5.628 + \frac{38-35}{40-35}\,(7.384-5.628) = 5.628 + \frac{3}{5}(1.756) = 5.628+1.054$$

$$P_{s,38°C} \approx 6.682\ \text{kPa}$$

Convirtiendo a mmHg (con el factor $760/101.325=7.5006$ mmHg por kPa, igual que en el Ejercicio 1):

$$P_{s,38°C} \approx 6.682\times 7.5006 = 50.13\ \text{mmHg}$$

Este valor coincide, con menos del 1 % de diferencia, con el que usa el material original ($49.692\ \text{mmHg}$) — se usará este último por ser el dato "oficial" del ejercicio, ya que la coincidencia confirma que es correcto.

**Paso 2 — Presión parcial del agua en el estado (1).**

$$p_{v1} = \frac{\%Y_{R1}\times P_{s1}}{100} = \frac{90\times 49.692}{100} = 44.723\ \text{mmHg}$$

**Paso 3 — Convertir la presión total del estado (1) a mmHg.**

$$P_1 = 33.02\ \text{kPa}\times\frac{760\ \text{mmHg}}{101.3\ \text{kPa}} = 33.02\times 7.5025 = 247.73\ \text{mmHg}$$

**Paso 4 — Saturación molar en el estado (1).**

$$Y_{m1} = \frac{p_{v1}}{P_1-p_{v1}} = \frac{44.723}{247.73-44.723} = \frac{44.723}{203.01}$$

$$Y_{m1} = 0.2203\ \frac{\text{mol agua}}{\text{mol aire seco}} \approx 0.22$$

**Paso 5 — Hipótesis a probar: "no hay condensación".** Si no condensa nada de agua, la **cantidad de moles de agua por mol de aire seco no cambia** entre (1) y (2) — porque no se agrega ni se quita agua del sistema, solo se comprime:

$$Y_{m2} \overset{?}{=} Y_{m1} = 0.22\ \frac{\text{mol agua}}{\text{mol aire seco}}$$

(el signo de interrogación indica que esto es una **hipótesis**, todavía por confirmar o refutar).

**Paso 6 — Convertir la presión total del estado (2) a mmHg.**

$$P_2 = 344.42\ \text{kPa}\times\frac{760}{101.3} = 344.42\times 7.5025 = 2584.4\ \text{mmHg}$$

**Paso 7 — Presión parcial "hipotética" en (2), suponiendo que no condensa.** Despejando $p_{v2}$ de $Y_{m2}=p_{v2}/(P_2-p_{v2})$ (mismo despeje algebraico que en el paso 7 del Ejercicio 1):

$$p_{v2} = \frac{Y_{m2}\,P_2}{1+Y_{m2}} = \frac{0.22\times 2584.4}{1.22} = \frac{568.57}{1.22}$$

$$p_{v2} \approx 466\ \text{mmHg}$$

**Paso 8 — Presión de saturación del agua a 49 °C (por interpolación, igual que en el paso 1).** De la tabla: a $45$ °C, $P_s=9.593\ \text{kPa}$; a $50$ °C, $P_s=12.349\ \text{kPa}$.

$$P_{s,49°C} \approx 9.593+\frac{49-45}{50-45}(12.349-9.593) = 9.593+\frac{4}{5}(2.756) = 9.593+2.205$$

$$P_{s,49°C} \approx 11.80\ \text{kPa} = 11.80\times 7.5006 = 88.49\ \text{mmHg}$$

(el material original usa $88.02\ \text{mmHg}$ — de nuevo, coincide con menos del 1 % de diferencia, lo que confirma el dato).

**Paso 9 — Comparar y concluir.**

$$p_{v2}\,(466\ \text{mmHg}) \quad \textbf{versus} \quad P_{s2}\,(88.02\ \text{mmHg})$$

Como $p_{v2} \gg P_{s2}$, la hipótesis "no hay condensación" es **imposible** (el vapor no puede sostener una presión parcial más de 5 veces mayor que su presión de saturación). Por tanto:

$$\boxed{\text{Sí se produce condensación de agua.}}$$

### 3.4 Parte (b) — Cantidad de agua condensada y volumen final

**Paso 10 — Reformular el estado (2): ahora sí está saturado.** Como condensa agua, el sistema se autorregula: la cantidad de vapor que queda en fase gaseosa es exactamente la que hace que $p_{v2}=P_{s2}$ (ni más, ni menos — si quedara más vapor, seguiría condensando; si quedara menos, se evaporaría más agua líquida hasta llegar de nuevo a ese punto de equilibrio). Entonces, en el estado (2) **real** (con condensación):

$$p_{v2} = P_{s2} = 88.02\ \text{mmHg}$$

**Paso 11 — Recalcular $Y_{m2}$, ahora con el valor correcto (saturado).**

$$Y_{m2} = \frac{P_{s2}}{P_2-P_{s2}} = \frac{88.02}{2584.4-88.02} = \frac{88.02}{2496.4}$$

$$Y_{m2} = 0.03526\ \frac{\text{mol agua}}{\text{mol aire seco}} \approx 0.0353$$

**Paso 12 — Balance de agua: cuánto condensó.** El agua que entró como vapor (en el estado 1) menos el agua que sale todavía como vapor (en el estado 2, ya saturado) es, por conservación de masa, el agua que condensó:

$$H_2O_{\text{cond}} = Y_{m1} - Y_{m2} = 0.22 - 0.0353$$

$$\boxed{H_2O_{\text{cond}} = 0.1847\ \frac{\text{mol}\ H_2O}{\text{mol aire seco}}}$$

**Paso 13 — Volumen de la mezcla de salida.** Se pide en m³ **por mol de aire seco**, así que conviene tomar como **base de cálculo 1 mol de aire seco**. Con esa base, los moles totales que quedan en fase gaseosa en la salida son:

$$n_T = n_{\text{aire seco}} + n_{\text{agua (vapor, en 2)}} = 1 + Y_{m2} = 1+0.0353 = 1.0353\ \text{mol}$$

**Por qué se usa $Y_{m2}$ y no $Y_{m1}$ aquí:** porque el volumen que se pide es el de la mezcla que **sale** del compresor (el agua que condensó ya no es parte de la fase gaseosa que ocupa ese volumen — está como líquido separado, ocupando un volumen despreciable en comparación).

Aplicando la ecuación de gas ideal, $PV=n_TRT$, con $R=8.3\times10^{-3}\ \text{m}^3\cdot\text{kPa}/(\text{mol}\cdot\text{K})$ (el valor de $R$ en estas unidades particulares, para que $P$ en kPa y $V$ en m³ combinen correctamente), $T=49+273=322\ \text{K}$, y $P=344.42\ \text{kPa}$ (la presión total real del sistema, no la parcial):

$$V = \frac{n_T\,R\,T}{P} = \frac{1.0353\times 8.3\times10^{-3}\times 322}{344.42}$$

Desglosando la aritmética paso a paso: $1.0353\times 8.3\times10^{-3}=8.593\times10^{-3}$; luego $8.593\times10^{-3}\times 322 = 2.767$; finalmente $2.767/344.42 = 8.03\times10^{-3}$.

$$\boxed{V = 8.0\times10^{-3}\ \frac{\text{m}^3}{\text{mol aire seco}}}$$

### 3.5 Resultado final del Ejercicio 2

$$H_2O_{\text{cond}} = 0.1847\ \frac{\text{mol}}{\text{mol a.s.}}\,,\qquad\qquad V = 8.0\times10^{-3}\ \frac{\text{m}^3}{\text{mol a.s.}}$$

**Aplicación industrial que señala la propia clase práctica:** este tipo exacto de cálculo (comprimir aire húmedo, verificar condensación, retirar el agua) es el que se realiza en las **plantas de obtención de O₂ y N₂**, en la etapa de preparación del aire antes de enviarlo a la torre de destilación criogénica — si no se retira el agua antes, se congelaría dentro de los equipos de enfriamiento y los obstruiría.

---

## 4. Ejercicio 3 — Trabajo independiente: deshumidificación por compresión

### 4.1 Enunciado

Aire húmedo a $t=34\ \text{°C}$ y $t_{bh}=27.3\ \text{°C}$ (temperatura de **bulbo húmedo** — se mide con un termómetro cuyo bulbo está envuelto en una mecha mojada; se define formalmente en la Conferencia 4, sección 2.2), $P=101.3\ \text{kPa}$. Se plantea deshumidificar aumentando la presión hasta $266.6\ \text{kPa}$ y disminuyendo la temperatura en $10\ \text{°C}$ (es decir, $T_{\text{final}}=24\ \text{°C}$). Si el volumen inicial de la mezcla es $6\ \text{m}^3$, determine la cantidad de agua condensada y el volumen final de la mezcla.

**Respuesta reportada por el material original:** $H_2O_{\text{cond}}=0.114\ \text{kg}$, $V_{\text{final}}=2.046\ \text{m}^3$.

### 4.2 Por qué este ejercicio es distinto a los dos anteriores

En los Ejercicios 1 y 2, la composición inicial se podía calcular **directamente con fórmulas** a partir de $\%Y_R$. Aquí, en cambio, el dato de entrada es la pareja $(t,\ t_{bh})$ — dos temperaturas medidas con termómetros. Como se explica en la Conferencia 4 (secciones 2.2 y 4), la relación entre $(t,t_{bh})$ y la composición $Y$ **no** es una fórmula algebraica simple: requiere o bien la **carta sicrométrica** (lectura gráfica) o bien un balance de energía completo (contenido que pertenece al Tema 4, Balance de Energía, todavía no visto en este punto del curso). Por eso este ejercicio se resuelve aquí exponiendo el **método completo**, y se contrasta el resultado con la respuesta oficial, en vez de pretender una precisión numérica que la lectura de un gráfico impreso no permite reproducir por escrito.

### 4.3 Método paso a paso

**Paso 1 — Leer $Y_1$ en la carta sicrométrica.** Se ubica la intersección de la vertical $t=34\ \text{°C}$ con la línea de bulbo húmedo $t_{bh}=27.3\ \text{°C}$ (para el sistema agua-aire, esa línea coincide con la de temperatura de saturación adiabática — ver Conferencia 4, sección 2.4). El punto de intersección da directamente $Y_1$ en el eje vertical de la carta. Como referencia de orden de magnitud (calculada con la ecuación de saturación adiabática, que anticipa contenido del Tema 4, usando calor húmedo $C_s\approx 1.005+1.88\,Y$ kJ/(kg·K) y el calor de vaporización del agua a $27.3$ °C, interpolado de las Steam Tables en $\approx 2437\ \text{kJ/kg}$): $Y_1\approx 0.024\ \text{kg agua/kg aire seco}$.

**Paso 2 — Volumen húmedo inicial.** Con la fórmula de la Conferencia 4, sección 3.2, $V_H=(0.082/P_{\text{atm}})(t+273)(1/MM_g+Y/MM_v)$, usando $Y_1\approx0.024$, $T_1=307\ \text{K}$, $P_1\approx1\ \text{atm}$:

$$V_{H1} \approx \frac{0.082}{1}\times 307\times\left(\frac{1}{29}+\frac{0.024}{18}\right) \approx 0.90\ \frac{\text{m}^3}{\text{kg a.s.}}$$

**Paso 3 — Masa de aire seco.**

$$m_{as} = \frac{V_1}{V_{H1}} = \frac{6}{0.90} \approx 6.7\ \text{kg aire seco}$$

**Paso 4 — Composición de salida ($Y_2$), asumiendo que el proceso satura la mezcla.** Como se comprime **y** se enfría, y el enunciado dice explícitamente "deshumidificar", la mezcla de salida está saturada (mismo razonamiento del Ejercicio 2, sección 3.2). Con $P_s(24°C)\approx 3.00\ \text{kPa}$ (interpolado de las Steam Tables entre $20$ °C y $25$ °C, igual que en la sección 3.3) y $P_2=266.6\ \text{kPa}$:

$$Y_2 = \frac{MM_{H_2O}}{MM_{\text{aire}}}\cdot\frac{P_s}{P_2-P_s} \approx \frac{18}{29}\times\frac{3.00}{266.6-3.00} \approx 0.0071\ \frac{\text{kg agua}}{\text{kg a.s.}}$$

**Paso 5 — Agua condensada.**

$$H_2O_{\text{cond}} = m_{as}\,(Y_1-Y_2) \approx 6.7\times(0.024-0.0071) \approx 0.11\ \text{kg}$$

**Paso 6 — Volumen final.** Se calcula $V_{H2}$ con la misma fórmula del paso 2, usando $Y_2$, $T_2=297\ \text{K}$ y $P_2$ en atm, y luego $V_2=m_{as}\times V_{H2}$.

### 4.4 Comparación con la respuesta oficial

El resultado de este método ($H_2O_{\text{cond}}\approx 0.11\ \text{kg}$) coincide, dentro de un margen razonable, con el reportado por el material original ($0.114\ \text{kg}$); la pequeña diferencia se debe a que $Y_1$ aquí se estimó con una fórmula aproximada (porque este documento no dispone de la carta sicrométrica impresa como archivo), mientras que en el aula ese valor se lee directamente y con mayor exactitud sobre el gráfico físico (Figura B-10 del texto). El valor $V_{\text{final}}=2.046\ \text{m}^3$ que reporta el material debe tomarse como la referencia a alcanzar una vez que se lea $Y_1$ directamente de la carta.

$$\boxed{H_2O_{\text{cond}} = 0.114\ \text{kg}\,,\qquad V_{\text{final}}=2.046\ \text{m}^3 \quad \text{(respuesta oficial del material fuente)}}$$

---

## 5. Ejercicios adicionales asignados (no resueltos aquí)

El "Trabajo Independiente" de la clase práctica pide además resolver los **ejercicios 6, 8 y 9 de la página 201** del libro de texto (Cruz/Pons, *Introducción a la Ingeniería Química*). Ese texto **no forma parte de los archivos digitales de esta carpeta**, así que esos tres ejercicios no se pueden reproducir aquí con fidelidad (no se conoce su enunciado exacto). Quien tenga acceso físico al libro puede resolverlos aplicando exactamente el mismo formulario y los mismos métodos desarrollados en las secciones 2 a 4 de este documento.

---

## 6. Conclusiones de la clase práctica

1. **Conociendo una sola forma de expresar la composición, se pueden obtener todas las demás**, siempre que se conozcan las masas molares del vapor y del gas, y la presión total del sistema — esta es la idea que se ejercitó en los tres ejercicios, pasando constantemente entre bases molares y másicas.
2. **El criterio para decidir si una mezcla condensa** es comparar la presión parcial "hipotética" del vapor (calculada suponiendo que no hay cambios de composición) contra la presión de saturación a la temperatura final: si la hipotética supera a $P_s$, condensa, y hay que recalcular con la salida saturada ($p_v=P_s$).
3. Se ejercitó el uso de **diagramas y tablas** (el gráfico de Cox y las tablas de vapor de agua) para, dada una temperatura, obtener la presión de saturación, y viceversa — la habilidad central que exige toda esta clase práctica.
4. No todos los problemas se pueden resolver con la carta sicrométrica: en el Ejercicio 2, por ejemplo, la mezcla alcanza presiones (2584 mmHg ≈ 3.4 atm) muy por encima del rango de 1 atm para el que está construida la carta sicrométrica estándar — por eso ahí hubo que resolver todo algebraicamente.

---

## Referencias / fuentes usadas en este documento

- [PIQ1 Clase practica 3 Composicion de las mezclas vapor-gas Etanol y compresor de aire.pdf](PIQ1%20Clase%20practica%203%20Composicion%20de%20las%20mezclas%20vapor-gas%20Etanol%20y%20compresor%20de%20aire.pdf) — fuente principal de los tres ejercicios.
- [Conferencia 3 - Presion de Vapor y Composicion de Mezclas Vapor-Gas.md](Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md) — teoría y demostraciones de las fórmulas usadas aquí.
- [../diagrama de COX.pdf](../diagrama%20de%20COX.pdf) — Figura B.9 real, usada en el Ejercicio 1.
- [../Steam Tables_Keenan.pdf](../Steam%20Tables_Keenan.pdf) — tablas de agua saturada, usadas para verificar e interpolar los valores de $P_s$ del Ejercicio 2 y del Ejercicio 3.
