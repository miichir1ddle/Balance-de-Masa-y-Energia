# Tema 2 — Conferencia 4: Mediciones termométricas, volumen húmedo, carta sicrométrica y procesos de vaporización-condensación

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuente principal:** [Conferencia 4 Tema 2 Plan E.pdf](Conferencia%204%20Tema%202%20Plan%20E.pdf)
> **Apoyo:** [Conferencia 3 - Presion de Vapor y Composicion de Mezclas Vapor-Gas.md](Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md) · [Guia de estudio Tema 2.pdf](Guia%20de%20estudio%20Tema%202.pdf) · [PIQ1 Clase practica 4 Procesos de vaporizacion y condensacion Saturador-Condensador-Calentadores.pdf](PIQ1%20Clase%20practica%204%20Procesos%20de%20vaporizacion%20y%20condensacion%20Saturador-Condensador-Calentadores.pdf) · [../Steam Tables_Keenan.pdf](../Steam%20Tables_Keenan.pdf) (usada para verificar los valores de $Y$ saturada)
>
> Este documento explica, paso a paso y sin dar nada por sabido, todo lo que exige la Conferencia 4: las cuatro mediciones termométricas asociadas a una mezcla vapor-gas (temperatura de rocío, de bulbo seco, de bulbo húmedo y de saturación adiabática), el volumen húmedo, la carta sicrométrica del sistema agua-aire y los cuatro procesos fundamentales de vaporización y condensación que se representan en ella. El ejercicio completo de la Clase Práctica #4 (saturador + condensador + dos calentadores en un mismo esquema) se resuelve aquí con cada paso justificado, y se verifica de forma independiente uno de sus datos clave contra las tablas de vapor.

---

## 0. Dónde estamos

Esta es la segunda y última de las dos conferencias del Tema 2 disponibles en esta carpeta. En la [Conferencia 3](Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md) se cubrió:

1. La diferencia entre vapor y gas ($T$ menor o mayor que la temperatura crítica).
2. Cómo evaluar la presión de vapor $P_s$ en función de $T$ (métodos analíticos y, sobre todo, el método gráfico de Cox con sustancias de referencia).
3. Las siete formas de expresar la composición de una mezcla vapor-gas (fracción molar/presión, fracción másica, masa de vapor por volumen, saturación molar, saturación, % saturación relativa y % saturación), agrupadas según tomen como base el total de la mezcla, el gas libre de vapor, o el grado de saturación.

Esta Conferencia 4 da el paso siguiente: **particulariza todo lo anterior al caso más estudiado, la mezcla vapor de agua–aire**, introduce las temperaturas que se miden con termómetros reales (no solo se calculan), construye con ellas la **carta sicrométrica** (una herramienta gráfica que resuelve visualmente lo que en la Conferencia 3 se resolvía algebraicamente), y clasifica los procesos industriales típicos donde esta mezcla cambia de estado.

**Nota metodológica de la propia conferencia:** antes de comenzar el desarrollo teórico, se indica preparar una experiencia práctica en el aula para medir con termómetros reales la temperatura de bulbo seco y la de bulbo húmedo — es decir, esta conferencia tiene un componente experimental explícito, pensado para palpar físicamente los conceptos antes de formalizarlos.

---

## 1. Objetivos de la conferencia

- Conocer las **definiciones termométricas** relacionadas con mezclas vapor-gas.
- Interpretar la **carta o diagrama sicrométrico**.
- Conocer los principales **procesos de vaporización y condensación** de una mezcla vapor-gas.

---

## 2. Mediciones termométricas

La idea central de esta sección es que, además de los cálculos algebraicos vistos en la Conferencia 3, existen **temperaturas específicas, medibles con instrumentos reales**, que caracterizan el estado de una mezcla vapor-gas. Se estudian cuatro: temperatura de rocío, de bulbo seco, de bulbo húmedo y de saturación adiabática.

### 2.1 Temperatura de rocío ($t_r$)

**Pregunta guía:** ¿qué le sucede a una mezcla vapor-gas parcialmente saturada cuando se somete a un **enfriamiento a presión total constante**?

Hay que recordar dos hechos ya establecidos:

- Cuando la temperatura disminuye, la presión de vapor $P_s$ **también disminuye** (sección 3 de la Conferencia 3: $P_s$ crece con $T$, así que al enfriar, baja).
- Por la ley de Dalton, la presión parcial del vapor es $p_i = y_i\,P$: si la **composición** de la mezcla no cambia (no se agrega ni se quita vapor) y la **presión total** tampoco cambia, entonces la presión parcial $p_v$ se mantiene constante durante el enfriamiento.

**Consecuencia:** a medida que la temperatura baja, $P_s$ disminuye mientras $p_v$ permanece fijo, así que la diferencia $(P_s - p_v)$ se va **cerrando**. La siguiente tabla (reconstruida de la secuencia de la conferencia, con 4 instantes de un enfriamiento progresivo) ilustra el proceso:

| Instante | Temperatura | Relación $P_s$ vs $p_v$ | Estado |
|---|---|---|---|
| 1 (inicio) | $T_1$ (mayor) | $P_{s1} > p_{v1}$ | Mezcla parcialmente saturada |
| 2 | $T_2 < T_1$ | $P_{s2} > p_{v2}$, pero la brecha es menor | Parcialmente saturada |
| 3 | $T_3 < T_2$ | $P_{s3} > p_{v3}$, brecha aún menor | Parcialmente saturada |
| 4 (final) | $T_4 < T_3$ | $P_{s4} = p_{v4}$ | **Mezcla saturada** (aparece la primera gota de líquido) |

