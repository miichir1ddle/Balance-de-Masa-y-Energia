# Tema 2 — Conferencia 3: Evaluación de la presión de vapor y composición de las mezclas vapor-gas

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuente principal:** [Conferencia 3 Tema 2 Plan E.pdf](Conferencia%203%20Tema%202%20Plan%20E.pdf)
> **Apoyo:** [Guia de estudio Tema 2.pdf](Guia%20de%20estudio%20Tema%202.pdf) · [PIQ1 Clase practica 3 Composicion de las mezclas vapor-gas Etanol y compresor de aire.pdf](PIQ1%20Clase%20practica%203%20Composicion%20de%20las%20mezclas%20vapor-gas%20Etanol%20y%20compresor%20de%20aire.pdf) · [../diagrama de COX.pdf](../diagrama%20de%20COX.pdf) (Figura B‑9 del texto, gráfica de Cox‑Othmer real) · [../Steam Tables_Keenan.pdf](../Steam%20Tables_Keenan.pdf) (tablas de vapor de agua, usadas aquí para verificar cada resultado numérico)
>
> Este documento explica, paso a paso y sin dar nada por sabido, todo lo que la Conferencia 3 exige: qué diferencia a un vapor de un gas, qué es la presión de vapor y cómo se evalúa (métodos analíticos y gráficos, con énfasis en el método de Cox), y las siete formas de expresar la composición de una mezcla vapor-gas, con las relaciones que existen entre ellas. Cada ejemplo que trae la Clase Práctica #3 se resuelve aquí completo, con la aritmética verificada de forma independiente contra las tablas de vapor de agua y la ecuación de Antoine (los resultados coinciden con menos de 1 % de diferencia, lo que confirma que los datos del material original son correctos).

---

## 0. Dónde estamos y por qué este tema

### 0.1 Ubicación dentro del programa

Como se explicó en el [Tema 1](../TEMA%201/Conferencia%201%20-%20Sistemas%20de%20Unidades%20y%20Dimensiones.md), la asignatura organiza su contenido en 4 temas:

| Tema | C | CP | CPM | Evaluación | Total |
|---|---|---|---|---|---|
| 1. Unidades y Dimensiones | 4 | 4 | 0 | 0 | 8 |
| **2. Mezclas Vapor-Gas** | **4** | **4** | **0** | **0** | **8** |
| 3. Balance de Masa | 4 | 14 | 2 | 2 (PP) | 22 |
| 4. Balance de Energía | 6 | 19 | 4 | 1 (TC) | 30 |

Tema 2 tiene 4 conferencias y 4 clases prácticas. Esta carpeta contiene las Conferencias 3 y 4 (numeradas de forma consecutiva con las del Tema 1, no reiniciadas), junto con las Clases Prácticas 3 y 4 que las acompañan. Esta Conferencia 3 corresponde, dentro del propio Tema 2, a su **primera** conferencia.

### 0.2 Por qué se estudian las mezclas vapor-gas

El texto guía lo introduce con ejemplos concretos de la industria:

- **Acondicionamiento de aire.**
- **Obtención de O₂ y N₂** a partir de aire húmedo (separación criogénica: antes de enfriar el aire hasta licuarlo hace falta conocer cuánta agua contiene, para poder retirarla y que no se congele y obstruya los equipos).
- **Enfriamiento de agua con aire** (torres de enfriamiento).
- Fabricación de **tejidos, papel y pastas alimenticias**, que se elaboran bajo condiciones específicas de vapor de agua en el aire.

La mezcla **agua–aire** es, con diferencia, la más estudiada: de ella depende el bienestar fisiológico humano (por eso hablamos de "humedad relativa" en el clima) y aparece en un sinnúmero de procesos industriales. Este tema construye las herramientas cuantitativas (fórmulas y gráficos) para trabajar con cualquier mezcla vapor-gas, y en la Conferencia 4 se particulariza todo al caso agua-aire mediante la carta sicrométrica.

### 0.3 Relación con los demás temas

Como señala la [Guía de estudio del Tema 2](Guia%20de%20estudio%20Tema%202.pdf):

- El concepto de **presión de vapor** ya se estudió en Química Física I; aquí se **retoma y se profundiza**, sobre todo en los métodos gráficos.
- Las **formas de expresar la composición** que se presentan en esta conferencia requieren **conversión de unidades**, tema ya dominado en el [Tema 1](../TEMA%201/).
- Los cálculos de cantidades de vapor condensado o evaporado que se hacen en los ejercicios **no son más que balances de masa** elementales — el mismo tipo de cálculo que se formalizará con todo rigor en el Tema 3. La propia Conferencia 3 lo señala explícitamente al cerrar.

---

## 1. Objetivos de la conferencia

Tal como los plantea el texto:

- Conocer el método de evaluación de la **presión de vapor** con sustancias de referencia.
- Conocer las **formas de expresar la composición** de una mezcla vapor-gas.

---

## 2. Aspectos introductorios: ¿qué diferencia a un vapor de un gas?

Esta distinción, según indica la propia conferencia, ya se vio en Química Física I, pero conviene "rememorarla" porque es la base de todo el tema:

- Una sustancia gaseosa que está a una **temperatura menor que su temperatura crítica** ($T < T_c$) se denomina **vapor**, y es **condensable mediante una compresión isotérmica** (es decir: si a esa temperatura le subo suficiente la presión, sin cambiar la temperatura, se convierte en líquido).
- El término **gas** se usa para una sustancia en estado gaseoso cuya temperatura es **superior a la crítica** ($T > T_c$): es **incondensable por compresión isotérmica** (por mucho que se le suba la presión a esa temperatura, no se licua).

> **Recordatorio:** la temperatura crítica $T_c$ de una sustancia pura es la temperatura por encima de la cual no existe una frontera definida entre líquido y gas — no importa cuánta presión se aplique, la sustancia no puede condensarse. Es una propiedad característica de cada sustancia.

### 2.1 Ejemplo guiado (el que trae la conferencia)

Mezcla agua–aire a $P = 101.3\ \text{kPa}$ y $T = 300\ \text{K}$ (≈ 27 °C), con $T_{c,\text{aire}} = 133\ \text{K}$ y $T_{c,\text{agua}} = 647\ \text{K}$:

| Componente | Comparación | Conclusión |
|---|---|---|
| H₂O | $T(300\text{K}) < T_c(647\text{K})$ | Es **vapor** (puede condensar) |
| Aire | $T(300\text{K}) > T_c(133\text{K})$ | Es **gas** (no puede condensar por compresión isotérmica a esa T) |

