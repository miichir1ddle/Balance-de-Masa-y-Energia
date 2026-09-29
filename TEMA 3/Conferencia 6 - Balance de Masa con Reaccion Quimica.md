# Tema 3 — Conferencia 6: Balance de masa en procesos estacionarios con reacción química

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuente principal:** [Conferencia 6 Tema 3 Plan E.pdf](Conferencia%206%20Tema%203%20Plan%20E.pdf)
> **Apoyo:** [Guia de estudio Tema 3.pdf](Guia%20de%20estudio%20Tema%203.pdf) · [PIQ1 Clase practica 9 Reactor secador Reactor catalitico.pdf](PIQ1%20Clase%20practica%209%20Reactor%20secador%20Reactor%20catalitico.pdf) · [PIQ1 Clase practica 10 Reacciones de combustion Mezclador horno.pdf](PIQ1%20Clase%20practica%2010%20Reacciones%20de%20combustion%20Mezclador%20horno.pdf) · [PIQ1 Clases practicas 11 y 12 Planta de produccion de amoniaco.pdf](PIQ1%20Clases%20practicas%2011%20y%2012%20Planta%20de%20produccion%20de%20amoniaco.pdf) · [Conferencia 5 - Expresion General del Balance de Masa y Balance sin Reaccion Quimica.md](Conferencia%205%20-%20Expresion%20General%20del%20Balance%20de%20Masa%20y%20Balance%20sin%20Reaccion%20Quimica.md) (base de todo lo que sigue) · [Complementos/Autopreparacion Balance de masa crq.pdf](Complementos/Autopreparacion%20Balance%20de%20masa%20crq.pdf) · [Complementos/Variantes de PI (07-08).pdf](Complementos/Variantes%20de%20PI%20(07-08).pdf)
>
> Este documento explica, paso a paso y sin dar nada por sabido, todo lo que exige la Conferencia 6: la extensión del balance de masa a procesos con reacción química (balance por componente y balance por elemento), las definiciones de % de conversión y % de exceso, el cálculo de los grados de libertad en sistemas reaccionantes, y las particularidades del caso más importante en la práctica industrial — la combustión. Se resuelven completos los ejercicios de las Clases Prácticas #9, #10 y #11-12 (esta última, sobre una planta de producción de amoníaco con reciclo y purga, es el ejercicio integrador de cierre del tema), verificando toda la aritmética de forma independiente y corrigiendo las erratas numéricas detectadas.

---

## 0. Dónde estamos

Esta es la **segunda** conferencia del Tema 3 (Balance de masa) y se apoya enteramente en la [Conferencia 5](Conferencia%205%20-%20Expresion%20General%20del%20Balance%20de%20Masa%20y%20Balance%20sin%20Reaccion%20Quimica.md): mismo programa de análisis (interpretación → base de cálculo → grados de libertad → solución numérica → comprobación), misma ecuación general del balance de masa (deducida allí desde la ley de conservación de la materia), y aquí se retoman específicamente las dos expresiones particulares que ya se habían derivado para reactivo y producto (sección 2.4 de la Conferencia 5), que ahora se desarrollan en profundidad.

La introducción de la propia conferencia resume bien la motivación: los procesos con reacción química tienen una enorme importancia tecnológica (producción de H₂SO₄, de NH₃, de productos biológicos, etc.), y en la mayoría de ellos **el reactor es el equipo clave**: de cómo opere depende en gran medida la eficiencia y la economía de todo el proceso. Por eso es esencial poder cuantificar, a partir de lo que se alimenta a un reactor, la cantidad y concentración de los productos que se obtienen — y esa cuantificación es, precisamente, un balance de masa con reacción química.

---

## 1. Objetivo de la conferencia

Analizar la técnica del balance de masa en procesos estacionarios donde ocurren reacciones químicas.

---

## 2. La ecuación estequiométrica como punto de partida

A diferencia del balance sin reacción química, aquí **es imprescindible conocer la ecuación estequiométrica** de la reacción en cuestión, porque todos los cálculos se apoyan en ella. La propia conferencia lo ilustra con el caso de la obtención de H₂SO₄ a partir de azufre, donde ocurren reacciones en tres equipos distintos (horno de combustión de azufre, convertidor de SO₂ a SO₃, y el reactor final de absorción):

$$\text{SO}_3 + \text{H}_2\text{O} \longleftrightarrow \text{H}_2\text{SO}_4$$

De esta ecuación se observa que 1 mol de SO₃ + 1 mol de H₂O (2 moles totales) producen 1 mol de H₂SO₄ (1 mol total). **¿Hay conservación molar en un proceso con reacción química?** No — el número total de moles cambia (2 moles de reactivos dan 1 mol de producto, en este ejemplo). Sin embargo, el **balance total másico sí se cumple siempre**, porque la masa ni se crea ni se destruye: 18 g de H₂O reaccionan con 80 g de SO₃ y dan exactamente 98 g de H₂SO₄ (18+80=98, la masa se conserva aunque los moles no).

Esta distinción —conservación de la masa sí, conservación molar no, en general— es la que obliga a elegir con cuidado cómo plantear el balance.

---

## 3. Dos formas de plantear el balance: por elemento o por componente

### 3.1 Balance por elementos

Se basa en que los **átomos** que componen las sustancias se mantienen constantes en la reacción: producto de la transformación química, los átomos simplemente "pasan" de formar parte de una sustancia a formar parte de otra, pero su cantidad total no cambia. Para el ejemplo del H₂SO₄:

$$\left[\text{Cantidad de Hidrógeno que entra al reactor}\right] = \left[\text{Cantidad de Hidrógeno que sale del reactor}\right]$$

Este tipo de balance **puede resultar más laborioso de plantear**, pero a veces es la **única vía posible**: por ejemplo, cuando se trata de reacciones múltiples o complejas cuya estequiometría exacta no se conoce (como ocurre en la sección 9.2 de este documento, con la deshidrogenación catalítica del propano, o en la combustión de combustibles sólidos o líquidos de composición variable — sección 6).

### 3.2 Balance por componente (sustancias)