**Definición:** la temperatura a la cual la mezcla se convierte en saturada, producto de un enfriamiento a presión constante y **sin contacto con ningún líquido**, se llama **temperatura de rocío** ($t_r$). Es función de la composición de la mezcla, de la naturaleza del vapor y de la presión — pero **no depende** de la temperatura a la que se encuentre inicialmente la mezcla (es una propiedad fija de "esa composición a esa presión").

**¿Varía el grado de saturación de la mezcla durante este proceso?** No en términos de composición (la cantidad de vapor por unidad de gas, $Y_m$, se mantiene constante hasta el instante 4, porque no se agrega ni se quita vapor); lo que sí cambia continuamente es el **% de saturación relativa** $\%Y_R$, que va aumentando hasta llegar a 100 % exactamente quo en $t_r$.

**Procedimiento para calcular $t_r$ (tres pasos):**

1. Calcular la **presión parcial del vapor** en la mezcla (el procedimiento exacto depende de cómo se conozca la composición — usar cualquiera de las relaciones de la Conferencia 3, sección 5.3).
2. **Igualar** esa presión parcial a la presión de vapor: $p_v = P_s(t_r)$.
3. Buscar, para ese compuesto, la **temperatura** a la que corresponde esa presión de vapor (con el método de Cox, con tablas, o con Antoine): esa temperatura es, por definición, $t_r$.

**Una vez conocida $t_r$, se puede recuperar la composición:** dado que $t_r$ determina unívocamente $P_s(t_r)$, y en el punto de rocío $p_v = P_s(t_r)$, se cumple:

$$Y_m = \frac{P_s(t_r)}{P - P_s(t_r)}$$

Es decir, **basta con medir $t_r$** (con un instrumento sencillo, como un espejo que se empaña) **para conocer la composición completa** de la mezcla — sin necesidad de un análisis químico directo. Esta es la "manera práctica de medir la temperatura de rocío" que la propia conferencia deja como pregunta abierta: enfriar una superficie hasta que se empañe (aparezca la primera gota de condensado) y leer su temperatura en ese instante.

### 2.2 Temperatura de bulbo seco ($t$) y de bulbo húmedo ($t_{bh}$)

**Temperatura de bulbo seco ($t$):** es, simplemente, la que mide un **termómetro ordinario**, con el bulbo expuesto directamente a la corriente gaseosa. Es la "temperatura" en el sentido cotidiano del término.

**Temperatura de bulbo húmedo ($t_{bh}$):** se mide envolviendo el bulbo del termómetro con una **mecha empapada en líquido** (de la misma naturaleza que el vapor de la mezcla) y exponiéndolo a la corriente gaseosa. Para que la medición sea válida deben cumplirse tres condiciones:

1. La cantidad de líquido debe ser **pequeña**, de modo que la saturación de la mezcla vapor-gas que lo rodea permanezca prácticamente constante (el líquido no debe "inundar" ni modificar significativamente la corriente).
2. La **temperatura inicial** de la mezcla y la del líquido deben ser **iguales**.
3. Debe haber **ausencia de fuente externa de calor**.

**Mecanismo físico de estabilización (por qué el termómetro húmedo marca una temperatura distinta al seco):**

1. Como la mezcla está parcialmente saturada, el líquido de la mecha comienza a **vaporizarse**, transfiriendo masa y calor hacia la mezcla. Como no hay fuente externa de calor, esa energía de vaporización sale **a expensas de la propia energía interna del líquido** — por eso su temperatura empieza a **descender**.
2. Al bajar la temperatura del líquido por debajo de la de la mezcla, se establece una **diferencia de temperaturas**, lo que provoca un **flujo de calor** desde la mezcla (más caliente) hacia el líquido (más frío).
3. En un tiempo finito, el flujo de calor que **entra** al líquido (desde la mezcla, por diferencia de temperatura) se **iguala** al flujo de calor que **sale** de él (consumido en vaporizar el líquido). Se alcanza un **equilibrio dinámico**: la temperatura del líquido se estabiliza. A esa temperatura de equilibrio se le llama **temperatura de bulbo húmedo** de la mezcla.

**¿Cuál es mayor, $t$ o $t_{bh}$, para una mezcla parcialmente saturada?** La de bulbo seco, $t$, siempre es **mayor**: $t_{bh} < t$ (el líquido se enfría por la vaporización). Y esa diferencia $(t - t_{bh})$ es **mayor cuanto menor es el grado de saturación** de la mezcla (mezclas más "secas" evaporan más líquido de la mecha, y se enfrían más).

### 2.3 Temperatura de saturación adiabática ($t_{sa}$)

Se considera ahora un caso relacionado pero distinto: una **cámara aislada térmicamente**, con la temperatura inicial del líquido igual a la de la mezcla que entra. La diferencia clave con el caso del bulbo húmedo es que aquí la **cantidad de líquido no es pequeña** — el contacto es prolongado y la vaporización es **significativa**, produciendo un **incremento real en la saturación** de la mezcla que sale (a diferencia del termómetro de bulbo húmedo, donde la saturación del entorno se mantenía prácticamente constante).

El **mecanismo de estabilización de la temperatura es idéntico** al del bulbo húmedo (vaporización → enfriamiento del líquido → flujo de calor → equilibrio dinámico). A la temperatura de equilibrio así alcanzada se le llama **temperatura de saturación adiabática** ($t_{sa}$) de la mezcla vapor-gas.

**¿Cómo sale la mezcla de la cámara si el contacto es prolongado?** Sale **saturada** a la temperatura $t_{sa}$ (con suficiente tiempo de contacto, el gas alcanza el equilibrio con el líquido a esa temperatura).

### 2.4 Relación entre las cuatro temperaturas

Este es un resultado central que hay que memorizar y entender, porque es la base de la construcción de la carta sicrométrica:

- **Caso general (cualquier mezcla vapor-gas):** $t_{sa} \le t_{bh}$ (la saturación adiabática, al involucrar más vaporización real, tiende a ser igual o menor que la de bulbo húmedo, salvo en el caso especial del agua).
- **Caso particular del sistema agua-aire:** se cumple exactamente $t_{bh} = t_{sa}$. Esta coincidencia (una casualidad numérica de las propiedades del agua-aire, no una ley general) es la que hace que la carta sicrométrica del agua-aire pueda representar ambas magnitudes con una sola familia de curvas, y es la razón física por la que el sistema agua-aire es, con diferencia, el más conveniente de tabular.

**Resumen completo (para mezclas parcialmente saturadas):**

$$t_{sa} < t_{bh} < t$$

y $t_r$ es única para cada composición dada (no se compara directamente con las otras tres en una desigualdad, porque depende de un proceso distinto — enfriamiento sin contacto con líquido, en vez de contacto con líquido).

**Para una mezcla saturada:** las cuatro coinciden exactamente:

$$t = t_{bh} = t_{sa} = t_r$$

(tiene sentido: si la mezcla ya está saturada, "enfriarla hasta saturarla" no requiere ningún cambio de temperatura, y poner líquido en contacto con ella tampoco provoca vaporización neta, así que ningún mecanismo de enfriamiento se activa).

---

## 3. Volumen húmedo ($V_H$)

### 3.1 Definición

El **volumen húmedo** es el volumen que ocupa la mezcla **por unidad de masa del gas** (no de la mezcla total) a una temperatura y presión dadas. Es una variable de gran trascendencia porque permite pasar de caudales volumétricos (lo que miden los instrumentos de planta, como un rotámetro o un venturi) a flujos másicos de gas seco (lo que se necesita para los balances de materia).

### 3.2 Fórmula y deducción

La conferencia da la fórmula sin demostrarla (remite a la página 157 del texto, no disponible en esta carpeta). Se reconstruye aquí la deducción completa, partiendo de la ecuación de gas ideal aplicada a **toda la mezcla** (vapor + gas juntos, que ocupan el mismo volumen $V$ a la misma $T$ y presión total $P$):

$$PV = n_T R T = (n_v+n_g)\,RT$$

Se quiere expresar esto por unidad de masa de **gas** ($m_g$), no de mezcla. Usando $Y = m_v/m_g$ (saturación, sección 5.3 de la Conferencia 3) y las masas molares:

$$n_v = \frac{m_v}{MM_v} = \frac{Y\,m_g}{MM_v} \qquad\qquad n_g = \frac{m_g}{MM_g}$$

Sustituyendo en $n_v+n_g$:

$$n_v + n_g = m_g\left(\frac{Y}{MM_v} + \frac{1}{MM_g}\right)$$

Sustituyendo de vuelta en $PV=(n_v+n_g)RT$ y dividiendo ambos lados entre $m_g$:

$$\frac{V}{m_g} = V_H = \frac{RT}{P}\left(\frac{1}{MM_g}+\frac{Y}{MM_v}\right)$$

Usando $R = 0.082\ \text{L·atm/(mol·K)}$, $P$ en atm y $T = (t+273)\ \text{K}$, y notando que $1\ \text{L/g} \equiv 1\ \text{m}^3/\text{kg}$ numéricamente, se llega exactamente a la fórmula de la conferencia:

$$\boxed{V_H = \frac{0.082}{P}\,(t+273)\left(\frac{1}{MM_G}+\frac{Y}{MM_V}\right)}$$

donde $P$ está en atm, $t$ en °C, $MM_G$ y $MM_V$ son las masas molares del gas y del vapor, $Y$ es la saturación (kg vapor/kg gas), y $V_H$ resulta en m³ de mezcla por **kg de gas** (no de mezcla total).

**Punto importante para no confundirse:** el volumen húmedo se define **por unidad de masa de gas seco**, no de mezcla total — igual que la saturación $Y$ y la saturación molar $Y_m$ de la Conferencia 3 (grupo 2, "base: el gas libre de vapor"). Esto es deliberado: en la mayoría de los procesos industriales (como se verá en la sección 5), el **flujo de gas seco se mantiene constante** de una corriente a otra (no se agrega ni se retira gas, solo vapor), así que referir todo a la masa de gas seco simplifica enormemente los balances.

---

## 4. Carta sicrométrica

### 4.1 Por qué se construye

Construir tablas y diagramas con las propiedades de un sistema es un trabajo importante del ingeniero químico: compacta la información y agiliza mucho las respuestas frente a resolver todo algebraicamente cada vez. Ese esfuerzo se justifica cuando un sistema se encuentra **con mucha frecuencia** en la práctica — y ese es exactamente el caso del sistema **vapor de agua–aire**, al que se le aplican los principios de la termometría estudiados arriba, dando lugar a una disciplina con nombre propio: la **sicrometría** (o higrometría). Su representación gráfica es la **carta sicrométrica**.

### 4.2 Construcción y características

- Se construye a **presión constante** de $101.3\ \text{kPa}$ (1 atm) — la presión atmosférica estándar, la condición más común en la práctica.
- El texto guía remite a dos versiones impresas: **Figura B-10** (válida hasta 45 °C) y **Figura B-11** (para $T>45\ \text{°C}$).
- El eje **horizontal** es la temperatura de bulbo seco $t$; el eje **vertical** es la **humedad** $Y$ (kg de H₂O por kg de aire seco).

**Curvas y elementos que contiene** (descripción de la figura del texto):