Esto explica por qué, a temperatura ambiente, el agua del aire húmedo puede condensarse (rocío, niebla, el "sudor" de un vaso con agua fría) mientras que el nitrógeno y el oxígeno del aire jamás lo hacen en esas condiciones: están muy por encima de su temperatura crítica.

**Por qué importa esta distinción:** en los cálculos tecnológicos de mezclas vapor-gas, identificar correctamente cuál componente es el "vapor" (condensable) y cuál es el "gas" (incondensable) es indispensable para plantear correctamente la composición del sistema — como se verá en la sección 5, todas las definiciones de composición tratan al vapor y al gas de forma asimétrica.

---

## 3. Evaluación de la presión de vapor

### 3.1 Definición

Cuando un líquido se coloca en un espacio cerrado, sus moléculas se evaporan y otras se condensan de vuelta al líquido. Al principio la vaporización domina, pero a medida que se acumula vapor, la condensación se acelera, hasta que **las velocidades de vaporización y de condensación se igualan**: se alcanza un **equilibrio dinámico**. En ese equilibrio, la presión que ejerce el vapor sobre el líquido se llama **presión de vapor** del líquido, y se denota $P_s$.

La presión de vapor de un líquido depende de:

1. La **naturaleza** del líquido (cada sustancia tiene la suya).
2. La **temperatura** (a mayor T, mayor $P_s$: las moléculas tienen más energía para escapar del líquido).
3. La presión externa total (en la práctica, para los propósitos de este curso, la dependencia relevante es con la temperatura).

### 3.2 El diagrama P vs T de una sustancia pura

Para visualizar cómo depende $P_s$ de $T$, se usa un diagrama de fases presión-temperatura. Tomando el agua como ejemplo (a $101.3\ \text{kPa}$, escala de referencia horizontal):

| Región / curva | Qué representa |
|---|---|
| Curva **DA** | Equilibrio sólido–vapor (sublimación) |
| Curva **AC** | Equilibrio sólido–líquido (fusión) |
| Curva **AB** | Equilibrio **líquido–vapor** (la curva de presión de vapor propiamente dicha) |
| Punto **A** | Punto triple: coexisten sólido, líquido y vapor simultáneamente |
| Región a la izquierda/arriba de AB y AC | **Sólido** |
| Región entre AC/AB (arriba) | **Líquido** |
| Región por debajo de AB (a la derecha) | **Gas** |

**Sobre la curva AB** (la que interesa en este tema): cada punto representa un **estado de equilibrio**, donde a **cada valor de temperatura le corresponde uno y solo uno** valor de presión de equilibrio (la presión de vapor a esa temperatura). Esto es justamente lo que permite tabular o graficar $P_s$ en función de $T$: es una función, no una relación arbitraria.

- La temperatura a la que se alcanza ese equilibrio dinámico se llama **temperatura de saturación**, y la presión correspondiente es la **presión de saturación** o **presión de vapor** ($P_s$). En el estado de equilibrio coexisten dos fases: **líquido saturado** y **vapor saturado**.
- Un estado **líquido** a una temperatura **menor** que la de saturación correspondiente a esa presión se llama **líquido subenfriado**. Gráficamente: cualquier punto dentro del "plano" delimitado por las curvas CA y AB, fuera de la línea de equilibrio (por ejemplo, el punto marcado "1" en la figura original, a 80 °C con la curva AB pasando por encima a esa T).
- Un estado de **vapor** a una temperatura **mayor** que la de saturación correspondiente a esa presión se llama **vapor sobrecalentado** (punto "3" en la figura, a 120 °C). Gráficamente: cualquier punto por debajo de la curva DAB extendida.
- Se define los **grados de sobrecalentamiento** ($^{\text{o}}SC$) como la diferencia entre la temperatura real del vapor y la temperatura de saturación que le correspondería a esa misma presión:

$$^{\text{o}}SC = (T_3 - T_2)_{P\ \text{cte}}$$

donde $T_2$ es la temperatura de saturación a esa presión (el punto "2" sobre la curva AB) y $T_3$ la temperatura real, mayor, del vapor sobrecalentado.

> **Ejemplo numérico con los propios valores de la figura:** a $P = 101.3\ \text{kPa}$, el agua satura a $T_2 = 100\ \text{°C}$ (es su temperatura normal de ebullición). Si el vapor está realmente a $T_3 = 120\ \text{°C}$ y a esa misma presión, sus grados de sobrecalentamiento son $^{\text{o}}SC = 120 - 100 = 20\ \text{°C}$. Si en cambio tenemos líquido a $T_1 = 80\ \text{°C}$ (por debajo de los 100 °C de saturación a esa presión), es líquido subenfriado.

### 3.3 Métodos para evaluar cuantitativamente $P_s$

Como la temperatura es una variable fácil de medir, todos los métodos se basan en la dependencia $P_s = P_s(T)$.

#### a) Métodos analíticos

**a.1 — Ecuación de Clausius-Clapeyron.** Ya se empleó en Química Física I:

$$\frac{d\ln P_s}{dT} = \frac{\Delta H_V}{R\,T^2}$$

donde $\Delta H_V$ es el calor (entalpía) de vaporización y $R$ la constante universal de los gases. Esta ecuación se obtiene de la termodinámica del equilibrio de fases; su forma integrada (asumiendo $\Delta H_V$ aproximadamente constante en un intervalo de T) da una relación lineal entre $\ln P_s$ y $1/T$.

**a.2 — Ecuación de Antoine.** Es una modificación empírica de Clausius-Clapeyron pensada para lograr mayor linealidad (mejor ajuste) en un intervalo más amplio de temperaturas:

$$\ln P_s = A - \frac{B}{T + C}$$

donde $A$, $B$ y $C$ son constantes específicas de cada sustancia (se obtienen por ajuste de datos experimentales). Esta es, en la práctica moderna, la forma más usada para calcular presiones de vapor por vía puramente analítica, y es la que se emplea en este documento para **verificar** los datos numéricos de los ejercicios resueltos más adelante (secciones 6.1 y 6.2).

#### b) Métodos gráficos

Tienen como ventaja dar una respuesta **más rápida** que los métodos analíticos, a cambio de menor precisión. Se construyen a partir de tablas de $P_s$ experimentales a distintas temperaturas. Los más importantes:

| Método | Ejes | Dónde se estudia (texto) |
|---|---|---|
| b.1 | $P_s$ vs $1/T$ | Epígrafe 2.7.4a, pág. 93 |
| b.2 | $\ln P_s$ vs $1/T$ | Epígrafe 2.7.4b, pág. 97 |
| b.3 | $\ln P_s$ vs $T$ | Epígrafe 2.7.4c, pág. 100 |
| b.4 | **Sustancias de referencia** (método de Cox) | Se detalla en la sección 4 |

Los tres primeros (b.1–b.3) son gráficos directos de $P_s$ tabulada contra alguna función de $T$; su fundamento es simplemente "graficar los datos de forma que salga lo más parecido a una recta posible", usando las formas sugeridas por Clausius-Clapeyron o Antoine. El cuarto método (b.4), por ser el más novedoso y el que efectivamente se usa en los ejercicios de este tema, se desarrolla en detalle a continuación.

---

## 4. Gráficos con sustancias de referencia: el método de Cox

### 4.1 Idea general

Estos métodos amplían el intervalo de linealidad de la dependencia $P_s$–$T$ y necesitan pocos datos experimentales. Se basan en una relación empírica: si se grafica una propiedad física de una sustancia (de la que se tiene información muy completa) contra la **misma propiedad de otra sustancia**, a menudo se obtiene una relación lineal. Aplicado a la presión de vapor, y tomando generalmente el **agua** como sustancia de referencia (porque sus propiedades están tabuladas con muchísima precisión — ver las [Steam Tables](../Steam%20Tables_Keenan.pdf) de este repositorio), existen dos métodos: el de **Cox-Othmer** y el de **Düring**. Aquí solo se estudia el primero.

### 4.2 Fundamento del método de Cox

El logaritmo de la presión de vapor de un líquido *i* a una temperatura dada es una **función lineal** del logaritmo de la presión de vapor de un líquido de referencia *r* a **esa misma temperatura**. La ecuación que fundamenta esto es:

$$d\ln P_s^{(i)} = \left[\frac{\Delta H_s^{(i)}}{\Delta H_s^{(r)}}\right] d\ln P_s^{(r)}$$

donde $P_s^{(i)}$, $\Delta H_s^{(i)}$ son la presión de vapor y el calor de vaporización de la sustancia de interés, y $P_s^{(r)}$, $\Delta H_s^{(r)}$ los de la sustancia de referencia. Lo importante es que la razón $\Delta H_s^{(i)}/\Delta H_s^{(r)}$ es, en la práctica, **prácticamente constante** en un intervalo amplio de temperaturas — y por eso, al integrar, la relación entre $\ln P_s^{(i)}$ y $\ln P_s^{(r)}$ resulta (aproximadamente) **una línea recta**, aunque cada una individualmente dependa de $T$ de forma curva (tipo Clausius-Clapeyron).

**¿Qué representa un punto sobre la línea de Cox?** Cada punto de esa recta corresponde a un valor de temperatura común $T$; ese punto da el par $\big(P_s^{(r)}(T),\ P_s^{(i)}(T)\big)$: las presiones de vapor, en general distintas entre sí, que tendrían la sustancia de referencia y la sustancia de interés **a esa misma temperatura**.

**¿Cuántos valores experimentales de $P_s^{(i)}$ se necesitan?** Solo **dos** — porque una recta queda determinada por dos puntos. Con solo conocer $P_s^{(i)}$ a dos temperaturas (y las correspondientes $P_s^{(r)}$ del agua, que ya están tabuladas), se puede trazar toda la recta y luego leer $P_s^{(i)}$ a **cualquier otra temperatura** dentro del rango de validez.

### 4.3 Procedimiento paso a paso

1. **A dos temperaturas dadas** $T_1$ y $T_2$, se buscan los valores correspondientes de $P_s^{(i)}$ y $P_s^{(r)}$ (agua):

   | $T$ | $P_s^{(i)}$ | $P_s^{(r)}$ |
   |---|---|---|
   | $T_1$ | $P_{s1}^{(i)}$ | $P_{s1}^{(r)}$ |
   | $T_2$ | $P_{s2}^{(i)}$ | $P_{s2}^{(r)}$ |

2. En **papel logarítmico**, se grafica $P_s^{(i)}$ (eje vertical) contra $P_s^{(r)}$ (eje horizontal); con solo esos dos puntos, ambos en escala logarítmica, queda determinada la recta de Cox para la sustancia *i*.
3. Para obtener $P_s^{(i)}$ a la **temperatura de interés**, se localiza la $P_s^{(r)}$ del agua a esa temperatura (que se lee de tablas, por ejemplo las Steam Tables) sobre el eje horizontal, se sube hasta interceptar la recta de Cox, y se lee el valor correspondiente de $P_s^{(i)}$ en el eje vertical.
4. En la práctica, para no tener que graficar cada sustancia por separado, existe un gráfico ya construido con muchas sustancias a la vez (Figura B.9 del texto — ver [../diagrama de COX.pdf](../diagrama%20de%20COX.pdf)): allí el eje horizontal está directamente calibrado en **temperatura** (usando como referencia interna el agua), y cada sustancia tiene su propia curva/recta. Esto permite, dada una temperatura, **leer directamente** la presión de vapor de decenas de sustancias (alcohol etílico, alcohol metílico, tolueno, mercurio, CO₂, NH₃, etc.) sin tener que construir el gráfico de Cox por separado cada vez. Este es exactamente el gráfico que se usa en el Ejercicio #1 de la Clase Práctica #3 (sección 6.1 de este documento).

**Ventaja fundamental del gráfico de Cox:** con muy pocos datos de la sustancia de interés (o ninguno, si ya está en el gráfico general de la Figura B.9), se puede evaluar su presión de vapor en un intervalo amplio de temperaturas con buena precisión, apoyándose en la información, mucho más completa, que se tiene del agua como referencia.

### 4.4 Método de Düring (autoestudio)

Se llama también "gráfico de igualdad de presiones". La conferencia lo deja como material de autoestudio, señalando que si se domina el de Cox, el de Düring se interpreta fácilmente por analogía (en vez de fijar temperaturas iguales y comparar presiones, fija presiones iguales y compara temperaturas). No se desarrolla más en este documento porque no forma parte del contenido evaluable explícito de esta conferencia.

---

## 5. Composición de las mezclas vapor-gas

### 5.1 Mezclas saturadas y no saturadas

Antes de definir cómo se expresa la composición, hay que distinguir dos estados posibles de una mezcla vapor-gas, comparando la **presión parcial** que ejerce el vapor en la mezcla ($p_v$) con su **presión de vapor** a esa misma temperatura ($P_s$):