Se plantea directamente sobre las sustancias que reaccionan o se forman, retomando las ecuaciones ya derivadas en la [Conferencia 5](Conferencia%205%20-%20Expresion%20General%20del%20Balance%20de%20Masa%20y%20Balance%20sin%20Reaccion%20Quimica.md#24-caso-b-procesos-estacionarios-con-reacción-química-bm-crq--anticipo):

$$\textbf{Para un reactivo:}\qquad \left[\text{entra}\right] = \left[\text{sale}\right] + \left[\text{reacciona}\right]$$

$$\textbf{Para un producto:}\qquad \left[\text{sale}\right] = \left[\text{entra}\right] + \left[\text{forma}\right]$$

Este es el tipo de balance **que más se emplea en la práctica**, expresado en términos **molares** para poder aprovechar directamente las relaciones estequiométricas (la razón de los coeficientes en la ecuación química balanceada). Es el que se usa en la inmensa mayoría de los ejercicios de este tema.

**Resumiendo:** en un proceso con reacción química hace falta conocer la ecuación estequiométrica y aplicar, sobre ella, balances de elemento o balances de sustancia (reactivos y/o productos), recordando siempre que el balance molar global **no** se conserva en general (aunque el másico sí).

### 3.3 La "tabla de balance": una herramienta que se repite en todos los ejercicios

En los ejercicios resueltos de este tema (secciones 7-9) aparece sistemáticamente una tabla de cuatro columnas que organiza visualmente el balance por componente:

| Compuesto | Entra | Reacciona | Forma | Sale |
|---|---|---|---|---|

Para un **reactivo**: Sale = Entra − Reacciona. Para un **producto**: Sale = Entra + Forma (con Entra = 0 si el producto no viene ya en la alimentación). Para un **inerte** (que ni reacciona ni se forma): Sale = Entra. Esta tabla, aunque no aparece formalizada explícitamente como tal en el texto de la conferencia, es la forma más clara de aplicar de manera sistemática las dos ecuaciones de la sección 3.2, y se usa en todos los ejercicios resueltos más adelante.

---

## 4. Reactivo limitante, % de conversión y % de exceso

### 4.1 Reactivo limitante

Cuando una reacción involucra dos (o más) reactivos, no siempre se alimentan en la proporción estequiométrica exacta. El **reactivo limitante** es aquel que, dadas las cantidades realmente alimentadas de cada reactivo, se agotaría primero si la reacción fuera completa — es decir, el que determina cuánto puede avanzar la reacción. Para identificarlo se compara, para cada reactivo, la cantidad alimentada dividida entre su coeficiente estequiométrico: el que dé el valor **menor** es el limitante (se desarrolla con un ejemplo numérico completo en la sección 7).

### 4.2 % de Conversión

No toda la cantidad de reactivo alimentada se convierte necesariamente en producto: puede haber mala operación, poco tiempo de residencia, condiciones que no favorecen que reaccione todo el reactivo, etc. Se define el **% de conversión** (o simplemente conversión, $x$) como la fracción del reactivo que efectivamente reacciona, respecto de la cantidad total de ese reactivo alimentada al proceso:

$$\%\text{Conversión} = \dfrac{\text{Cantidad de reactivo que reacciona}}{\text{Cantidad total de reactivo alimentado}}\times 100 = \dfrac{(\text{Cant. que entra} - \text{Cant. que sale})\ \text{del reactivo}}{\text{Cantidad total de reactivo alimentado}}\times 100$$

**Importante:** el % de conversión **no se define para cada reactivo por separado**, sino específicamente para el **Reactivo Limitante**. Los valores extremos: $x=0\%$ significa que no reacciona nada del reactivo limitante (el reactor no está funcionando); $x=100\%$ significa que se consume por completo — el límite superior teórico ideal.

### 4.3 % de Exceso

Cuando hay dos reactivos y uno de ellos es el limitante, el otro está necesariamente en **exceso**. La cantidad del reactivo en exceso que sería exactamente necesaria para consumir por completo al reactivo limitante se llama **cantidad estequiométrica** (o "reactivo teórico"). Puede ocurrir que, además de esa cantidad estequiométrica, la corriente que entra al reactor traiga una cantidad **adicional** del reactivo en exceso — el "reactivo que acompaña al limitante":

$$\left[\text{Cantidad teórica}\right] = \left[\text{Cantidad Estequiométrica}\right] + \left[\text{Cantidad del reactivo que acompaña al limitante}\right]$$

$$\%\text{Exceso} = \dfrac{\text{Cantidad alimentada} - \text{Cantidad teórica}}{\text{Cantidad teórica}}\times 100$$

**¿Qué sucede si no hay reactivo en exceso, además del limitante?** El % de exceso es 0 — se alimentó exactamente la cantidad teórica (estequiométrica) del otro reactivo, ni más ni menos.

**¿Qué significa que la reacción se conduzca con un 20 % de exceso?** Que se alimenta un 20 % más del reactivo no limitante de lo que sería estrictamente necesario, en base estequiométrica, para consumir todo el reactivo limitante — un margen de seguridad habitual en la práctica industrial para favorecer que la conversión del reactivo limitante sea alta.

> Existe también la definición de **rendimiento**, de menor importancia relativa dentro de esta conferencia y que el propio material remite al texto (Tomo I, pág. 296) sin desarrollarla aquí.

### 4.4 Ejemplo guiado de la propia conferencia: reactor de obtención de SO₃

**Enunciado:** para el reactor $\text{SO}_2(g) + \tfrac{1}{2}\text{O}_2(g) \leftrightarrow \text{SO}_3(g)$, alimentado con SO₂ puro y aire seco, y con productos de composición molar $\text{SO}_2=5.41\%$, $\text{O}_2=6.77\%$, $\text{SO}_3=21.65\%$, $\text{N}_2=66.17\%$, calcular el % de conversión y el % de exceso.

**Grados de libertad** (BC aún no fijada): 8 incógnitas (7 componentes no definidos en masa en las corrientes de entrada y salida: $\text{SO}_{2(1)}, \text{O}_{2(2)}, \text{N}_{2(2)}, \text{SO}_{2(3)}, \text{O}_{2(3)}, \text{N}_{2(3)}, \text{SO}_{3(3)}$, más 1 incógnita adicional por la conversión) frente a 7 ecuaciones (4 EPB: SO₂, O₂, N₂, SO₃; más 3 composiciones/cantidades definidas de forma independiente). $V=7-8=-1$: no tiene solución sin fijar una base de cálculo.

**Base de cálculo: 100 kmol de productos** (se toma esta corriente por ser la de mayor información disponible).

$$\text{SO}_{3\ \text{sale}} = \text{SO}_{3\ \text{formado}} = 100(0.2165) = 21.65\ \text{kmol}$$

$$\text{SO}_{2\ \text{reacc}} = 21.65\ \text{kmol SO}_3\left(\dfrac{1\ \text{SO}_2}{1\ \text{SO}_3}\right) = 21.65\ \text{kmol}\qquad\Rightarrow\qquad \text{SO}_{2\ \text{entra}} = 100(0.0541)+21.65 = 27.06\ \text{kmol}$$

$$\text{O}_{2\ \text{entra}} = 100(0.0677) + 21.65\ \text{kmol SO}_3\left(\dfrac{\tfrac{1}{2}\text{O}_2}{1\ \text{SO}_3}\right) = 6.77+10.825 = 17.60\ \text{kmol}$$

**Determinación del reactivo limitante** (comparando lo alimentado de cada reactivo dividido entre su coeficiente estequiométrico — la magnitud más pequeña señala al limitante):

$$\dfrac{27.06\ \text{kmol SO}_2}{1} = 27.06 \qquad\text{vs.}\qquad \dfrac{17.60\ \text{kmol O}_2}{1/2} = 35.2$$

Como $27.06 < 35.2$: **el SO₂ es el reactivo limitante; el O₂ está en exceso.**

$$\%\text{Conversión} = \dfrac{\text{SO}_{2\ \text{reacc}}}{\text{SO}_{2\ \text{entra}}}\times 100 = \dfrac{21.65}{27.06}\times 100 = 80.0\%$$

$$\text{O}_{2\ \text{teórico}} = \text{O}_{2\ \text{estequiométrico}} = 27.06\ \text{kmol SO}_2\left(\dfrac{\tfrac{1}{2}\text{O}_2}{1\ \text{SO}_2}\right) = 13.53\ \text{kmol}$$

$$\%\text{Exceso} = \dfrac{17.60-13.53}{13.53}\times 100 = 30.1\%$$

$$\boxed{\%\text{Conversión} = 80\%\,,\qquad \%\text{Exceso de O}_2 = 30.1\%}$$

**% de exceso en términos de aire.** El ejercicio plantea además demostrar que el % de exceso, calculado en términos de O₂, es idéntico al calculado en términos de aire seco (ya que el aire tiene una fracción fija de O₂, 21 % molar):

$$m_{\text{aire seco}} = \dfrac{m_{O_2}}{0.21}\qquad\Rightarrow\qquad \%\text{Exceso}_{\text{aire}} = \left[\dfrac{O_{2\ entra}/0.21 - O_{2\ teo}/0.21}{O_{2\ teo}/0.21}\right]\times 100$$

Sacando 0.21 como factor común (aparece igual en los tres términos) y simplificando, el 0.21 se **cancela por completo**:

$$\boxed{\%\text{Exceso}_{\text{aire}} = \dfrac{O_{2\ entra}-O_{2\ teo}}{O_{2\ teo}}\times 100 = \%\text{Exceso}_{O_2}}$$

Este resultado —que el % de exceso es el mismo si se expresa en O₂ puro o en aire seco— es la razón por la cual, en la práctica industrial de combustión (sección 6), casi siempre se reporta el % de exceso directamente en términos de **aire**, sin necesidad de referirlo al O₂.

---

## 5. Grados de libertad en sistemas con reacción química

La ecuación general sigue siendo la misma de la [Conferencia 5](Conferencia%205%20-%20Expresion%20General%20del%20Balance%20de%20Masa%20y%20Balance%20sin%20Reaccion%20Quimica.md#41-definición-y-convenio-de-signos-de-este-curso): $V=\#\text{ELI}-\#\text{Incógnitas}$, pero ahora con dos ajustes propios de los sistemas reaccionantes:

$$\#\text{Incógnitas} = \left[\begin{array}{c}\text{tantos compuestos no definidos}\\\text{en masa en cada corriente}\end{array}\right] + \left[\begin{array}{c}\text{tantas relaciones de conversión}\\\text{como reacciones tenga el sistema}\end{array}\right]$$

$$\#\text{Ecuaciones Independientes} = \left[\begin{array}{c}\text{tantas como compuestos}\\\text{tenga el sistema}\end{array}\right] + \left[\begin{array}{c}\text{tantas composiciones o cantidades}\\\text{definidas independientes existan}\end{array}\right] + \left[\begin{array}{c}\text{tantas relaciones}\\\text{particulares existan}\end{array}\right]$$

En otras palabras: la conversión de cada reacción presente en el sistema **cuenta como una incógnita más** (salvo que sea un dato del problema, en cuyo caso no se cuenta), y el número de compuestos del sistema (reactivos y productos) juega el mismo papel que jugaban los "componentes" en el balance sin reacción química.

**Una particularidad importante, señalada explícitamente en la Clase Práctica #11-12:** en procesos con reacción química **no siempre existe una regla completamente general** para determinar los grados de libertad de cada subsistema posible — a diferencia del caso sin reacción, donde el conteo de EPB+ERC+ERE es mecánico. En particular, cuando en una corriente hay una o más sustancias **inertes** (que no participan en la reacción, como el CH₄ o el argón en una planta de amoníaco) cuyo flujo ni composición se conocen, se necesita contar con las **ecuaciones provenientes del balance de esos inertes** como ecuaciones restrictivas especiales adicionales — de lo contrario el sistema puede parecer no resoluble cuando en realidad sí lo es. Este punto se ilustra en detalle en la sección 9 de este documento.

**¿Cómo se interpreta que la varianza sea mayor, menor o igual a cero?** Exactamente igual que en la Conferencia 5 (sección 4.1 de ese documento): $V=0$ → solución única; $V<0$ → faltan datos (sobran incógnitas); $V>0$ → sobran ecuaciones (revisar redundancia o consistencia de los datos).

---

## 6. Particularidades del proceso de combustión

Aunque los aspectos teóricos del balance de masa con reacción química son totalmente generales, la **combustión** merece un tratamiento aparte por su enorme importancia práctica: está presente en casi la totalidad de los procesos tecnológicos (generación de energía, hornos, calderas, motores). Sus particularidades, resumidas en la Clase Práctica #10, son:

- El **combustible** es siempre el **reactivo limitante**, y generalmente se trabaja con (o se asume) 100 % de conversión del mismo.
- El **% de exceso** se define casi siempre para el **aire de combustión**, y solo ocasionalmente en términos de O₂ (como se demostró en la sección 4.4, ambos dan el mismo resultado numérico).
- Se define el **% de completamiento** como el porcentaje del combustible que reacciona produciendo **CO₂** (combustión completa), en vez de CO (combustión incompleta). Es un concepto distinto del % de conversión: la conversión mide cuánto combustible reaccionó *en total*; el completamiento mide, del combustible que sí reaccionó, qué fracción llegó hasta CO₂ en vez de quedarse en CO.
- Los **productos de la combustión** típicos son:

| Producto | Origen |
|---|---|
| CO₂ | Combustión **completa** del carbono del combustible |
| CO | Combustión **incompleta** del carbono del combustible |
| H₂O | Combustión del hidrógeno del combustible **+** agua que entra con el aire **+** vapor de atomización (si el combustible es líquido) **+** humedad que trae el propio combustible |
| O₂ | El que sobra, porque siempre hay un % de exceso |
| N₂ | **Elemento de correlación** del aire (no reacciona; ver también la sección 3.2-b de la Conferencia 5) |

- Con combustibles **gaseosos** (como en los ejercicios de este documento) es práctica común hacer el balance **por componentes**. Con combustibles **sólidos** (bagazo) o **líquidos** (petróleo), cuya composición exacta no siempre se conoce con precisión, el balance se hace generalmente **por elementos** (sección 3.1) — y ese caso, junto con el de la combustión de combustibles sólidos y líquidos en general, se deja para el Tema 4 (Balance de Energía), como aclara explícitamente la Clase Práctica #10 en sus conclusiones.

---

## 7. Ejercicios resueltos de la Clase Práctica #9

### 7.1 Ejercicio #1 — Neutralización de H₃PO₄ con NaOH, seguida de secado adiabático

**Enunciado:** al reactor entran H₃PO₄ (25 kmol/min) y NaOH (25 kmol/min), según $\text{H}_3\text{PO}_4+2\text{NaOH}=\text{Na}_2\text{HPO}_4+2\text{H}_2\text{O}$. Su producto se seca de forma adiabática con aire húmedo (18 900 m³/min a 40 °C, $\%Y_R=30\%$), y el aire sale a 25 °C. Si la conversión en el reactor es 80 %:
a) Calcular la composición de la mezcla a la salida del secado.
b) Calcular el % de exceso de H₃PO₄.