| Elemento | Qué representa |
|---|---|
| **Curva 100 % $Y_R$** | El límite de saturación: todo punto sobre ella es una mezcla exactamente saturada ($p_v=P_s$). |
| Región **por debajo** de esa curva | Mezclas **no saturadas** (cualquier punto en esa zona). |
| Rectas de **% $Y_R$** constante (curvas de humedad relativa) | Familias de curvas paralelas a la de saturación, para valores intermedios de humedad relativa. |
| Líneas de **$t_{bh}=t_{sa}$** constante | Para el sistema agua-aire, ambas coinciden (sección 2.4), así que es una sola familia de rectas de pendiente negativa que van desde la curva de saturación hacia temperaturas más altas y humedades más bajas. |
| Líneas de **$V_H$** constante | Otra familia de curvas, para leer el volumen húmedo directamente sin calcularlo con la fórmula de la sección 3.2. |
| $t_r$ | Se lee proyectando horizontalmente desde el punto de estado hacia la curva de saturación, y bajando verticalmente hasta el eje de temperatura — es decir, la temperatura de saturación que tiene la mezcla a **su misma humedad $Y$** (por eso $t_r$ y $Y$ forman un "par redundante": si se sabe uno del par, se sabe el otro, ver más abajo). |

**Propiedades del sistema agua-aire que resume la carta:**

- $t_{bh} = t_{sa}$ (ya visto).
- Las mezclas **saturadas** se ubican exactamente **sobre** la curva de 100 % $Y_R$.
- Cualquier punto **por debajo** de esa curva es una mezcla **no saturada**.

### 4.3 Grados de libertad: ¿cuántos datos hacen falta para fijar un punto?

**Pregunta que deja planteada la conferencia:** *¿será posible conocer la humedad y el $\%Y_R$ si se conocen $t$ y $t_{bh}$?* — Sí: como la presión está fija (101.3 kPa) en toda la carta, **basta con conocer dos condiciones cualesquiera** de la mezcla (por ejemplo, $t$ y $t_{bh}$, o $t$ y $\%Y_R$, o $t$ y $Y$) para ubicar un único punto en el diagrama, y de ahí leer directamente **todas las demás** propiedades (los cuatro tipos de temperatura, $Y$, $Y_m$, $\%Y_R$, $\%Y$, $V_H$).

**La única excepción** son las **parejas redundantes**: $(t_r, Y)$ y $(t_{bh}, t_{sa})$. Estas dos parejas **no** aportan información independiente entre sí (conocer $t_r$ ya implica conocer $Y$, y viceversa, según la relación de la sección 2.1; y para el sistema agua-aire $t_{bh}$ y $t_{sa}$ son literalmente el mismo número, sección 2.4). Por eso, si los dos datos que se dan son, por ejemplo, $t_r$ y $Y$, en realidad **solo se tiene un dato independiente** y el punto no queda determinado — hace falta un segundo dato genuinamente distinto (como $t$).

### 4.4 Extensión de la carta

Aunque está construida para 1 atm, la carta sicrométrica **puede emplearse para otras presiones bajo ciertas limitaciones**, y su uso puede extenderse a sistemas vapor-gas **distintos** del agua-aire (con las correcciones correspondientes). Este material es de autoestudio (páginas 168–175 del texto) y no se desarrolla más aquí por no ser parte del contenido central de la conferencia.

---

## 5. Procesos de vaporización y condensación

Con la carta ya construida, se pueden representar y analizar gráficamente los procesos industriales más comunes que sufre una mezcla vapor-gas. La clave para entender cada uno es identificar **qué variable se mantiene constante** durante el proceso (esto determina qué trayectoria sigue el punto de estado dentro de la carta) y luego deducir cómo cambian las demás.

### 5.1 Calentamiento

**Esquema:** una corriente de mezcla vapor-gas entra a un calentador a $t_1$ y sale a $t_2 > t_1$, sin que se agregue ni se retire líquido.

- **Como la operación ocurre en ausencia de líquido, la humedad $Y$ se mantiene constante** — no hay ni vaporización ni condensación, solo se le entrega calor sensible a la mezcla. En la carta, el proceso es un **desplazamiento horizontal** (a $Y$ constante) hacia temperaturas mayores.
- **Efecto sobre las demás variables:** $t$, $t_{bh}$ y $V_H$ **aumentan**; $\%Y_R$ **disminuye** (porque $P_s$ sube con $T$ mientras $p_v$ se mantiene fijo, alejando a la mezcla de la saturación); $t_r$ y $Y$ se **mantienen constantes** (son la pareja redundante ligada a la composición, que no cambia).

### 5.2 Enfriamiento (sin llegar a condensar)

Es, en esencia, el **proceso inverso** al calentamiento: la mezcla cede energía y su temperatura disminuye.

- **¿Se mantiene la humedad constante?** Sí — sigue sin haber contacto con líquido, así que $Y$ no cambia. En la carta es el mismo desplazamiento horizontal que el calentamiento, pero en sentido contrario (hacia $t$ menor).
- **¿Qué variables aumentan?** El $\%Y_R$ (la mezcla se acerca a la saturación a medida que $T$ baja y $P_s$ disminuye, mientras $p_v$ se mantiene fijo).
- **¿Qué variables disminuyen?** $t$, $t_{bh}$, $V_H$.
- **¿Se puede alcanzar la saturación?** Sí, si se enfría lo suficiente como para tocar la curva de 100 % $Y_R$ — ese punto de contacto es, precisamente, la temperatura de rocío $t_r$ de esa mezcla (coherente con la definición de la sección 2.1).

### 5.3 Condensación