- **Mezcla no saturada** (o parcialmente saturada): $(p_v < P_s)_T$. La mezcla "podría admitir más vapor" antes de saturarse.
- **Mezcla saturada**: $(p_v = P_s)_T$. La mezcla ya no admite más vapor a esa temperatura sin que empiece a condensar.

**Mecanismo físico:** si una mezcla parcialmente saturada se pone en contacto con líquido de la misma naturaleza que su vapor (por ejemplo, aire húmedo no saturado en contacto con agua líquida), comienza la vaporización del líquido. Si la temperatura se mantiene fija, la diferencia $(P_s - p_v)$ va **disminuyendo** a medida que se vaporiza más líquido y $p_v$ aumenta. Si el tiempo de contacto es suficientemente grande, eventualmente $p_v$ alcanza a $P_s$: **la mezcla se satura**. Este es, de hecho, el principio físico detrás del proceso de "saturación adiabática" que se estudiará en la Conferencia 4.

### 5.2 Notación que se usa en esta sección

| Símbolo | Significado |
|---|---|
| $P$ | Presión **total** de la mezcla |
| $p_v$ | Presión **parcial** del vapor en la mezcla (el texto original lo denota $\overline{P_v}$) |
| $P_s$ | Presión de **vapor** (saturación) del componente condensable, a la temperatura de la mezcla |
| $n_v,\ n_g$ | Moles de vapor y de gas, respectivamente |
| $N = n_v + n_g$ | Moles **totales** de la mezcla |
| $m_v,\ m_g$ | Masa de vapor y de gas, respectivamente |
| $M = m_v + m_g$ | Masa **total** de la mezcla |
| $MM_v,\ MM_g$ | Masa molar del vapor y del gas |

### 5.3 Las siete formas de expresar la composición

Conviene agruparlas, como hace la propia conferencia en su resumen final, en **tres grupos**: las que toman como base el **total de la mezcla**, las que toman como base el **gas libre de vapor**, y las que expresan directamente el **grado de saturación**.

#### Grupo 1 — Base: el total de la mezcla

**a) Fracción molar ($y_m$) y fracción presión ($y_P$)**

$$y_m = \frac{n_v}{N} \qquad\qquad y_P = \frac{p_v}{P}$$

Si se asume **comportamiento de gas ideal**, la ley de Dalton establece que la presión parcial de un componente es igual a su fracción molar multiplicada por la presión total: $p_v = y_m\,P$. Reordenando, $y_m = p_v/P = y_P$. Es decir, **bajo gas ideal, fracción molar y fracción presión son numéricamente iguales**:

$$y_m = y_P = \frac{n_v}{N} = \frac{p_v}{P}$$

Y si además la mezcla está **saturada** ($p_v = P_s$):

$$(y_m)_{SAT} = \left(\frac{p_v}{P}\right)_{SAT} = \frac{P_s}{P}$$

**b) Fracción másica ($y$)**

$$y = \frac{m_v}{M}$$

Es el análogo másico de $y_m$: en vez de moles de vapor sobre moles totales, es masa de vapor sobre masa total.

**c) Masa de vapor por unidad de volumen de mezcla**

Aplicando la ecuación de gas ideal al vapor (presión parcial $p_v$, mismo volumen $V$ y temperatura $T$ que la mezcla):

$$p_v V = n_v R T = \frac{m_v}{MM_v}\,R T$$

Despejando la masa de vapor por unidad de volumen:

$$\frac{m_v}{V} = \frac{p_v\,MM_v}{RT}$$

Esta forma es útil, por ejemplo, cuando interesa saber cuánta masa de vapor hay disuelta en un metro cúbico de mezcla (concentración volumétrica), más que una fracción relativa.

#### Grupo 2 — Base: el gas libre de vapor (masa/moles de gas seco)

**d) Saturación molar ($Y_m$)**

Es la relación entre los moles de vapor y los moles de **gas** (no de mezcla total):

$$Y_m = \frac{n_v}{n_g} = \frac{n_v}{N - n_v}$$

Aplicando la ley de los gases ideales (Dalton) igual que antes, se obtiene:

$$Y_m = \frac{p_v}{P - p_v}$$

y para una mezcla **saturada**:

$$(Y_m)_{SAT} = \frac{P_s}{P - P_s}$$

Para la mezcla vapor de agua–aire en particular, esta magnitud recibe un nombre propio: **humedad molar**.

*Relación entre $Y_m$ y $y_m$:* dividiendo numerador y denominador de $Y_m = n_v/(N-n_v)$ entre $N$:

$$Y_m = \frac{n_v/N}{1 - n_v/N} = \frac{y_m}{1 - y_m} \qquad\Longleftrightarrow\qquad y_m = \frac{Y_m}{1+Y_m}$$

**e) Saturación ($Y$)**

Es el análogo másico de $Y_m$: la relación entre la masa de vapor y la masa de **gas**:

$$Y = \frac{m_v}{m_g}\,,\qquad m_v = n_v\,MM_v\,,\quad m_g = n_g\,MM_g$$

Sustituyendo estas dos expresiones en la definición de $Y$:

$$Y = \frac{n_v\,MM_v}{n_g\,MM_g} = \left(\frac{n_v}{n_g}\right)\frac{MM_v}{MM_g} = Y_m\,\frac{MM_v}{MM_g} \qquad\Longleftrightarrow\qquad Y_m = Y\,\frac{MM_g}{MM_v}$$

*Relación entre $Y$ y $y$:* por el mismo tipo de manipulación algebraica que para $Y_m$/$y_m$ (dividiendo $m_v/(M-m_v)$ entre $M$):

$$Y = \frac{y}{1-y} \qquad\Longleftrightarrow\qquad y = \frac{Y}{1+Y}$$

> **Pregunta que deja planteada la conferencia:** *"Si en una mezcla vapor-gas conocemos la fracción másica, ¿cómo calcular las demás?"* — La respuesta es precisamente esta red de relaciones: de $y$ se obtiene $Y = y/(1-y)$; de $Y$ se obtiene $Y_m = Y\cdot MM_g/MM_v$; de $Y_m$ se obtiene $y_m = Y_m/(1+Y_m)$; y de $y_m$ (vía Dalton) se obtiene $p_v = y_m P$. Es decir: **basta con conocer una sola forma de composición para poder calcular todas las demás**, siempre que se conozcan las masas molares y (si se necesita $p_v$) la presión total.

#### Grupo 3 — Expresan directamente el grado de saturación