$$\text{H}_3\text{PO}_4(1) \to \boxed{\text{Reactor}} \xrightarrow{(3)} \boxed{\text{Secado Adiabático}} \to (6) \qquad \text{NaOH}(2) \uparrow \qquad \text{aire}(4) \uparrow \qquad (5)\ \text{aire, } 25°C \uparrow$$

**Grados de libertad en el reactor.** Incógnitas: $F_3, x_{H_3PO_4(3)}, x_{NaOH(3)}, x_{Na_2HPO_4(3)}, x_{H_2O(3)}$ (5; la conversión **no** cuenta como incógnita porque es un dato del enunciado). Ecuaciones: 4 EPB (H₃PO₄, NaOH, Na₂HPO₄, H₂O) + 1 ERC (la de la corriente 3) = 5. $V=5-5=0$: tiene solución. BC = 1 min.

**Determinación del reactivo limitante:** entran 25 kmol de H₃PO₄ y 25 kmol de NaOH; la reacción consume 2 mol NaOH por cada mol de H₃PO₄, así que para agotar los 25 kmol de H₃PO₄ harían falta 50 kmol de NaOH — pero solo hay 25 kmol. Por tanto el **NaOH es el limitante** y el H₃PO₄ está en exceso.

**Tabla de balance** (con NaOH reacc = $0.8\times 25=20$ kmol, por dato de conversión 80 %):