**Punto de partida:** al llegar, por enfriamiento, al punto de mezcla saturada (es decir, se alcanzó $t_r$ — este primer tramo, del punto inicial hasta la saturación, es simplemente el "enfriamiento" de la sección 5.2). Una **disminución adicional** de temperatura, más allá de ese punto, hace que la presión parcial que "querría" ejercer el vapor supere a la presión de saturación, y esto obliga a que una parte del vapor **condense** (exactamente la misma lógica física que se usó para resolver el Ejercicio 2 de la Clase Práctica #3, en la [Conferencia 3](Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md), sección 6.2).

- **En la carta:** como la mezcla, una vez saturada, **permanece saturada** durante todo el resto del enfriamiento (el exceso de vapor condensa instantáneamente para mantener el equilibrio), el proceso sigue exactamente la **curva de 100 % $Y_R$** hacia temperaturas menores.
- **Efecto sobre las variables:** excepto $\%Y_R$, que permanece constante e igual al 100 % durante todo este tramo, el **resto de los parámetros disminuyen** ($t$, $t_r$, $t_{bh}$, $t_{sa}$, $V_H$, $Y$). Nótese que en este tramo **todas las temperaturas son iguales en cada punto** (porque la mezcla está saturada — recordar la sección 2.4: $t=t_{bh}=t_{sa}=t_r$ cuando hay saturación).
- **¿Es humidificación o deshumidificación?** **Deshumidificación**: el contenido de vapor $Y$ de la mezcla **disminuye** a medida que condensa.
- **Cálculo del agua condensada** (por unidad de masa de gas seco, entre el estado (1) de entrada y el (2) de salida):

$$H_2O_{\text{cond}} = Y_1 - Y_2 \qquad \left[\frac{\text{kg}\ H_2O}{\text{kg aire seco}}\right]$$

  Si se quiere expresar por **unidad de tiempo** (por ejemplo, kg/h), hace falta un dato adicional: el **flujo de aire seco** (en kg aire seco/h), de modo que $\dot{H_2O}_{\text{cond}} = \dot{m}_{as}\,(Y_1-Y_2)$.

### 5.4 Vaporización adiabática

Un ejemplo típico es el **secado de un sólido húmedo** en condiciones adiabáticas (el líquido está impregnado en el material que se seca), o el propio proceso descrito al definir $t_{sa}$ en la sección 2.3 (cámara aislada, gas en contacto prolongado con líquido).

- **Característica definitoria:** el proceso ocurre a **$t_{sa}$ constante**, que para la mezcla agua-aire equivale también a **$t_{bh}$ constante** (por la coincidencia $t_{bh}=t_{sa}$ ya explicada). En la carta, el proceso sigue exactamente las líneas de $t_{bh}=t_{sa}$ constante, que van desde el punto de entrada hasta la curva de saturación.
- **¿Qué variables aumentan?** $t_r$, $Y$, $\%Y_R$ (la mezcla se va acercando a la saturación, ganando contenido de vapor).
- **¿Qué variables disminuyen?** $t$ (la mezcla se enfría, porque el calor sensible que cede se usa para vaporizar el líquido — el mismo mecanismo del bulbo húmedo, sección 2.2, pero ahora con vaporización significativa).
- **¿Qué se mantiene constante?** $t_{sa}$ y $t_{bh}$.
- **¿Es humidificación o deshumidificación?** Como hay un **incremento de la saturación**, es un proceso de **humidificación**.
- **Cálculo del agua evaporada:**

$$H_2O_{\text{evap}} = Y_2 - Y_1 \qquad \left[\frac{\text{kg}\ H_2O}{\text{kg aire seco}}\right]$$

  (nótese el orden invertido respecto a la condensación: aquí $Y_2 > Y_1$ porque la mezcla gana vapor, no lo pierde).

### 5.5 Otros procesos (autoestudio)

La conferencia menciona dos procesos adicionales — **compresión** y **enfriamiento de agua** — que quedan como material de autoestudio (páginas 183–189 del texto, no incluidas en esta carpeta). El Ejercicio 2 de la Clase Práctica #3 (resuelto en la Conferencia 3, sección 6.2) es, de hecho, un ejemplo completo de proceso de **compresión con condensación**, así que ese caso particular ya quedó cubierto en este repositorio con todo detalle.

### 5.6 Resumen visual de los cuatro procesos

Situando los cuatro procesos en los mismos ejes $(t, Y)$ de la carta, alrededor de un punto de partida sobre o cerca de la curva de saturación:

| Proceso | Dirección en la carta | Variable que se mantiene constante |
|---|---|---|
| **Calentamiento** | Horizontal, hacia $t$ mayor | $Y$ (y por tanto $t_r$) |
| **Enfriamiento** | Horizontal, hacia $t$ menor | $Y$ (y por tanto $t_r$) |
| **Condensación** | Sobre la curva de saturación, hacia $t$ menor | $\%Y_R = 100\ \%$ |
| **Saturación adiabática (vaporización)** | Hacia la curva de saturación, siguiendo las líneas de $t_{bh}$ | $t_{bh} = t_{sa}$ |

**Observación de cierre de la conferencia:** solo en los procesos de **vaporización y condensación** cambia la humedad $Y$ de la mezcla; en el calentamiento y el enfriamiento simples, $Y$ es un invariante del proceso.

---

## 6. Ejemplo resuelto completo (Clase Práctica #4)

Este es el ejercicio que acompaña y ejercita directamente el contenido de esta conferencia: el manejo de la carta sicrométrica del sistema agua-aire y el cálculo de los flujos asociados a procesos de vaporización y condensación en un esquema con varios equipos combinados.

### 6.1 Planteamiento

**Sistema (a $101.3\ \text{kPa}$ constante):**

```
(1) t=24°C, tbh=16°C  ──►  Saturador  ──(3)──┐
                                              ├──►  Calentador  ──(6)──►  Salida: %Yr=30, tr=14°C, 30 870 m³/h
                        (2) H2O  ▲            │
                                 │           (5)
(9) t=30°C, %Yr=100  ──►  Condensador  ──(7)──┤
                                (8) 50 kg H2O/h retirados
                                              └──►  Calentador  ──(5)──┘  (alimenta la unión antes de (4))
```

Datos: las condiciones de las corrientes (3), (4) y (5) son **las mismas** (son, de hecho, el mismo punto de estado, dividido en tres tramos de tubería antes y después de la unión).

**Incisos a resolver:**

(a) Representar el proceso en la carta sicrométrica.
(b) Determinar las condiciones de las corrientes (3), (4) y (5).
(c) Calcular la masa de mezcla húmeda en kg/h que circula por la corriente (5).
(d) Determinar el agua incorporada por hora al proceso en el saturador adiabático.
(e) Calcular el flujo de agua en la corriente (3).

### 6.2 Ecuaciones de trabajo generales

Antes de resolver, conviene fijar las tres relaciones que se usan repetidamente (además de las ya vistas en las secciones 3 y 5):

$$H_2O = m_{as}\,\Delta Y \qquad\text{(agua ganada o perdida, en kg, con } \Delta Y = Y_{\text{sale}}-Y_{\text{entra}}\text{ tomado siempre positivo)}$$

$$V_H = \frac{V_t}{m_{as}} \qquad\text{(ambos volúmenes medidos en el mismo estado termodinámico: misma } T, P, \text{ composición)}$$

$$m_{ah} = m_{as} + m_{\text{agua}} = m_{as}(1+Y) \qquad\text{(masa de aire húmedo total = aire seco × (1+Y), porque } m_{\text{agua}}=m_{as}Y\text{)}$$

### 6.3 Inciso (a) — Representación en la carta

Cada corriente se ubica como un punto $(t, Y)$:

- **(1)** entra al saturador con $t=24\ \text{°C}$, $t_{bh}=16\ \text{°C}$. Como el saturador es un proceso de **vaporización adiabática** (sección 5.4), la trayectoria de (1) a (3) sigue la línea de $t_{bh}=16\ \text{°C}$ constante hasta acercarse a la curva de saturación.
- **(9)** entra al condensador con $t=30\ \text{°C}$, $\%Y_R=100$ (ya saturada, sobre la curva). El condensador enfría a lo largo de la curva de saturación (proceso de **condensación**, sección 5.3) hasta (7).
- **(7)** se calienta (proceso de **calentamiento**, sección 5.1, a $Y$ constante) hasta (5).
- **(3)=(4)=(5)** se unen y entran al segundo calentador, que también opera a $Y$ constante, hasta llegar a (6), donde se reportan $\%Y_R=30$, $t_r=14\ \text{°C}$.

### 6.4 Inciso (b) — Condiciones de (3), (4) y (5)

Estos valores se leen directamente de la carta sicrométrica, siguiendo la línea de $t_{bh}=16\ \text{°C}$ desde el punto (1) hasta donde la trayectoria del saturador se estabiliza:

$$t = 19.5\ \text{°C}\,,\quad t_{bh}=16\ \text{°C}\,,\quad t_{sa}=16\ \text{°C}\,,\quad t_r=14\ \text{°C}\,,\quad \%Y_R=70\,,\quad Y=0.01\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}}\,,\quad V_H = 0.842\ \frac{\text{m}^3\text{(a.h.)}}{\text{kg(a.s.)}}$$