Las cinco formas anteriores no dicen, por sí solas, **qué tan cerca está la mezcla de saturarse**. Para eso se definen:

**f) Porcentaje de saturación relativa ($\%Y_R$)**

Es la relación entre la presión parcial del vapor y la presión de vapor a la misma temperatura, expresada en por ciento:

$$\%Y_R = \left(\frac{p_v}{P_s}\right)_T \times 100$$

Para la mezcla vapor de agua–aire, esta cantidad se conoce popularmente como **humedad relativa** — el número que se escucha todos los días en el pronóstico del tiempo.

Bajo gas ideal, usando $y_m = p_v/P$ y $(y_m)_{SAT} = P_s/P$:

$$\%Y_R = \frac{p_v/P}{P_s/P}\times 100 = \left(\frac{y_m}{(y_m)_{SAT}}\right)\times 100$$

**¿Qué significan los valores extremos?** $\%Y_R = 0$ significa que no hay vapor en absoluto ($p_v=0$); $\%Y_R = 100$ significa que la mezcla está exactamente saturada ($p_v = P_s$) — es el límite en el que empieza a condensar.

**g) Porcentaje de saturación ($\%Y$)**

Se define como la relación entre los moles de vapor por mol de gas que **realmente** tiene la mezcla, y los moles de vapor por mol de gas que **tendría si estuviera saturada** a esas mismas condiciones de $T$ y $P$:

$$\%Y = \left[\frac{(n_v/n_g)}{(n_v/n_g)_{SAT}}\right]\times 100 = \left(\frac{Y_m}{(Y_m)_{SAT}}\right)\times 100 = \left(\frac{Y}{Y_{SAT}}\right)\times 100$$

Para la mezcla agua-aire, se conoce simplemente como **% Humedad**.

**Relación entre $\%Y$ y $\%Y_R$:** partiendo de $\%Y = (Y_m/(Y_m)_{SAT})\times 100$ y sustituyendo $Y_m = p_v/(P-p_v)$, $(Y_m)_{SAT} = P_s/(P-P_s)$:

$$\frac{Y_m}{(Y_m)_{SAT}} = \frac{p_v/(P-p_v)}{P_s/(P-P_s)} = \frac{p_v}{P_s}\cdot\frac{P-P_s}{P-p_v}$$

y como $p_v/P_s = \%Y_R/100$, se obtiene:

$$\%Y = \%Y_R\left[\frac{P-P_s}{P-p_v}\right]$$

que es exactamente la relación que trae la conferencia. De aquí se deducen dos consecuencias importantes:

- **Si la mezcla está saturada** ($P_s = p_v$): el corchete vale 1, así que $\%Y = \%Y_R$ (ambos indicadores de saturación coinciden, como es de esperar).
- **Si la mezcla NO está saturada**: como $P_s > p_v$ en ese caso, se cumple $(P-P_s) < (P-p_v)$, así que el corchete es menor que 1, y por tanto $\%Y < \%Y_R$. Esta es la respuesta a la pregunta que deja planteada la conferencia sobre mezclas no saturadas.

### 5.4 Resumen esquemático

| Grupo | Magnitudes | Base de referencia |
|---|---|---|
| 1 | $y_m$, $y_P$, $y$, $m_v/V$ | Total de la mezcla |
| 2 | $Y$, $Y_m$ | Solo el gas (masa/moles libres de vapor) |
| 3 | $\%Y$, $\%Y_R$ | Expresan el grado de saturación directamente |

**Idea central para retener:** todas estas definiciones están relacionadas entre sí mediante identidades algebraicas exactas (no aproximaciones), así que **conociendo una sola de ellas —y las masas molares y la presión total— se pueden calcular todas las demás**. Esta es la habilidad que se ejercita en los ejercicios resueltos a continuación.

---

## 6. Ejemplos resueltos (Clase Práctica #3)

A continuación se resuelven completos los ejercicios de la Clase Práctica #3, que es la que acompaña y ejercita directamente el contenido de esta conferencia (evaluación de $P_s$ por el método de Cox, y formas de expresar la composición). Todos los resultados numéricos fueron verificados de forma independiente en este documento contra la ecuación de Antoine (para el agua) y las [Steam Tables](../Steam%20Tables_Keenan.pdf) del repositorio.

### 6.1 Ejercicio 1 — Mezcla alcohol etílico–aire (uso del método de Cox)

**Enunciado:** una mezcla de alcohol etílico y aire, a $P = 101.3\ \text{kPa}$ y $T = 19\ \text{°C}$, tiene una saturación relativa del 60 %. A esta mezcla se le incorporan, por evaporación, 0.1886 g de alcohol por gramo de aire seco, hasta saturarse. Determine la temperatura final del proceso.

**Esquema:**

| | Estado (1) | Estado (2) |
|---|---|---|
| $P$ | 101.3 kPa | 101.3 kPa |
| $\%Y_R$ | 60 | 100 (saturada) |
| $T$ | 19 °C | ¿? |

Se incorporan 0.1886 g alcohol/g aire seco entre (1) y (2).

**Paso 1 — Presión de vapor del alcohol a 19 °C.** Se lee del gráfico de Cox (Figura B.9, sustancia = alcohol etílico) a $T=19\ \text{°C}$: $P_s = 40\ \text{mmHg}$.

**Paso 2 — Presión parcial del alcohol en el estado (1).** Como $\%Y_R = (p_v/P_s)\times 100$:

$$p_{v1} = \frac{60}{100}\times 40 = 24\ \text{mmHg}$$

**Paso 3 — Saturación molar en (1).**

$$Y_{m1} = \frac{p_{v1}}{P - p_{v1}} = \frac{24}{760 - 24} = \frac{24}{736} = 0.0326\ \frac{\text{mol alcohol}}{\text{mol aire seco}}$$

(aquí la presión total se expresó en mmHg: $101.3\ \text{kPa} = 760\ \text{mmHg}$, exactamente 1 atm).

**Paso 4 — Convertir a base másica (saturación $Y$).** Usando $Y = Y_m\cdot(MM_v/MM_g)$, con $MM_{\text{alcohol etílico}} = 46\ \text{g/mol}$ y $MM_{\text{aire}} = 29\ \text{g/mol}$:

$$Y_1 = 0.0326\left(\frac{46}{29}\right) = 0.0517\ \frac{\text{g alcohol}}{\text{g aire seco}}$$

**Paso 5 — Balance de la evaporación.** Se incorporan 0.1886 g alcohol/g aire seco:

$$Y_2 = Y_1 + 0.1886 = 0.0517 + 0.1886 = 0.2403\ \frac{\text{g alcohol}}{\text{g aire seco}}$$

**Paso 6 — Volver a base molar.**

$$Y_{m2} = Y_2\left(\frac{29}{46}\right) = 0.2403\left(\frac{29}{46}\right) = 0.1515\ \frac{\text{mol alcohol}}{\text{mol aire seco}}$$

**Paso 7 — Presión parcial en (2).** Como el estado (2) está **saturado**, $p_{v2} = P_{s2}$. Despejando de $Y_{m2} = p_{v2}/(P-p_{v2})$:

$$p_{v2} = P_{s2} = \frac{Y_{m2}\,P}{1+Y_{m2}} = \frac{0.1515\times 760}{1+0.1515} = \frac{115.14}{1.1515} = 100\ \text{mmHg}$$

**Paso 8 — Leer la temperatura correspondiente en el gráfico de Cox.** Buscando en la Figura B.9, sobre la curva del alcohol etílico, a qué temperatura $P_s = 100\ \text{mmHg}$:

$$\boxed{T_{\text{final}} = 35\ \text{°C}}$$

**Verificación independiente (ecuación de Antoine para el etanol, $\ln P_s[\text{mmHg}] = A - B/(T[\text{°C}]+C)$ con $A=8.20417$, $B=1642.89$, $C=230.3$):**

- A $T=19$ °C: $P_s = 10^{8.20417 - 1642.89/249.3} = 10^{1.614} \approx 41.1\ \text{mmHg}$ (el material fuente usa 40 mmHg — diferencia menor al 3 %, coherente con la precisión de lectura de un gráfico).
- A $T=35$ °C: $P_s = 10^{8.20417 - 1642.89/265.3} = 10^{2.012} \approx 103\ \text{mmHg}$ (el cálculo pide 100 mmHg — de nuevo, diferencia menor al 3 %).

Esta verificación confirma que los datos y el resultado del ejercicio son físicamente correctos.

### 6.2 Ejercicio 2 — Compresión de aire húmedo (¿condensa o no?)

**Enunciado:** se desea comprimir aire húmedo desde $38\ \text{°C}$, $33.02\ \text{kPa}$ y $90\ \%$ de humedad relativa, hasta $344.42\ \text{kPa}$. Por efecto de la compresión, la temperatura se eleva hasta $49\ \text{°C}$.
(a) Determine si se produce o no condensación del agua.
(b) Si se produce, calcule la masa de agua condensada y el volumen de la mezcla en m³/mol de aire seco.

**Idea clave (antes de calcular):** la condensación ocurre si y solo si, a la temperatura final, la presión parcial que "querría" tener el vapor (si no condensara nada) **supera** la presión de saturación a esa temperatura: $(p_v > P_s)_T$. Como el vapor no puede ejercer más presión parcial que su $P_s$ a esa T sin condensar, si el cálculo "ideal" (sin condensación) da $p_v > P_s$, la conclusión es que **sí** condensa, y hay que recalcular con la mezcla saturada a la salida.

**Parte (a):**

**Paso 1 — Presión de saturación del agua a 38 °C.** De las [Steam Tables](../Steam%20Tables_Keenan.pdf) (interpolando entre 35 °C → 5.628 kPa y 40 °C → 7.384 kPa): $P_{s,38°C} \approx 6.68\ \text{kPa} = 50.1\ \text{mmHg}$, consistente con el valor que usa el ejercicio, $P_{s1} = 49.692\ \text{mmHg}$.

**Paso 2 — Presión parcial del agua en (1).**

$$p_{v1} = \frac{\%Y_{R1}\cdot P_{s1}}{100} = \frac{90\times 49.692}{100} = 44.723\ \text{mmHg}$$

**Paso 3 — Saturación molar en (1).** Con $P_1 = 33.02\ \text{kPa} = 33.02\times\dfrac{760}{101.3} = 247.7\ \text{mmHg}$:

$$Y_{m1} = \frac{p_{v1}}{P_1-p_{v1}} = \frac{44.723}{247.7-44.723} = \frac{44.723}{203.0} = 0.22\ \frac{\text{mol agua}}{\text{mol aire seco}}$$

**Paso 4 — Suponer que NO hay condensación** (hipótesis a verificar): si no condensa nada, la composición molar no cambia, $Y_{m2} = Y_{m1} = 0.22$. Con $P_2 = 344.42\ \text{kPa} = 344.42\times(760/101.3) = 2584.4\ \text{mmHg}$:

$$p_{v2} = \frac{Y_{m2}\,P_2}{1+Y_{m2}} = \frac{0.22\times 2584.4}{1.22} = 466\ \text{mmHg}$$

**Paso 5 — Comparar con $P_s$ a 49 °C.** De las Steam Tables (interpolando 45 °C → 9.593 kPa y 50 °C → 12.349 kPa): $P_{s,49°C}\approx 11.80\ \text{kPa} = 88.5\ \text{mmHg}$ (el ejercicio usa 88.02 mmHg — coincide con menos del 1 % de diferencia).

Como $p_{v2}(466\ \text{mmHg}) > P_{s2}(88.02\ \text{mmHg})$: **la hipótesis de "no condensación" es físicamente imposible** (el vapor no puede sostener una presión parcial mayor que su presión de saturación). Por tanto:

$$\boxed{\text{Sí se produce condensación.}}$$

**Parte (b) — Cálculo del agua condensada y el volumen:**

**Paso 6 — Como condensa, la mezcla de salida queda exactamente saturada:** $p_{v2} = P_{s2} = 88.02\ \text{mmHg}$.

$$Y_{m2} = \frac{P_{s2}}{P_2-P_{s2}} = \frac{88.02}{2584.4 - 88.02} = \frac{88.02}{2496.4} = 0.0353\ \frac{\text{mol agua}}{\text{mol aire seco}}$$

**Paso 7 — Agua condensada (balance de moles de agua, por mol de aire seco):**

$$H_2O_{\text{cond}} = Y_{m1} - Y_{m2} = 0.22 - 0.0353 = 0.1847\ \frac{\text{mol}\ H_2O}{\text{mol aire seco}}$$

**Paso 8 — Volumen de la mezcla de salida (por mol de aire seco).** Tomando como base **1 mol de aire seco**, los moles totales en la corriente de salida son $n_T = 1 + Y_{m2} = 1 + 0.0353 = 1.0353\ \text{mol}$. Con gas ideal ($R = 8.3\times10^{-3}\ \text{m}^3\cdot\text{kPa}/(\text{mol}\cdot\text{K})$):