| Compuesto | Entra | Reacciona | Forma | Sale |
|---|---|---|---|---|
| NaOH | 25 | 20 | – | 5 |
| H₃PO₄ | 25 | $20\left(\tfrac{1}{2}\right)=10$ | – | 15 |
| H₂O | – | – | $20\left(\tfrac{2}{2}\right)=20$ | 20 |
| Na₂HPO₄ | – | – | $20\left(\tfrac{1}{2}\right)=10$ | 10 |

**Agua evaporada en el secador**, con el flujo de aire húmedo convertido a moles y las humedades leídas en la carta sicrométrica ($Y_{40°C,30\%}=0.02$; $Y_{25°C}=0.014$, esta última correspondiente a la humedad de saturación adiabática a la que llega el aire a 25 °C):

$$n_{as} = \dfrac{18900\ \text{m}^3}{0.907\ \text{m}^3/\text{kg}}\times\dfrac{1\ \text{kmol}}{29\ \text{kg}} = 718.6\ \text{kmol}$$

$$\text{H}_2\text{O}_{evap} = 718.6\ \text{kmol}\left[(0.02-0.014)\dfrac{29}{18}\right]\dfrac{\text{kmol H}_2\text{O}}{\text{kmol}} \approx 7\ \text{kmol}$$

**Composición final (corriente 6):**

| | (3) kmol | (6) kmol | $x_i=(n_i/n_t)\times 100$ |
|---|---|---|---|
| H₃PO₄ | 15 | 15 | 34.9 % |
| NaOH | 5 | 5 | 11.6 % |
| H₂O | 20 | $20-7=13$ | 30.2 % |
| Na₂HPO₄ | 10 | 10 | 23.3 % |
| **Total** | | **43** | **100 %** |

**b) % de exceso de H₃PO₄:**

$$\text{H}_3\text{PO}_{4\ teórico} = \text{H}_3\text{PO}_{4\ estequiométrico} = 25\ \text{kmol}_{NaOH}\left(\dfrac{1\ \text{H}_3\text{PO}_4}{2\ \text{NaOH}}\right) = 12.5\ \text{kmol}$$

$$\%\text{Exceso} = \dfrac{25-12.5}{12.5}\times 100 = 100\%$$

$$\boxed{\text{Composición de (6): } 34.9\%\ \text{H}_3\text{PO}_4,\ 11.6\%\ \text{NaOH},\ 30.2\%\ \text{H}_2\text{O},\ 23.3\%\ \text{Na}_2\text{HPO}_4 \qquad \%\text{Exceso}=100\%}$$

**Interpretación:** un 100 % de exceso de H₃PO₄ significa que se alimentó **el doble** de la cantidad estequiométricamente necesaria (25 kmol alimentados frente a solo 12.5 kmol requeridos) — un exceso considerable, coherente con el hecho de que el NaOH resultó ser el reactivo limitante pese a que ambos se alimentaron en igual cantidad molar (25 y 25 kmol): la razón es que la estequiometría de la reacción no es 1:1, sino 1:2 (1 mol de H₃PO₄ por cada 2 de NaOH).

### 7.2 Ejercicio #2 — Deshidrogenación catalítica del propano (balance por elementos)

**Enunciado:** el propileno (C₃H₆) se produce por deshidrogenación catalítica del propano (C₃H₈), pero ocurren también varias reacciones paralelas que producen otros hidrocarburos, además de descomposición de carbón sobre la superficie del catalizador. Alimentando 58.2 kmol de C₃H₈ puro, y con la composición molar de salida dada (C₃H₈ = 45 %, C₃H₆ = 20 %, C₂H₆ = 6 %, C₂H₄ = 1 %, CH₄ = 3 %, H₂ = 25 %), calcular la cantidad de carbono que se deposita sobre el catalizador (corriente 3).

**¿Por qué debe ser un balance por elementos?** Porque, al haber varias reacciones paralelas simultáneas cuyas ecuaciones estequiométricas individuales no se conocen todas con precisión (solo se conoce la composición final de la mezcla de productos), es imposible plantear un balance por componente para cada reacción por separado. La única vía es un **balance elemental**: sobre el **Carbono** y el **Hidrógeno**, que se conservan como átomos sin importar cuántas reacciones distintas hayan ocurrido.

**Grados de libertad.** BC = 1 día. Incógnitas: $F_2$ (flujo de gases de salida) y $F_3$ (carbono depositado) — 2 incógnitas (la conversión no aparece como incógnita porque es, precisamente, un balance elemental, no uno de conversión). Ecuaciones: 2 EPB (una para C, una para H). $V=2-2=0$: tiene solución.

**¿Por cuál elemento empezar?** Conviene empezar por el **Hidrógeno**, porque el carbono depositado (corriente 3) no contiene H, así que esa corriente **desaparece** del balance de H, dejando una sola incógnita ($F_2$).

**Balance de H** ($\text{H}_{entra(1)}=\text{H}_{sale(2)}$, contando los átomos de H de cada especie por mol):

$$H_{entra} = 58.2\left(\dfrac{8}{1}\right) = 465.6\ \text{kmol H}$$

$$H_{sale} = F_2\Big[0.45(8)+0.20(6)+0.06(6)+0.01(4)+0.03(4)+0.25(2)\Big] = F_2(5.82)\ \text{kmol H}$$

$$465.6 = 5.82\,F_2 \quad\Rightarrow\quad \boxed{F_2 = \dfrac{465.6}{5.82} = 80\ \text{kmol/día}}$$

**Balance de C** (todos los compuestos de la lista contienen 3, 3, 2, 2 y 1 átomos de C respectivamente, y hay que sumar además el carbono depositado, $F_3$):

$$C_{entra(1)} = 58.2(3) = 174.6\ \text{kmol C}$$

$$C_{sale(2)} = 80\Big[0.45(3)+0.20(3)+0.06(2)+0.01(2)+0.03(1)\Big] = 80(2.12) = 169.6\ \text{kmol C}$$

$$\boxed{C_{sale(3)} = C_{entra(1)} - C_{sale(2)} = 174.6-169.6 = 5\ \text{kmol/día}}$$

**Este ejemplo ilustra perfectamente cuándo usar balance por elementos:** siempre que la red de reacciones sea demasiado compleja, desconocida, o involucre subproductos indeseados (como el depósito de carbono en un catalizador, un fenómeno de "coquización" muy común en reactores catalíticos industriales) para los que no existe una ecuación estequiométrica única y bien definida.

---

## 8. Ejercicio resuelto de la Clase Práctica #10 — Combustión de propano con mezclador y horno