(coherente con lo esperado: $t_{bh}=t_{sa}=16\ \text{°C}$, confirmando la identidad de la sección 2.4 para el sistema agua-aire; y $Y=0.01$ es mayor que la $Y$ de entrada en (1), como corresponde a un proceso de humidificación por saturación adiabática).

De forma análoga, para la corriente **(9)**, saturada a $t=30\ \text{°C}$: usando las [Steam Tables](../Steam%20Tables_Keenan.pdf), $P_s(30°C)=4.246\ \text{kPa}$, y con $P=101.3\ \text{kPa}$:

$$Y_{(9)} = \frac{MM_{H_2O}}{MM_{\text{aire}}}\cdot\frac{P_s}{P-P_s} = \frac{18}{29}\times\frac{4.246}{101.3-4.246} = 0.6207\times 0.04375 = 0.0272\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}}$$

Este valor **coincide exactamente** con el que reporta el ejercicio ($Y_{(9)}=0.0272$), lo que confirma tanto el dato leído en la carta como el método.

### 6.5 Inciso (c) — Masa de mezcla húmeda que circula por (5)

**Paso 1 — Plantear la masa de aire húmedo:**

$$m_{ah(5)} = m_{as(5)}(1+Y_{(5)})$$

**Paso 2 — Obtener $m_{as(5)}$ a partir del balance de agua en el condensador.** Como $m_{as(5)}=m_{as(7)}=m_{as(9)}$ (el aire seco no cambia de masa al atravesar condensador y calentador — solo cambia el contenido de vapor y la temperatura) y, por la ecuación de la sección 6.2, $H_2O_{\text{cond}}=m_{as}\,\Delta Y$ entre (9) y (7):

$$\Delta Y = Y_{(9)}-Y_{(7)} = 0.0272-0.01 = 0.0172\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}}$$

(aquí se usó que $Y_{(7)}=Y_{(3,4,5)}=0.01$, porque el calentador entre (7) y (5) no cambia $Y$ — sección 5.1). Con los 50 kg/h de agua retirados en el condensador (corriente 8):

$$m_{as} = \frac{H_2O_{\text{cond}}}{\Delta Y} = \frac{50\ \text{kg/h}}{0.0172\ \tfrac{\text{kg}\ H_2O}{\text{kg a.s.}}} = 2906.97\ \frac{\text{kg a.s.}}{\text{h}}$$

**Paso 3 — Calcular la masa de aire húmedo en (5):**

$$m_{ah(5)} = 2906.97\times(1+0.01) = \boxed{2936.04\ \text{kg/h}}$$