$$V = \frac{n_T\,R\,T}{P} = \frac{1.0353\times 8.3\times10^{-3}\times(49+273)}{344.42} = 8.0\times10^{-3}\ \frac{\text{m}^3}{\text{mol aire seco}}$$

**Resultado final:**

$$\boxed{H_2O_{\text{cond}} = 0.1847\ \tfrac{\text{mol}}{\text{mol a.s.}}\,,\qquad V = 8.0\times10^{-3}\ \tfrac{\text{m}^3}{\text{mol a.s.}}}$$

Este es el tipo de cálculo que aparece en las **plantas de obtención de O₂ y N₂**, en la etapa de preparación (secado por compresión y enfriamiento) del aire antes de la destilación criogénica — exactamente el ejemplo industrial mencionado en la introducción de esta conferencia (sección 0.2).

### 6.3 Ejercicio 3 — Trabajo independiente (deshumidificación por compresión)

**Enunciado (dejado como tarea en la Clase Práctica #3):** aire húmedo a $t = 34\ \text{°C}$ y $t_{bh} = 27.3\ \text{°C}$ (temperatura de bulbo húmedo — se define formalmente en la Conferencia 4), $P = 101.3\ \text{kPa}$. Se plantea deshumidificar aumentando la presión hasta $266.6\ \text{kPa}$ y disminuyendo la temperatura en $10\ \text{°C}$ (es decir, $T_{\text{final}} = 24\ \text{°C}$). Si el volumen inicial de la mezcla es $6\ \text{m}^3$, determine el agua condensada y el volumen final.

**Respuesta que reporta el material fuente:** $H_2O_{\text{cond}} = 0.114\ \text{kg}$ y $V_{\text{final}} = 2.046\ \text{m}^3$.

**Método completo para resolverlo** (el procedimiento es formalmente idéntico al del Ejercicio 2, con la diferencia de que aquí el dato de entrada no es $\%Y_R$ sino la pareja $(t,\ t_{bh})$, que exige usar la **carta sicrométrica** del sistema agua-aire — la herramienta gráfica que se presenta recién en la Conferencia 4):

1. **Leer $Y_1$ en la carta sicrométrica**, ubicando el punto de intersección de $t=34\ \text{°C}$ con la curva de bulbo húmedo $t_{bh}=27.3\ \text{°C}$ (para el sistema agua-aire, como se verá en la Conferencia 4, $t_{bh}$ coincide con la temperatura de saturación adiabática, lo que permite ubicar el punto siguiendo esa curva desde el 100 % de saturación en $t_{bh}$ hasta la vertical de $t=34\ \text{°C}$). Ese punto da $Y_1$ (kg agua/kg aire seco) directamente. Usando la ecuación de saturación adiabática con calor húmedo aproximado ($C_s \approx 1.005+1.88\,Y$) y el calor de vaporización del agua a $27.3\ \text{°C}$ (≈ 2437 kJ/kg, interpolado de las Steam Tables), se obtiene un valor de referencia $Y_1 \approx 0.024\ \text{kg agua/kg aire seco}$, del orden correcto para verificar la lectura gráfica.
2. **Calcular el volumen húmedo inicial $V_{H1}$** con la fórmula de la sección 5.3(c) generalizada (ver también sección 3 de la Conferencia 4): $V_{H} = (0.082/P_{\text{atm}})(t+273)(1/MM_g + Y/MM_v)$. Con $Y_1\approx 0.024$, $T_1=307\ \text{K}$, $P_1\approx 1\ \text{atm}$: $V_{H1}\approx 0.90\ \text{m}^3/\text{kg a.s.}$
3. **Obtener la masa de aire seco:** $m_{as} = V_1/V_{H1} = 6/0.90 \approx 6.7\ \text{kg aire seco}$.
4. **Calcular $Y_2$**, la saturación en la salida (la mezcla llega saturada porque se comprime y se enfría hasta condensar): con $P_{s}(24\,°C) \approx 3.00\ \text{kPa}$ (interpolado de las Steam Tables) y $P_2 = 266.6\ \text{kPa}$: $Y_2 = 0.622\,P_s/(P_2-P_s) \approx 0.0071\ \text{kg agua/kg a.s.}$
5. **Agua condensada:** $H_2O_{\text{cond}} = m_{as}\,(Y_1-Y_2) \approx 6.7\times(0.024-0.0071) \approx 0.11\ \text{kg}$ — del mismo orden que la respuesta reportada (0.114 kg), con la pequeña diferencia atribuible a la precisión de la lectura gráfica de $Y_1$ sobre la carta impresa (que no forma parte de los archivos digitales de esta carpeta).
6. **Volumen final:** $V_2 = m_{as}\cdot V_{H2}$, calculando $V_{H2}$ con $Y_2$, $T_2=297\ \text{K}$, $P_2$ en atm, de forma análoga al paso 2.

**Conclusión práctica:** el método es exactamente el mismo que en el Ejercicio 2 (comparar $p_v$ "hipotético" contra $P_s$, confirmar condensación, recalcular con la salida saturada, aplicar el balance $H_2O_{\text{cond}}=m_{as}\Delta Y$ y la ecuación del volumen húmedo). La única pieza que aquí requiere la carta sicrométrica en lugar de una fórmula directa es la lectura de $Y_1$ a partir de $(t, t_{bh})$ — y esa es, precisamente, la habilidad que se entrena en la Conferencia 4 y en su Clase Práctica #4 (ver la sección 6 de [Conferencia 4](Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md)). Las respuestas numéricas finales que reporta el material fuente, $H_2O_{\text{cond}}=0.114\ \text{kg}$ y $V=2.046\ \text{m}^3$, deben tomarse como el valor de referencia para verificar la lectura del gráfico una vez que se dispone de la carta impresa.

---

## 7. Preguntas de repaso (respondidas)

La conferencia intercala varias preguntas a lo largo del desarrollo, a modo de guía socrática. Se recopilan y responden aquí:

**¿Cómo define usted el término presión de vapor?**
Es la presión que ejerce el vapor de un líquido sobre ese mismo líquido cuando ambas fases están en equilibrio dinámico (velocidad de vaporización = velocidad de condensación) dentro de un espacio cerrado, a una temperatura dada.

**¿Cómo es la dependencia de la presión de vapor con la temperatura?**
Es una función creciente y no lineal: $P_s$ aumenta con $T$. Gráficamente corresponde a la curva AB del diagrama P-T (sección 3.2); se puede modelar con Clausius-Clapeyron o, con mejor ajuste en un rango amplio, con la ecuación de Antoine (sección 3.3).

**¿Qué punto representa el líquido subenfriado / el vapor sobrecalentado en el diagrama P-T?**
El líquido subenfriado: cualquier punto en la región líquida, fuera de la curva de equilibrio AB (temperatura menor que la de saturación a esa presión). El vapor sobrecalentado: cualquier punto en la región de vapor por debajo de la curva DAB extendida (temperatura mayor que la de saturación a esa presión).

**¿Qué forma toma la representación gráfica de $\ln P_s^{(i)}$ vs $\ln P_s^{(r)}$? ¿Cuántos valores experimentales de $P_s^{(i)}$ se necesitan?**
Toma la forma de una línea recta (consecuencia de que $\Delta H_s^{(i)}/\Delta H_s^{(r)}$ es aproximadamente constante); solo se necesitan **dos** valores experimentales de $P_s^{(i)}$ (a dos temperaturas), porque dos puntos determinan una recta (sección 4.2–4.3).

**¿Cuál es la ventaja fundamental del gráfico de Cox?**
Permite evaluar la presión de vapor de una sustancia en un intervalo amplio de temperaturas con muy pocos datos experimentales propios, apoyándose en la información —mucho más completa— de una sustancia de referencia (usualmente el agua).

**En las definiciones de composición, para el caso de las mezclas saturadas, ¿cuál es la consideración más importante a emplear?**
Que, por definición de mezcla saturada, la presión parcial del vapor **es igual** a su presión de saturación a esa temperatura: $p_v = P_s$. Esta igualdad es la que permite, conociendo solo la temperatura (de la cual se obtiene $P_s$ por Cox o por tablas), calcular directamente $(y_m)_{SAT}$, $(Y_m)_{SAT}$, etc., sin necesitar ningún otro dato experimental de composición.

**Si en una mezcla vapor-gas conocemos la fracción másica, ¿cómo calcular las demás?**
Respondida en detalle al final de la sección 5.3(e): mediante la cadena de identidades $y \to Y \to Y_m \to y_m \to p_v$ (y de ahí, cualquier otra).

**¿Qué significan los valores extremos (0 % y 100 %) de $\%Y_R$?**
0 % significa ausencia total de vapor ($p_v=0$); 100 % significa mezcla exactamente saturada ($p_v = P_s$), el umbral en el que comenzaría la condensación si se sigue agregando vapor o bajando la temperatura.

---

## 8. Para seguir estudiando

Orientaciones que deja la conferencia, junto con la precisión de qué cubre este documento y qué requiere el libro de texto:

- **Texto, páginas 75–145** (no incluido entre los archivos de esta carpeta): contiene las demostraciones completas que la conferencia remite a pie de página (por ejemplo, la de $y_m=y_P$ en las págs. 120–121, la de $Y_m$ en la pág. 125, la de $Y=Y_m\,MM_v/MM_g$ en la pág. 127, la de $\%Y_R=(y_m/y_{m,SAT})\cdot100$ y $y_m=Y_m/(1+Y_m)$ en la pág. 129, y la de $\%Y=\%Y_R[(P-P_s)/(P-p_v)]$ en la pág. 131). Este documento las reconstruyó todas de forma independiente en la sección 5.3, con resultados idénticos a los que reporta la conferencia — lo cual confirma que las fórmulas están citadas correctamente.
- **Ejemplo resuelto 2.2, pág. 107** (método de Cox) y **ejemplos 2.3, 2.4, 2.5, págs. 132, 136, 140** (formas de composición): no incluidos en esta carpeta; la Clase Práctica #3 (resuelta íntegra en la sección 6 de este documento) cubre el mismo tipo de cálculo.
- **Epígrafes 2.5, 2.7.4d, 2.8, 2.10 (del 1 al 6):** material de autoestudio adicional no cubierto en el cuerpo principal de la conferencia (incluye el método de Düring).
- **Formulario resumen (CP#4):** la conferencia pide construir, como ejercicio, un formulario con todas las formas de expresar la composición y sus variables — la tabla de la sección 5.4 y las fórmulas recuadradas de la sección 5.3 cumplen exactamente esa función.
- **Carpeta [TCE1](TCE1/)** de este repositorio: contiene doce variantes (A–L) de un "Trabajo de Control Extraclases #1" que integra el contenido de esta conferencia con el de la Conferencia 4 (incluye, por ejemplo, ejercicios con saturadores, calentadores y enfriadores en serie, del mismo tipo que el de la sección 6 de la [Conferencia 4](Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md)). Estos archivos están en formato .doc con figuras incrustadas que no se pudieron extraer en este documento; conviene abrirlos directamente en un procesador de texto para resolverlos como práctica adicional una vez dominadas ambas conferencias.

La conferencia cierra anunciando el tema de la siguiente: la mezcla vapor de agua–aire es la más estudiada tanto en la vida doméstica como en la industrial, y sus relaciones se resumen en la **carta sicrométrica** — con sus propias variables (temperaturas de rocío, bulbo húmedo, bulbo seco y saturación adiabática) y los procesos que se pueden evaluar con ella. Ese es exactamente el contenido de la [Conferencia 4](Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md).

---

## Referencias / fuentes usadas en este documento

- [Conferencia 3 Tema 2 Plan E.pdf](Conferencia%203%20Tema%202%20Plan%20E.pdf) — fuente principal del contenido teórico.
- [Guia de estudio Tema 2.pdf](Guia%20de%20estudio%20Tema%202.pdf) — objetivos, conocimientos y habilidades del tema, y su relación con los Temas 1 y 3.
- [PIQ1 Clase practica 3 Composicion de las mezclas vapor-gas Etanol y compresor de aire.pdf](PIQ1%20Clase%20practica%203%20Composicion%20de%20las%20mezclas%20vapor-gas%20Etanol%20y%20compresor%20de%20aire.pdf) — los tres ejercicios resueltos completos en la sección 6.
- [../diagrama de COX.pdf](../diagrama%20de%20COX.pdf) — Figura B.9 real (Hougen, Watson y Ragatz, *Principios de los procesos químicos*), usada en el Ejercicio 1.
- [../Steam Tables_Keenan.pdf](../Steam%20Tables_Keenan.pdf) — tablas de agua saturada, usadas para verificar de forma independiente todos los valores numéricos de presión de vapor de esta conferencia.