### 8.1 El proceso

**Enunciado:** hay un proceso previo de enriquecimiento del combustible en un mezclador (corriente 1, 72.7 % C₃H₈ / 27.3 % N₂, se mezcla con C₃H₈ puro, corriente 2, para dar la corriente 3, 89.3 % C₃H₈ / 10.7 % N₂ — con 85 kmol/h de C₃H₈ puro alimentado por (2)), que luego entra a un horno junto con aire húmedo (25 % de exceso, 50 °C, $\%Y_R=75\%$), con las reacciones:

$$\text{C}_3\text{H}_8 + 5\text{O}_2 = 3\text{CO}_2+4\text{H}_2\text{O}\qquad(\text{I, combustión completa})\qquad \text{C}_3\text{H}_8+\tfrac{7}{2}\text{O}_2=3\text{CO}+4\text{H}_2\text{O}\qquad(\text{II, incompleta})$$

Con 100 % de conversión y 90 % de completamiento en el horno, calcular: a) el aire teórico; b) la composición molar de los gases de combustión; c) la temperatura de rocío de esos gases.

### 8.2 Parte (a): aire teórico

**Grados de libertad en el mezclador.** Incógnitas: $F_1, F_3$ (2). Ecuaciones: 2 EPB (C₃H₈, N₂). $V=2-2=0$. BC = 1 h.

$$F_1+F_2=F_3\,,\qquad 0.273\,F_1=0.107\,F_3 \;\Rightarrow\; F_1=0.392\,F_3$$

$$0.392\,F_3+F_2=F_3 \;\Rightarrow\; F_3=\dfrac{F_2}{1-0.392}=\dfrac{85}{0.608}=139.8\ \text{kmol/h}$$

$$\text{C}_3\text{H}_{8(3)} = 139.8(0.893) = 124.8\ \text{kmol/h}$$

Con 100 % de conversión, **todo** el propano alimentado al horno reacciona; el aire teórico es el estequiométricamente necesario para la combustión **completa** (reacción I, que es la referencia del "aire teórico"):

$$O_{2\ teórico} = 124.8\ \text{kmol C}_3\text{H}_8\left(\dfrac{5\ O_2}{1\ \text{C}_3\text{H}_8}\right) = 624\ \text{kmol}$$

$$\boxed{\text{aire teórico} = \dfrac{624}{0.21} = 2971.4\ \text{kmol/h}}$$

### 8.3 Parte (b): composición de los gases de combustión

Con el 25 % de exceso (dato del enunciado) aplicado sobre el O₂ teórico:

$$O_{2\ entra} = 624(1+0.25) = 780\ \text{kmol/h}$$

**Split de conversión según el % de completamiento (90 % vía reacción I, 10 % vía reacción II):**

$$\text{CO}_{2\ forma} = 124.8(0.9)\left(\dfrac{3\ \text{CO}_2}{1\ \text{C}_3\text{H}_8}\right) = 337.0\ \text{kmol}\,,\qquad \text{CO}_{forma} = 124.8(0.1)\left(\dfrac{3\ \text{CO}}{1\ \text{C}_3\text{H}_8}\right) = 37.4\ \text{kmol}$$

$$\text{H}_2\text{O}_{forma} = 124.8\left(\dfrac{4\ \text{H}_2\text{O}}{1\ \text{C}_3\text{H}_8}\right) = 499.2\ \text{kmol}\qquad(\text{4 H}_2\text{O por C}_3\text{H}_8\text{, igual en ambas reacciones})$$

$$O_{2\ reacc} = 124.8(0.9)(5) + 124.8(0.1)\left(\dfrac{7}{2}\right) = 561.6+43.68 = 605.3\ \text{kmol}\qquad\Rightarrow\qquad O_{2\ sale}=780-605.3=174.7\ \text{kmol}$$

**N₂**, elemento de correlación (entra con el aire y con la corriente 3):

$$N_{2\ entra} = 780\left(\dfrac{79}{21}\right)+139.8(0.107) = 2934.3+15.0 = 2949.2\ \text{kmol}$$

**Agua que entra con el aire húmedo** ($Y_{50°C,\%Y_R=75\%}=0.063$ kg H₂O/kg aire, leído de la carta sicrométrica):

$$H_2O_{entra} = 0.063\,\dfrac{29}{18}\times\dfrac{780}{0.21} = 0.063(1.6111)(3714.3) = 377\ \text{kmol}$$

$$H_2O_{sale} = H_2O_{entra}+H_2O_{forma} = 377+499.2 = 876.2\ \text{kmol}$$

**Tabla de balance completa** (kmol/h):

| Compuesto | Entra | Reacciona | Forma | Sale |
|---|---|---|---|---|
| C₃H₈ | 124.8 | 124.8 | – | – |
| O₂ | 780 | 605.3 | – | 174.7 |
| N₂ | 2949.2 | – | – | 2949.2 |
| H₂O | 377 | – | 499.2 | 876.2 |
| CO₂ | – | – | 337.0 | 337.0 |
| CO | – | – | 37.4 | 37.4 |

**Composición de la corriente de gases de combustión (5):**

| | kmol | % molar |
|---|---|---|
| O₂ | 174.7 | 3.99 |
| N₂ | 2949.2 | 67.42 |
| H₂O | 876.2 | 20.03 |
| CO₂ | 337.0 | 7.70 |
| CO | 37.4 | 0.86 |
| **Total** | **4374.5** | **100** |

$$\boxed{\text{aire teórico}=2971.4\ \text{kmol/h}\,;\qquad y_{O_2}=3.99\%,\ y_{N_2}=67.42\%,\ y_{H_2O}=20.03\%,\ y_{CO_2}=7.70\%,\ y_{CO}=0.86\%}$$

> **Nota de verificación:** el material fuente presenta dos erratas de transcripción aquí, detectadas y corregidas de forma independiente en este documento: (i) el nitrógeno de entrada al horno se imprime como "2949,2" en la ecuación pero como "2949,7" en la tabla resumen — el valor correcto es **2949.2** en ambos casos, porque N₂ es inerte (entra = sale) y porque la suma total de la corriente 5 (4374.5 kmol) solo cuadra exactamente usando 2949.2; (ii) el agua que entra con el aire húmedo se imprime como "337" en la ecuación de $H_2O_{sale}$, pero el valor correcto —coherente con el cálculo explícito de $H_2O_{entra}$ y con el total de 876.2 kmol— es **377** kmol ($377+499.2=876.2$; $337+499.2=836.2\neq 876.2$).

### 8.4 Parte (c): temperatura de rocío de los gases de combustión