### 6.6 Inciso (d) — Agua incorporada por hora en el saturador adiabático

**Paso 1 — Plantear el balance de agua en el saturador** (de (1) a (3)):

$$H_2O_{\text{incorp}} = m_{as(1)}\,\Delta Y\,,\qquad \Delta Y = Y_{(4)}-Y_{(1)}$$

**Paso 2 — Obtener $Y_{(1)}$.** Del primer calentador, $m_{as(4)}=m_{as(6)}$ y $Y_{(4)}=Y_{(6)}$ (a $Y$ constante); del enunciado de (6), $\%Y_R=30$ y $t_r=14\ \text{°C}$ — de la relación de la sección 2.1, $t_r$ determina $Y$: leyendo en la carta a $t_r=14\ \text{°C}$ sobre la curva de saturación y proyectando horizontalmente, $Y_{(6)}=0.008\ \text{kg}\ H_2O/\text{kg a.s.}$ Entonces:

$$\Delta Y = Y_{(4)}-Y_{(1)} = 0.01-0.008 = 0.002\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}}$$

**Paso 3 — Obtener $m_{as(6)}$ a partir del caudal volumétrico dado y el volumen húmedo en (6).** Con $V_{H(6)}=0.884\ \text{m}^3\text{(a.h.)/kg(a.s.)}$ (leído de la carta a las condiciones de (6)) y el caudal $30\,870\ \text{m}^3/\text{h}$:

$$m_{as(6)} = \frac{V_{(6)}}{V_{H(6)}} = \frac{30\,870\ \text{m}^3/\text{h}}{0.884\ \text{m}^3/\text{kg a.s.}} = 34\,920.8\ \frac{\text{kg a.s.}}{\text{h}}$$

**Paso 4 — Balance de aire seco en la unión antes del segundo calentador.** El aire seco se conserva: $m_{as(6)} = m_{as(3)}+m_{as(5)}$, y como $m_{as(1)}=m_{as(3)}$ (el saturador tampoco cambia la masa de aire seco):

$$m_{as(1)} = m_{as(3)} = m_{as(6)} - m_{as(5)} = 34\,920.8 - 2906.97 = 32\,013.83\ \frac{\text{kg a.s.}}{\text{h}}$$

**Paso 5 — Calcular el agua incorporada:**

$$H_2O_{\text{incorp}} = m_{as(1)}\,\Delta Y = 32\,013.83\times(0.01-0.008) = \boxed{64\ \text{kg}\ H_2O/\text{h}}$$

### 6.7 Inciso (e) — Flujo de agua en la corriente (3)

Con $m_{as(3)}=32\,013.83\ \text{kg a.s./h}$ (calculado en el paso 4 anterior) y $Y_{(3)}=0.01\ \text{kg}\ H_2O/\text{kg a.s.}$ (inciso b):

$$H_2O_{(3)} = m_{as(3)}\,Y_{(3)} = 32\,013.83\times 0.01 = 320.14\ \text{kg/h}$$

Convirtiendo a base molar ($MM_{H_2O}=18\ \text{g/mol}$):

$$H_2O_{(3)} = \frac{320.14\ \text{kg/h}}{18\ \text{kg/kmol}} = \boxed{17.78\ \text{kmol/h}}$$

### 6.8 Comentario de cierre del ejercicio

Este ejercicio integra exactamente las tres piezas de la conferencia: la **lectura de la carta sicrométrica** (incisos a-b, para obtener $t_{bh}$, $t_r$, $Y$ y $V_H$ en cada punto), el **volumen húmedo** como puente entre caudales volumétricos y flujos másicos de aire seco (inciso d, paso 3), y el **balance de agua** en cada equipo (calentador: $Y$ constante; saturador y condensador: $\Delta Y \ne 0$, con $H_2O = m_{as}\Delta Y$). Como señala la propia clase práctica en su conclusión: estas ecuaciones **"no son más que ecuaciones del próximo tema" (balance de masa)** — es decir, este ejercicio es, en esencia, un balance de masa aplicado a un caso particular (agua-aire), resuelto con las herramientas gráficas de la sicrometría en lugar de las herramientas formales del Tema 3.

---

## 7. Preguntas de repaso (respondidas)

**¿Cuándo se considera técnicamente que se está en presencia de una mezcla vapor-gas?**
Cuando uno de sus componentes tiene $T<T_c$ (es vapor, condensable) y el otro tiene $T>T_c$ (es gas, incondensable) a las condiciones del sistema (ver Conferencia 3, sección 2).

**¿Cuál es el fundamento físico del método gráfico de Cox?**
Que el logaritmo de la presión de vapor de una sustancia es, aproximadamente, una función lineal del logaritmo de la presión de vapor de una sustancia de referencia a la misma temperatura, porque la razón de sus calores de vaporización es prácticamente constante (Conferencia 3, sección 4.2).

**¿Cómo se define una mezcla vapor-gas parcialmente saturada?**
Aquella en la que la presión parcial del vapor es menor que su presión de saturación a esa temperatura: $p_v < P_s$ (Conferencia 3, sección 5.1).

**¿Varía el grado de saturación de la mezcla durante un enfriamiento hacia el punto de rocío?**
Sí: el $\%Y_R$ aumenta progresivamente desde su valor inicial hasta 100 % exactamente en $t_r$, aunque la composición ($Y_m$, $Y$) permanece constante durante todo ese tramo (sección 2.1).

**¿Podría sugerir una manera práctica de medir la temperatura de rocío?**
Enfriar una superficie (por ejemplo, un espejo o un vaso metálico) en contacto con la mezcla hasta que se empañe con la primera gota de condensado, y leer la temperatura de esa superficie en ese instante — esa es, por definición, $t_r$.

**Para una mezcla parcialmente saturada, ¿qué temperatura es mayor, la de bulbo seco o la de bulbo húmedo? ¿Por qué?**
La de bulbo seco, $t$, siempre es mayor que $t_{bh}$, porque la evaporación del líquido en la mecha húmeda enfría el termómetro por debajo de la temperatura real de la corriente (sección 2.2).

**Si el contacto mezcla-líquido en la cámara de saturación adiabática es prolongado, ¿cómo sale la mezcla?**
Sale **saturada**, a la temperatura de saturación adiabática $t_{sa}$ (sección 2.3).

**¿Será posible conocer la humedad y el $\%Y_R$ si se conocen $t$ y $t_{bh}$?**
Sí — dos condiciones independientes cualesquiera (con presión fija) determinan un único punto en la carta, del cual se leen todas las demás propiedades. La única excepción son las parejas redundantes $(t_r,Y)$ y $(t_{bh},t_{sa})$ (sección 4.3).

**¿Será un proceso de humidificación o de deshumidificación la condensación? ¿Y la saturación adiabática?**
La condensación es **deshumidificación** ($Y$ disminuye); la saturación adiabática (vaporización) es **humidificación** ($Y$ aumenta) (secciones 5.3 y 5.4).

**Si se quiere conocer el agua condensada por unidad de tiempo, ¿qué información adicional hace falta?**
El **flujo de aire seco** (en, por ejemplo, kg aire seco/h), porque la fórmula $H_2O_{\text{cond}}=Y_1-Y_2$ da un resultado por unidad de masa de aire seco, no por unidad de tiempo (sección 5.3).

**¿No debe cumplirse que $H_2O_{\text{entra}} = H_2O_{\text{sale}} + H_2O_{\text{cond}}$?**
Sí — y esta es, señala la propia conferencia al cerrar, la forma más elemental de un **balance de masa**: lo que entra de agua a un equipo debe salir, ya sea como vapor en la corriente gaseosa o como líquido condensado. Formalizar este tipo de balance con todo rigor (para sistemas de cualquier complejidad, no solo agua-aire) es precisamente el contenido del Tema 3.

---

## 8. Para seguir estudiando

- **Texto, páginas 145–199** (no incluidas en esta carpeta): contiene todo el contenido de la conferencia con mayor detalle, incluyendo la demostración de la fórmula del volumen húmedo (pág. 157, reconstruida en la sección 3.2 de este documento) y los ejercicios resueltos 2.8 (pág. 148, cálculo de $t_r$), 2.10 (pág. 159, aplicación numérica de $V_H$), 2.11 y 2.12 (págs. 164–165, lectura de la carta), 2.15 (pág. 176, calentamiento), 2.16 (pág. 179, condensación), 2.17 (pág. 182, saturación adiabática), 2.20–2.23 (págs. 189–196, compresión y enfriamiento de agua).
- **Figuras B-10 y B-11 del apéndice B** del texto: la carta sicrométrica impresa propiamente dicha, necesaria para resolver problemas por lectura gráfica directa (como el Ejercicio 3 de la Conferencia 3, sección 6.3, y el ejercicio de la sección 6 de este documento).
- **Páginas 168–175:** extensión del uso de la carta a otras presiones y a sistemas distintos del agua-aire (autoestudio, sección 4.4 de este documento).
- **Páginas 183–189:** procesos de compresión y enfriamiento de agua (autoestudio, sección 5.5).
- **Carpeta [TCE1](TCE1/)** de este repositorio: el "Trabajo de Control Extraclases #1" (doce variantes A–L) integra exactamente el tipo de esquema con varios equipos (saturadores, calentadores, enfriadores) que se resolvió en la sección 6 de este documento — es la continuación natural de práctica una vez dominada esta conferencia.

**Aviso importante que deja la propia conferencia:** en la clase #6 (la última del Tema 2) se realiza un **CT (control) de 30 minutos** en clase, cuyo contenido evalúa específicamente el **dominio de las formas de expresar la composición de una mezcla vapor-gas** — es decir, el contenido íntegro de la sección 5 de la [Conferencia 3](Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md). Conviene repasar en particular la tabla resumen de esa sección y la cadena de relaciones entre $y$, $Y$, $Y_m$, $y_m$ y $p_v$.

La conferencia cierra anticipando el Tema 3: los cálculos de agua ganada o perdida vistos aquí ($H_2O = m_{as}\Delta Y$) son, en esencia, balances de masa resueltos de manera elemental; el próximo tema los formaliza **con mayor rigor de contenido y de métodos**, extendiéndolos a cualquier proceso químico, no solo a mezclas vapor-gas.

---

## Referencias / fuentes usadas en este documento

- [Conferencia 4 Tema 2 Plan E.pdf](Conferencia%204%20Tema%202%20Plan%20E.pdf) — fuente principal del contenido teórico.
- [Conferencia 3 - Presion de Vapor y Composicion de Mezclas Vapor-Gas.md](Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md) — base conceptual (presión de vapor, formas de composición) sobre la que se construye esta conferencia.
- [Guia de estudio Tema 2.pdf](Guia%20de%20estudio%20Tema%202.pdf) — objetivos y habilidades del tema.
- [PIQ1 Clase practica 4 Procesos de vaporizacion y condensacion Saturador-Condensador-Calentadores.pdf](PIQ1%20Clase%20practica%204%20Procesos%20de%20vaporizacion%20y%20condensacion%20Saturador-Condensador-Calentadores.pdf) — el ejercicio resuelto completo en la sección 6.
- [../Steam Tables_Keenan.pdf](../Steam%20Tables_Keenan.pdf) — tabla de agua saturada, usada para verificar de forma independiente el valor de $Y_{(9)}$ en la sección 6.4.