El **punto de rocío** es la temperatura a la cual el vapor de agua presente en una mezcla gaseosa comienza a condensar al enfriarse dicha mezcla a presión constante — es decir, la temperatura de saturación correspondiente a la **presión parcial actual** del vapor de agua en la mezcla (concepto desarrollado con detalle en la [Conferencia 3 del Tema 2](../TEMA%202/Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md#32-el-diagrama-p-vs-t-de-una-sustancia-pura)).

$$\bar{P}_{H_2O} = P_{total}\cdot y_{H_2O} = 101.3\ \text{kPa}(0.2003) = 20.29\ \text{kPa} = 20.29\ \text{kPa}\times\dfrac{1\ \text{atm}}{101.3\ \text{kPa}}\times\dfrac{760\ \text{mmHg}}{1\ \text{atm}} = 152.2\ \text{mmHg}$$

Buscando en las tablas de vapor de agua (Perry) la temperatura de saturación correspondiente a esta presión:

$$\boxed{T_{rocío} = T_{sat}(152.2\ \text{mmHg}) = 60.5\ °C}$$

**Interpretación:** si estos gases de combustión se enfrían por debajo de 60.5 °C, comenzará a condensar agua líquida — un dato crítico en el diseño de ductos y equipos de recuperación de calor aguas abajo de un horno, para evitar corrosión por condensados ácidos (especialmente si el combustible contiene azufre).

---

## 9. Ejercicio resuelto de las Clases Prácticas #11 y #12 — Planta de producción de NH₃ (reciclo y purga)

Este es el ejercicio integrador de cierre del tema: combina mezclador, reactor catalítico, separador y una corriente de **purga** (una variante del desvío estudiado en la Conferencia 5, aquí aplicada a una corriente de **reciclo**), y exige distinguir cuidadosamente entre la **conversión de un solo paso por el reactor** y la **conversión global del proceso completo**.

### 9.1 El proceso y la estrategia general

**Enunciado:** una alimentación fresca de 74 % H₂, 24.5 % N₂, 1.2 % CH₄ y 0.3 % Ar (% molares) reacciona catalíticamente: $\text{N}_2(g)+3\text{H}_2(g)=2\text{NH}_3(g)$. La corriente de salida del reactor se recircula. Para evitar que el CH₄ y el Ar (inertes, que no reaccionan) se acumulen indefinidamente en el lazo de reciclo, se purga una fracción del gas reciclado. Datos de diseño: la alimentación **combinada** al reactor (fresca + reciclo) contiene 18 % de CH₄; en el reactor se convierte el 65 % del N₂ (por paso); el N₂ en la purga es el 1.51 % del N₂ alimentado al proceso (fresco). BC = 100 kmol de alimentación fresca (1).

$$\text{(1) Alimentación fresca} \to \underbrace{\bullet}_{\text{M}} \xrightarrow{(2)} \boxed{\text{Reactor catalítico}} \xrightarrow{(3)} \boxed{\text{Separador}} \to \begin{cases}\text{(4) NH}_3=47.81\ \text{kmol}\\ \text{(5)} \to \underbrace{\bullet}_{\text{D}} \to \begin{cases}\text{(6) Purga}\\ \text{(7) Reciclo} \to \text{regresa a M}\end{cases}\end{cases}$$

**Por qué en estos sistemas no siempre hay una regla mecánica para los grados de libertad (sección 5):** en cada posible subsistema (Mezclador, Reactor, Separador, Proceso completo) hay corrientes con inertes (CH₄, Ar) de composición o flujo desconocidos; las ecuaciones restrictivas especiales que provienen de sus balances (como "el CH₄ ni se forma ni reacciona") son indispensables para cerrar el sistema, y hay que identificarlas caso por caso — no existe una fórmula única que las genere automáticamente. Por eso, antes de intentar resolver ningún subsistema, conviene tabular los grados de libertad de **todos** los sistemas posibles y elegir, en cada etapa, el que dé $V=0$:

| | Mezclador | Reactor | Separador | Proceso |
|---|---|---|---|---|
| # Incógnitas | 11 | 11 | 12 | 7 |
| # EPB | 5 | 3 | 5 | 5 |
| # ERC | 2 | 2 | 2 | 1 |
| # ERE | 0 | 0 | 0 | 1 |
| **V** | **−4** | **−6** | **−5** | **0** |

**Solo el "Proceso completo" tiene $V=0$**: es el punto de partida obligado.

### 9.2 Paso 1 — Balance en el proceso completo

Las tres ecuaciones restrictivas disponibles a este nivel: los inertes (CH₄, Ar) entran solo por (1) y salen solo por la purga (6), sin cambiar (no reaccionan, y no hay otra salida para ellos que la purga, ya que el producto (4) es NH₃ puro):

$$\text{CH}_{4(1)}=\text{CH}_{4(6)}=0.012(100)=1.2\ \text{kmol}\qquad A_{(1)}=A_{(6)}=0.003(100)=0.3\ \text{kmol}\qquad N_{2(6)}=0.0151(24.5)=0.37\ \text{kmol}$$

**Reactivo limitante:** para 24.5 kmol de N₂ hacen falta $24.5\times 3=73.5$ kmol de H₂; hay 74 kmol disponibles → **el N₂ es el limitante**, el H₂ está ligeramente en exceso.

$$N_{2\ reacc}=N_{2\ entra}-N_{2\ sale}=24.5-0.37=24.13\ \text{kmol}$$

$$H_{2\ reacc}=24.13\left(\dfrac{3}{1}\right)=72.39\ \text{kmol}\qquad NH_{3\ forma}=24.13\left(\dfrac{2}{1}\right)=48.26\ \text{kmol}\qquad H_{2\ sale}=74-72.39=1.61\ \text{kmol}$$

Y como el NH₃ formado se reparte entre el producto (4, dato = 47.81 kmol) y lo que arrastra la purga:

$$NH_{3\ sale(6)}=48.26-47.81=0.45\ \text{kmol}$$

**Composición de la corriente de purga (6):**

| | kmol | % |
|---|---|---|
| H₂ | 1.61 | 40.97 |
| N₂ | 0.37 | 9.41 |
| NH₃ | 0.45 | 11.45 |
| Ar | 0.30 | 7.63 |
| CH₄ | 1.20 | 30.54 |
| **F₆** | **3.93** | **100** |

**Conversión global del proceso** (por el N₂, reactivo limitante, tomando como frontera todo el proceso):

$$\%\text{Conversión}_{proceso} = \dfrac{N_{2\ reacc}}{N_{2\ entra}}\times 100 = \dfrac{24.13}{24.5}\times 100 = 98.49\%$$

Como el punto de división (D) es solo un desvío mecánico (sección 6.1 de la Conferencia 5), las corrientes (5), (6) y (7) **comparten exactamente la misma composición** — solo difieren en el flujo total.

### 9.3 Paso 2 — Balance en el mezclador

Con las composiciones de (6)=(7) ya conocidas, se reanaliza la tabla de grados de libertad: ahora el **Mezclador** da $V=0$ (Reactor sigue en $V=-6$; Separador, en $V=-1$).

$$F_1\,x_{CH_4(1)}+F_7\,x_{CH_4(7)}=F_2\,x_{CH_4(2)}\qquad F_7(0.3054)=F_2(0.18)-100(0.012)\qquad(1)$$

$$F_1+F_7=F_2\qquad\Rightarrow\qquad F_7=F_2-100\qquad(2)$$

Sustituyendo (2) en (1): $0.3054(F_2-100)=0.18\,F_2-1.2 \;\Rightarrow\; 0.1254\,F_2=29.34 \;\Rightarrow\; \boxed{F_2=234\ \text{kmol}}\,,\qquad F_7=234-100=134\ \text{kmol}$

**Composición de (2)**, por balance de cada especie (p. ej., para el H₂: $x_{H_2(2)}=\dfrac{100(0.74)+134(0.4097)}{234}=0.5509$, y análogamente para N₂, NH₃ y Ar):

| | % |
|---|---|
| H₂ | 55.09 |
| N₂ | 15.86 |
| NH₃ | 6.56 |
| Ar | 4.49 |
| CH₄ | 18.00 |
| **F₂ = 234 kmol** | |

**Balance total en el divisor:** $F_5=F_6+F_7=3.93+134=137.93$ kmol (misma composición que (6) y (7)).

### 9.4 Paso 3 — Balance en el separador

Ahora el **Separador** da $V=0$ (el Reactor sigue en $V=-2$): es una separación sin reacción química, exactamente del tipo estudiado en la Conferencia 5.

$$F_3=F_4+F_5=47.81+137.93=185.74\ \text{kmol}$$

Por balance de cada componente (p. ej. H₂: $x_{H_2(3)}=\dfrac{137.93(0.4097)}{185.74}=0.3042$; análogo para los demás, y para NH₃ hay que sumar también el aporte de (4): $x_{NH_3(3)}=\dfrac{137.93(0.1145)+47.81}{185.74}=0.3424$):

| | % |
|---|---|
| H₂ | 30.42 |
| N₂ | 6.99 |
| NH₃ | 34.24 |
| Ar | 5.67 |
| CH₄ | 22.68 |
| **F₃ = 185.74 kmol** | |

### 9.5 Paso 4 — Cierre en el reactor: conversión de un solo paso y % de exceso

Con (2) y (3) ya completamente conocidos, se cierra finalmente el reactor **por diferencia**, sin necesidad de plantear un nuevo sistema de ecuaciones:

| Compuesto | Entra (2) | Reacciona | Forma | Sale (3) |
|---|---|---|---|---|
| H₂ | 128.91 | 72.41 | – | 56.5 |
| N₂ | 37.11 | 24.13 | – | 12.98 |
| NH₃ | 15.35 | – | 48.25 | 63.6 |
| CH₄ | 42.12 | – | – | 42.12 |
| Ar | 10.51 | – | – | 10.51 |

$$H_{2\ reacc}=128.91-56.5=72.41\ \text{kmol}\qquad N_{2\ reacc}=37.11-12.98=24.13\ \text{kmol}\qquad NH_{3\ forma}=63.6-15.35=48.25\ \text{kmol}$$

$$\boxed{\%\text{Conversión (un solo paso)} = \dfrac{N_{2\ reacc}}{N_{2\ entra(2)}}\times 100 = \dfrac{24.13}{37.11}\times 100 = 65.0\%}$$

**¡Coincide exactamente con el dato del enunciado ("se convierte en el reactor el 65 % del N₂")!** Este es un punto pedagógico central de todo el ejercicio: el 65 % de conversión por paso **no se usó como ecuación** en ningún momento de la solución (el sistema se cerró usando solo las restricciones de composición de CH₄, Ar y N₂ en la purga); su recuperación exacta al final, calculada de forma completamente independiente a partir de los balances ya resueltos, es una **comprobación numérica** de que toda la cadena de cálculo es internamente consistente — exactamente el paso (e) ("comprobación de los resultados") del programa de análisis de la Conferencia 5.

$$\%\text{Exceso de H}_2 = \dfrac{H_{2\ entra}-H_{2\ teórico}}{H_{2\ teórico}}\times 100\,,\qquad H_{2\ teórico}=N_{2(2)}\left(\dfrac{3}{1}\right)=37.11(3)=111.33\ \text{kmol}$$

$$\boxed{\%\text{Exceso} = \dfrac{128.91-111.33}{111.33}\times 100 = 15.8\%}$$

**Conclusión que resalta el propio material:** este ejercicio muestra con total claridad la **diferencia entre la conversión de un solo paso por el reactor (65 %) y la conversión global del proceso completo (98.49 %)**: gracias al reciclo, la mayor parte del N₂ que no reaccionó en su primer paso por el reactor **vuelve a tener oportunidad de reaccionar** en pasadas sucesivas, de modo que casi todo el N₂ fresco termina, tarde o temprano, convertido en NH₃ — y solo una pequeña fracción (1.51 %, por diseño) se pierde en la purga. Esta es precisamente la lógica que hace económicamente viables los procesos industriales de síntesis con reactivos costosos y conversiones de equilibrio bajas por paso (como la síntesis de amoníaco real, el proceso Haber-Bosch, en el que la conversión de equilibrio por paso ronda apenas el 15-20 %, y es el reciclo el que permite conversiones globales cercanas al 98-99 %).

**Trabajo independiente propuesto:** verificar que la composición de la corriente (3) se puede obtener también resolviendo primero el balance en el punto divisor y después en el separador (ya realizado aquí, en ese mismo orden, en las secciones 9.3-9.4), y comprobar el balance total en unidades másicas en el reactor — ejercicio de verificación que queda para el lector, siguiendo exactamente el mismo patrón usado en el resto del documento (traducir moles a masa multiplicando por la masa molar de cada especie, y comprobar que la masa total que entra al reactor en (2) es igual a la que sale en (3), ya que —a diferencia de los moles— la masa total sí se conserva en toda reacción química, como se estableció en la sección 2).

---

## 10. Preguntas de repaso (respondidas)

**¿Hay siempre conservación molar en un proceso con reacción química?**
No. El número total de moles puede aumentar o disminuir según la estequiometría de la reacción (p. ej., 2 moles de reactivos → 1 mol de producto en la síntesis de H₂SO₄ a partir de SO₃ y H₂O). Lo que **sí** se conserva siempre es la **masa total**.

**¿Cómo se expresa la ecuación de balance del SO₃? ¿Y la del H₂SO₄?**
Para el reactivo SO₃ (que se consume): $[\text{entra}]=[\text{sale}]+[\text{reacciona}]$. Para el producto H₂SO₄ (que se forma): $[\text{sale}]=[\text{entra}]+[\text{forma}]$.

**¿Qué valores extremos toma la conversión y qué interpretación tienen?**
0 % (no reacciona nada del reactivo limitante) y 100 % (se consume por completo). Son los límites teóricos; en la práctica casi ningún reactor opera exactamente en ninguno de los dos extremos.

**¿Qué sucede si no hay reactivo en exceso con el limitante?**
El % de exceso es 0: se alimentó justo la cantidad estequiométrica del reactivo no limitante, ni más ni menos.

**¿Qué significa que la reacción se conduzca con un 20 % de exceso?**
Que se alimenta un 20 % más del reactivo no limitante de lo estrictamente necesario, en base estequiométrica, para consumir todo el reactivo limitante.

**¿Por qué en estos sistemas, de manera general, no es posible plantear el balance de masa total?**
Porque el balance de masa **total** (suma de todas las especies) no distingue entre reactivos y productos, y al no conservarse el número de moles (aunque sí la masa), un balance molar total sencillamente no es válido como ecuación independiente en presencia de reacción química — hay que trabajar componente por componente (o elemento por elemento), aplicando en cada caso la ecuación que corresponda (reactivo o producto), y solo la masa total (no los moles totales) se conserva de entrada a salida.

**¿Cómo se determina en una reacción cuál es el reactivo limitante?**
Se compara, para cada reactivo, la cantidad alimentada dividida entre su coeficiente estequiométrico en la reacción balanceada; el que dé el **valor menor** es el limitante (ver el ejemplo numérico completo de la sección 4.4 y de la sección 9.2).

---

## 11. Recursos complementarios para la Prueba Parcial

La [Guía de estudio del Tema 3](Guia%20de%20estudio%20Tema%203.pdf) recomienda explícitamente, una vez estudiadas todas las conferencias y clases prácticas, resolver **todos** los ejercicios de los documentos de autopreparación de la carpeta [Complementos](Complementos/), que integran los conocimientos de todo el tema y sientan además las bases para el estudio de los balances de energía del Tema 4.

### 11.1 Autopreparación — Balance de masa con reacción química

El documento [Autopreparacion Balance de masa crq.pdf](Complementos/Autopreparacion%20Balance%20de%20masa%20crq.pdf) trae **10 problemas** con respuesta numérica (sin solución desarrollada), del mismo estilo que los resueltos en las secciones 7-9 de este documento: reactores de oxidación de SH₂, de metano, de propano/pentano con horno y saturador adiabático (integrando Tema 2 y Tema 3), reactores en dos lechos catalíticos en serie, y — de particular interés porque son formalmente idénticos al ejercicio de la sección 9 de este documento — dos problemas con **reciclo y purga** (producción de yoduro de metilo, problema #7, y síntesis de metanol a partir de CO y H₂, problema #10). El propio documento marca los problemas #4, #7 y #10 como los de mayor dificultad, recomendando resolver primero los siete restantes.

### 11.2 Autopreparación — Balance de masa sin reacción química

El documento [Autopreparacion Balance de masa srq.pdf](Complementos/Autopreparacion%20Balance%20de%20masa%20srq.pdf) (referenciado también al cierre de la [Conferencia 5](Conferencia%205%20-%20Expresion%20General%20del%20Balance%20de%20Masa%20y%20Balance%20sin%20Reaccion%20Quimica.md#11-para-seguir-estudiando)) trae 6 problemas adicionales sin reacción química.

### 11.3 Variantes de la Prueba Intrasemestral (PI)

El documento [Variantes de PI (07-08).pdf](Complementos/Variantes%20de%20PI%20(07-08).pdf) contiene **6 variantes** de un mismo examen ya aplicado en cursos anteriores, todas sobre el **mismo proceso técnico**: combustión de etano ($\text{C}_2\text{H}_6+\tfrac{7}{2}\text{O}_2=2\text{CO}_2+3\text{H}_2\text{O}$ y $\text{C}_2\text{H}_6+\tfrac{5}{2}\text{O}_2=2\text{CO}+3\text{H}_2\text{O}$) en un horno alimentado con aire que primero se satura adiabáticamente y luego se calienta, seguido de un separador con condensador. Es un ejercicio particularmente valioso porque **integra explícitamente el Tema 2 completo** (saturador adiabático, carta sicrométrica, temperatura de rocío — ver la [Conferencia 4 del Tema 2](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md)) con el Tema 3 (conversión, completamiento, % de exceso, balance con reacción química), exactamente el tipo de problema integrador que puede aparecer en la Prueba Parcial. Las seis variantes comparten la misma respuesta numérica subyacente (los mismos flujos y composiciones), pero cada una da un subconjunto distinto de datos y pide calcular las demás — un excelente ejercicio de autoevaluación: %exceso=20 %, %conversión=95 %, %completamiento=90 %, con la corriente de gases finales (equivalente a 71.5 kmol/h) de composición molar N₂=58.39 %, H₂O=16.50 %, CO₂=13.43 %, O₂=8.32 %, CO=2.66 %, C₂H₆=0.7 %, y temperatura de rocío ≈ 54-56 °C según el punto exacto del proceso que se evalúe.

### 11.4 Complemento numérico: `ReacSO3.xls`

La carpeta `Complementos` incluye también una hoja de cálculo, `ReacSO3.xls`, con el mismo tipo de reactor de oxidación de SO₂ a SO₃ desarrollado en la sección 4.4 de este documento — útil para explorar cómo cambian el % de conversión y el % de exceso al variar la composición de los productos, sin tener que rehacer manualmente toda la aritmética.

---

## 12. Cierre del Tema 3 y transición al Tema 4

Con esta conferencia se completa el núcleo teórico del Tema 3: la Conferencia 5 estableció la expresión general del balance de masa y su aplicación sin reacción química (incluyendo desvíos y sistemas heterogéneos), y esta Conferencia 6 la extendió a sistemas con reacción química, con especial atención a la combustión y a los procesos con reciclo y purga. Las Clases Prácticas #9 a #12, resueltas íntegramente en este documento, cubren el espectro completo de dificultad del tema: desde un reactor simple de neutralización (CP9) hasta una planta con reciclo y purga (CP11-12).

Como señala la propia Guía de estudio, los cálculos de cantidades de reactivos y productos desarrollados aquí "dejan sentadas las bases" para el Tema 4: el **Balance de Energía**, donde exactamente los mismos flujos de materiales calculados mediante estas técnicas (composiciones, conversiones, flujos molares y másicos) servirán como punto de partida para calcular los flujos de calor asociados a cada proceso — incluyendo, como anticipa la Clase Práctica #10, el caso de la combustión de combustibles sólidos y líquidos, que por su relación directa con el cálculo de calores de combustión se trata con más naturalidad como parte del Tema 4 que del Tema 3.

---

## Referencias / fuentes usadas en este documento

- [Conferencia 6 Tema 3 Plan E.pdf](Conferencia%206%20Tema%203%20Plan%20E.pdf) — fuente principal del contenido teórico (secciones 2–6).
- [Guia de estudio Tema 3.pdf](Guia%20de%20estudio%20Tema%203.pdf) — conocimientos, objetivos y habilidades del tema completo, y recomendación de los materiales de autopreparación (sección 11).
- [PIQ1 Clase practica 9 Reactor secador Reactor catalitico.pdf](PIQ1%20Clase%20practica%209%20Reactor%20secador%20Reactor%20catalitico.pdf) — ejercicios resueltos en la sección 7.
- [PIQ1 Clase practica 10 Reacciones de combustion Mezclador horno.pdf](PIQ1%20Clase%20practica%2010%20Reacciones%20de%20combustion%20Mezclador%20horno.pdf) — ejercicio resuelto en la sección 8.
- [PIQ1 Clases practicas 11 y 12 Planta de produccion de amoniaco.pdf](PIQ1%20Clases%20practicas%2011%20y%2012%20Planta%20de%20produccion%20de%20amoniaco.pdf) — ejercicio integrador resuelto en la sección 9.
- [Conferencia 5 - Expresion General del Balance de Masa y Balance sin Reaccion Quimica.md](Conferencia%205%20-%20Expresion%20General%20del%20Balance%20de%20Masa%20y%20Balance%20sin%20Reaccion%20Quimica.md) — base teórica común (ecuación general del balance, programa de análisis, grados de libertad, desvío/reciclo).
- [../TEMA 2/Conferencia 3 - Presion de Vapor y Composicion de Mezclas Vapor-Gas.md](../TEMA%202/Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md) y [../TEMA 2/Conferencia 4 - Mediciones Termometricas, Carta Sicrometrica y Procesos.md](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md) — punto de rocío y carta sicrométrica, usados en las secciones 7 y 8.
- [Complementos/Autopreparacion Balance de masa crq.pdf](Complementos/Autopreparacion%20Balance%20de%20masa%20crq.pdf) y [Complementos/Variantes de PI (07-08).pdf](Complementos/Variantes%20de%20PI%20(07-08).pdf) — material adicional de autopreparación, referenciado en la sección 11.
