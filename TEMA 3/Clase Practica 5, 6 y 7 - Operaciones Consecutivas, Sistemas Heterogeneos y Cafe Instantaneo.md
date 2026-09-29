# Tema 3 — Clases Prácticas 5, 6 y 7: balance de masa sin reacción química (paso a paso)

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuentes principales:** [PIQ1 Clase practica 5 Operaciones consecutivas y desvio Triple efecto y concentrador de jugo.pdf](PIQ1%20Clase%20practica%205%20Operaciones%20consecutivas%20y%20desvio%20Triple%20efecto%20y%20concentrador%20de%20jugo.pdf) · [PIQ1 Clase practica 6 Sistemas heterogeneos.pdf](PIQ1%20Clase%20practica%206%20Sistemas%20heterogeneos.pdf) · [PIQ1 Clase practica 7 Tecnologia del cafe instantaneo.pdf](PIQ1%20Clase%20practica%207%20Tecnologia%20del%20cafe%20instantaneo.pdf) (y su [enunciado](PIQ1%20Clase%20practica%207%20Tecnologia%20del%20cafe%20instantaneo_enunciado.pdf))
> **Teoría de base (léase antes si algo no se entiende):** [Conferencia 5 - Expresion General del Balance de Masa y Balance sin Reaccion Quimica.md](Conferencia%205%20-%20Expresion%20General%20del%20Balance%20de%20Masa%20y%20Balance%20sin%20Reaccion%20Quimica.md)
> **Apoyo numérico:** [../TEMA 2/Conferencia 4 - Mediciones Termometricas, Carta Sicrometrica y Procesos.md](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md) (carta sicrométrica, usada en CP6 y CP7)
>
> Este documento es un desarrollo **independiente** de las Clases Prácticas 5, 6 y 7, pensado para poder seguirse sin tener que ir y venir a otro archivo: cada fórmula se recuerda antes de usarse, cada sustitución numérica se muestra completa (no se "saltan" pasos de álgebra ni conversiones de unidades), y se explica el **porqué** de cada decisión de cálculo, no solo el cómo. Los cinco ejercicios de estas tres clases prácticas se resuelven íntegros, incluidos los trabajos independientes y la variante con recirculación del ejercicio de café instantáneo, que el material original deja sin resolver.

---

## 0. Qué son estas clases prácticas y qué se espera lograr con ellas

Una "clase práctica" (CP), a diferencia de una conferencia, no introduce teoría nueva: **ejercita** la teoría ya explicada en la conferencia correspondiente. Las tres clases prácticas de este documento ejercitan, todas, el mismo bloque teórico —el balance de masa **sin** reacción química de la [Conferencia 5](Conferencia%205%20-%20Expresion%20General%20del%20Balance%20de%20Masa%20y%20Balance%20sin%20Reaccion%20Quimica.md)— pero cada una añade una dificultad distinta:

- **CP5** ejercita los **procesos con desvío** (bypass) y las **operaciones consecutivas** (varios equipos en serie), y obliga a decidir, entre varios sistemas posibles, cuál conviene resolver primero según sus grados de libertad.
- **CP6** ejercita las formas de expresar la composición en **sistemas heterogéneos** (mezclas sólido-líquido: suspensiones y tortas de filtración), un vocabulario nuevo que no se usó en el Tema 2.
- **CP7** integra **todo lo anterior** en un solo proceso complejo de 13 corrientes (percolador, mezclador, secador spray, separador ciclónico, prensa y secador), obligando a decidir en qué orden conviene resolver cada subsistema — la habilidad más avanzada de todo el bloque sin reacción química.

---

## 1. Formulario de partida (recordatorio, sin re-derivar)

Antes de resolver nada, conviene tener a mano las fórmulas que se usarán una y otra vez. Todas se demuestran con detalle en la Conferencia 5; aquí solo se recuerdan como herramientas de trabajo.

### 1.1 Balance de masa sin reacción química y grados de libertad

$$\left[\text{Masa (o moles) que entra de un componente o de una corriente}\right] = \left[\text{Masa (o moles) que sale}\right]$$

$$V = \#\text{Ecuaciones Linealmente Independientes (ELI)} - \#\text{Incógnitas}\,,\qquad \#\text{ELI}=\#\text{Componentes (EPB)}+\#\text{ERC}+\#\text{ERE}$$

**Recordatorio del convenio de signos** (importante porque es el opuesto al de otros textos): $V=0$ → el sistema tiene solución única; $V<0$ → faltan ecuaciones o sobran incógnitas, no se puede resolver todavía (falta fijar una base de cálculo, o hay que ampliar/cambiar la frontera del sistema); $V>0$ → sobran ecuaciones, hay que revisar redundancia o consistencia de los datos.

- **EPB** (ecuaciones propias del balance): tantas como componentes tenga el sistema.
- **ERC** (restrictivas de composición): tantas como corrientes de composición no totalmente conocida ($\sum x_i = 1$ en cada una).
- **ERE** (restrictivas específicas): cualquier relación adicional propia del problema (p. ej., "$m_1=m_2=m_3$").

### 1.2 Sistemas con desvío (bypass) o recirculación

$$\text{Corriente fresca} \to \underbrace{\bullet}_{\text{punto de desvío}} \to \boxed{\text{Proceso}} \to \underbrace{\bullet}_{\text{punto de unión}} \to \text{Corriente producto}$$

Se puede balancear en 4 fronteras distintas: (i) el punto de desvío (solo cantidades totales, porque las composiciones no cambian ahí — es una división mecánica); (ii) alrededor del proceso; (iii) el punto de unión; (iv) el sistema completo (con la corriente de desvío quedando **interna**, sin cruzar la frontera).

### 1.3 Sistemas heterogéneos (sólido-líquido): notación y fórmulas

| Magnitud | Definición | Símbolo (suspensión / torta) |
|---|---|---|
| Fracción másica del sólido en la mezcla | masa sólido seco / masa mezcla | $x$ / $x_t$ |
| Fracción másica del sólido en base libre de sólido | masa sólido seco / masa **líquido** | $X$ / $X_t$ |
| Concentración de sólidos en la mezcla | masa sólido seco / volumen mezcla | $C_s'$ / $C_t'$ |
| Concentración de sólidos en base libre | masa sólido seco / volumen **líquido** | $C_s$ |
| Humedad de la mezcla | masa líquido / masa mezcla | $H$ |

$$x=\dfrac{X}{1+X}\,,\qquad x+H=1\,,\qquad \dfrac{C_s'}{d_s}=x\,,\qquad C_s\cdot\dfrac{1}{d}=X\,,\qquad \dfrac{1}{d_s}=\dfrac{x}{d_p}+\dfrac{1-x}{d}$$

con $d_s$ la densidad de la mezcla, $d$ la del líquido puro, $d_p$ la del sólido seco puro. **Por qué existe esta doble familia de fórmulas (base "mezcla total" y base "líquido libre de sólido"):** exactamente por la misma razón que en las mezclas vapor-gas del Tema 2 — algunos datos de un problema vienen naturalmente en una base (p. ej., "kg de sólido por m³ de líquido", que es concentración en base libre, $C_s$) y otros en la otra (p. ej., "% de sólidos en la torta", que es $x_t$), así que hace falta poder convertir de una a otra sin perder información.

---

## 2. Ejercicio 1 (CP5) — Evaporador de tres efectos en serie

### 2.1 Enunciado

Una solución acuosa de un sólido al 50 % másico se concentra en un evaporador de **tres efectos** (tres equipos en serie, cada uno recibe la salida del anterior y evapora agua adicional). El flujo de alimentación es $F=50000$ kg/h y la producción final es $C=35000$ kg/h. En **cada** efecto se evapora **igual** cantidad de agua ($m_1=m_2=m_3$). Determinar las corrientes que salen del 2.º y 3.er efecto.

### 2.2 Entender el problema y dibujarlo

$$50000\ \tfrac{kg}{h}\ (F)\ \Big\{x_{s(F)}=0.5,\ x_{H_2O(F)}=0.5\Big\}\ \longrightarrow\ \boxed{1^{er}\ \text{efecto}}\ \xrightarrow{A}\ \boxed{2^{do}\ \text{efecto}}\ \xrightarrow{B}\ \boxed{3^{er}\ \text{efecto}}\ \longrightarrow\ 35000\ \tfrac{kg}{h}\ (C)$$

con $m_1$, $m_2$, $m_3$ el agua evaporada (en forma de vapor) que sale por arriba de cada efecto respectivamente. Nótese que ninguna corriente intermedia ($A$, $B$) tiene su flujo ni su composición dados directamente — solo se conoce la alimentación (F, con su composición) y el producto final (C, solo su flujo). Esto es justamente lo que hace este problema interesante: hay que **decidir con qué sistema empezar**.

### 2.3 Por qué ningún efecto por sí solo tiene solución

Antes de calcular nada, conviene comprobar los grados de libertad de **cada** posible sistema, empezando por el más pequeño (un solo efecto). BC = 1 h (se elige el tiempo como base porque ya hay flujos dados "por hora" — ver la Conferencia 5, sección 3.2-b).

**Sistema = solo el 1.er efecto** (aunque no contiene, dentro de su frontera, ni a B ni a C):

- Incógnitas: $m_1$, $A$, $x_{s(A)}$, $x_{H_2O(A)}$ → 4.
- Ecuaciones: 2 EPB (agua, sólido) + 1 ERC (la de la corriente A, $x_{s(A)}+x_{H_2O(A)}=1$) = 3.
- $V=3-4=-1$: **no tiene solución** (falta una ecuación o dato).

**Sistema = solo el 2.do efecto:**

- Incógnitas: $B$, $m_2$, $A$, $x_{s(B)}$, $x_{H_2O(B)}$, $x_{s(A)}$, $x_{H_2O(A)}$ → 7 (nótese que aquí $A$ es una corriente de **entrada**, así que su composición también es incógnita).
- Ecuaciones: 2 EPB + 2 ERC (de A y de B) = 4.
- $V=4-7=-3$: **no tiene solución**, y peor que el anterior.

**Sistema = solo el 3.er efecto:**

- Incógnitas: $B$, $m_3$, $x_{s(B)}$, $x_{H_2O(B)}$, $x_{s(C)}$, $x_{H_2O(C)}$ → 6 (aunque $C=35000$ kg es dato, su **composición** no lo es).
- Ecuaciones: 2 EPB + 2 ERC (de B y de C) = 4.
- $V=4-6=-2$: **tampoco tiene solución**.

**Conclusión intermedia:** ninguno de los tres efectos por separado se puede resolver — a cada uno le "faltan" datos, porque las corrientes internas ($A$, $B$) no son conocidas por ningún lado todavía. Hay que **ampliar la frontera**.

### 2.4 El sistema que sí funciona: el proceso completo

**Sistema = los tres efectos juntos** (frontera alrededor de todo el evaporador; ahora $A$ y $B$ quedan **internas** — no cruzan la frontera, así que no cuentan como incógnitas del sistema):

$$m_1,m_2,m_3\ \uparrow\uparrow\uparrow \qquad F=50000\ \text{kg/h}\ \{x_{s(F)}=0.5\} \longrightarrow \boxed{1^{ero},\,2^{do}\,\text{y}\,3^{er}\ \text{efectos}} \longrightarrow C=35000\ \text{kg/h}\ \{x_{s(C)}\}$$

- Incógnitas: $m_1$, $m_2$, $m_3$, $x_{s(C)}$, $x_{H_2O(C)}$ → 5.
- Ecuaciones: 2 EPB (agua, sólido) + 1 ERC (de C) + 2 ERE ($m_1=m_2$ y $m_2=m_3$, que son dos ecuaciones independientes aunque se enuncien juntas como "$m_1=m_2=m_3$") = 5.
- $V=5-5=0$: **¡sí tiene solución!**

**Estrategia de dos pasos, ya que ahora sí se puede avanzar:**

1. Resolver el proceso completo para obtener $m_1$, $m_2$, $m_3$, $x_{s(C)}$, $x_{H_2O(C)}$.
2. Con esos valores ya conocidos, volver a analizar el 3.er efecto solo: ahora sus incógnitas se reducen (porque $m_3$ y la composición de $C$ ya no son incógnitas, son datos), y su $V$ deja de ser negativo.

### 2.5 Paso 1 — Resolver el proceso completo

**Balance global (total):**

$$F = C + m_1+m_2+m_3$$

$$50000 = 35000 + (m_1+m_2+m_3)$$

$$m_1+m_2+m_3 = 50000-35000 = 15000\ \text{kg}\qquad(1)$$

**Balance del sólido** (el sólido no se evapora — solo el agua sale por arriba de cada efecto — así que todo el sólido que entra con $F$ sale exactamente con $C$):

$$F\,x_{s(F)} = C\,x_{s(C)}$$

$$50000(0.5) = 35000\,x_{s(C)}$$

$$x_{s(C)} = \dfrac{50000(0.5)}{35000} = \dfrac{25000}{35000} = 0.7143\qquad(2)$$

**Ecuación restrictiva de composición para C:**

$$x_{s(C)}+x_{H_2O(C)}=1 \qquad\Rightarrow\qquad x_{H_2O(C)} = 1-0.7143 = 0.2857\qquad(3)$$

**Ecuaciones restrictivas especiales** (dato del enunciado, "en cada efecto se evapora igual cantidad"):

$$m_1=m_2=m_3$$

Sustituyendo en (1): como los tres son iguales, $m_1+m_1+m_1=3\,m_1=15000$, así que:

$$\boxed{m_1=m_2=m_3=\dfrac{15000}{3}=5000\ \text{kg}}$$

### 2.6 Paso 2 — Resolver el 3.er efecto (ahora sí resoluble)

Con $m_3=5000$ kg y la composición de $C$ ya conocidos, se replantean los grados de libertad del 3.er efecto: sus incógnitas se reducen de 6 a solo 3 ($B$, $x_{s(B)}$, $x_{H_2O(B)}$), mientras que las ecuaciones siguen siendo 4 (2 EPB + 2 ERC, aunque ahora la de $C$ ya está resuelta y solo aporta un valor conocido, no una incógnita nueva) — de modo que $V=4-3=1$; en la práctica esto significa que hay **más que suficiente** información y el sistema se resuelve de forma directa, ecuación por ecuación, sin necesidad de resolver un sistema simultáneo.

**Balance total en el 3.er efecto** ($B$ es la entrada, $C$ y $m_3$ las salidas):

$$B = C + m_3 = 35000+5000 = 40000\ \text{kg}$$

**Balance del sólido en el 3.er efecto** (de nuevo, el sólido no se evapora, así que todo el sólido de $B$ termina en $C$):

$$B\,x_{s(B)} = C\,x_{s(C)}$$

$$40000\,x_{s(B)} = 35000(0.7143)$$

$$x_{s(B)} = \dfrac{35000(0.7143)}{40000} = \dfrac{25000}{40000} = 0.625$$

**Restrictiva de composición para B:**

$$x_{H_2O(B)} = 1-0.625 = 0.375$$

$$\boxed{B=40000\ \text{kg/h}\,,\qquad x_{s(B)}=0.625\ (62.5\%)\,,\qquad x_{H_2O(B)}=0.375\ (37.5\%)}$$

### 2.7 Trabajo independiente: hallar la corriente A

La propia clase práctica pide, como ejercicio adicional: "Determine el flujo y la composición de la corriente A tomando como sistema el primer efecto. Posteriormente tome como sistema el 2.do efecto y verifique que los cálculos son correctos, globalmente y por componentes." Se resuelve aquí completo.

**Sistema = 1.er efecto**, ahora con $F=50000$ kg y $m_1=5000$ kg ya conocidos (a diferencia de la sección 2.3, donde $m_1$ todavía era incógnita):

$$\text{Balance total: } A = F-m_1 = 50000-5000 = 45000\ \text{kg}$$

$$\text{Balance de sólido: } F\,x_{s(F)}=A\,x_{s(A)} \;\Rightarrow\; x_{s(A)}=\dfrac{50000(0.5)}{45000}=\dfrac{25000}{45000}=0.5556$$

$$x_{H_2O(A)} = 1-0.5556 = 0.4444$$

$$\boxed{A=45000\ \text{kg/h}\,,\qquad x_{s(A)}=0.5556\ (55.56\%)\,,\qquad x_{H_2O(A)}=0.4444\ (44.44\%)}$$

**Verificación con el 2.do efecto** ($A$ es ahora la entrada; $B$ y $m_2=5000$ kg, las salidas):

$$\text{Balance total: } B = A-m_2 = 45000-5000 = 40000\ \text{kg}$$

Este valor de $B$ debe coincidir exactamente con el que se obtuvo en la sección 2.6 trabajando "hacia atrás" desde el 3.er efecto ($B=40000$ kg) — **y coincide exactamente**, lo cual confirma que ambos caminos de cálculo son consistentes.

$$\text{Balance de sólido: } A\,x_{s(A)}=B\,x_{s(B)} \;\Rightarrow\; x_{s(B)}=\dfrac{45000(0.5556)}{40000}=\dfrac{25000}{40000}=0.625$$

De nuevo, $x_{s(B)}=0.625$ coincide **exactamente** con el valor obtenido en la sección 2.6. Esta doble coincidencia (flujo y composición de $B$, calculados por dos caminos independientes: hacia adelante desde $F$, y hacia atrás desde $C$) es la comprobación cruzada que recomienda el paso (e) del programa de análisis de la Conferencia 5 — y confirma que toda la solución del Ejercicio 1 es correcta.

---

## 3. Ejercicio 2 (CP5) — Concentrador de jugo de naranja con corriente de ajuste

### 3.1 Enunciado y por qué existe este proceso

Para reducir los costos de traslado del jugo de naranja fresco, a menudo se concentra antes de embarcarse y se restituye (se le vuelve a agregar agua, o en este caso jugo fresco) al llegar a destino. La concentración se hace en un evaporador especial que opera a **presión menor que la atmosférica** y con **tiempo de residencia corto**, precisamente para minimizar la pérdida de los compuestos de sabor y aroma (presentes en cantidades muy pequeñas y muy volátiles/sensibles al calor). Como aun así se pierde algo de esos compuestos, una práctica común de la industria es **sobre-concentrar** el jugo (más de lo necesario) y luego **diluirlo de vuelta** con una porción de jugo fresco sin procesar — la llamada "corriente de ajuste" — para lograr la concentración final deseada con mejor sabor y aroma que si se hubiera concentrado directamente hasta ese punto.

**Enunciado numérico:** si se utiliza el 10 % de la alimentación de jugo fresco como corriente de ajuste, calcular la composición del producto concentrado y la razón de evaporación (flujo de agua evaporada entre peso de jugo fresco) cuando se alimentan 10 000 kg/h de jugo fresco. $x_{S(1)}=12\%$ (sólidos disueltos, azúcares) en el jugo fresco; $x_{S(5)}=80\%$ en el jugo concentrado (salida del evaporador).

### 3.2 Dibujar el proceso: es exactamente un esquema de desvío

$$(1)\ \text{Jugo fresco}\ \{x_{S(1)}=0.12\} \longrightarrow \underbrace{\bullet}_{\text{punto de desvío}} \xrightarrow{(2)} \boxed{\text{Evaporador}} \xrightarrow[x_{S(5)}=0.80]{(5)} \underbrace{\bullet}_{\text{mezclador (punto de unión)}} \longrightarrow (6)\ \text{Concentrado}$$

con la corriente (3) — el 10 % de (1) — yendo directamente del punto de desvío al mezclador (sin pasar por el evaporador), y (4) el agua evaporada, saliendo por arriba del evaporador. Comparando con el esquema general de la sección 1.2: (1) es la "corriente fresca", (3) es el "desvío", el evaporador es el "proceso" y (6) es la "corriente producto".

**BC = 1 h**, porque los datos vienen dados como flujos por hora.

### 3.3 Paso 1 — Balance en el punto de desvío

Como se explicó en la sección 1.2, en el punto de desvío **solo tiene sentido balancear cantidades totales** (las composiciones de (2) y (3) son idénticas a la de (1), porque es una simple división mecánica del mismo jugo, sin ningún cambio físico o químico):

$$F_1 = F_2+F_3$$

Por dato del enunciado, $F_1=10000$ kg (flujo total de jugo fresco alimentado), y la corriente de ajuste es el 10 % de esa alimentación:

$$F_3 = 0.1\times F_1 = 0.1(10000) = 1000\ \text{kg}$$

Despejando $F_2$:

$$F_2 = F_1-F_3 = 10000-1000 = 9000\ \text{kg}$$

### 3.4 Paso 2 — Balance en el evaporador

Como la corriente (2) sale directamente del punto de desvío sin cambio de composición, $x_{S(2)}=x_{S(1)}=0.12$.

**Balance total:** $F_2 = F_4+F_5$ (el jugo que entra al evaporador o sale como agua evaporada (4), o sale como jugo concentrado (5)).

**Balance de sólidos** (el sólido —los azúcares— no se evapora; solo el agua se va por (4), así que todo el sólido que entra por (2) sale por (5)):

$$x_{S(2)}\,F_2 = x_{S(5)}\,F_5$$

Despejando $F_5$:

$$F_5 = \dfrac{x_{S(2)}\,F_2}{x_{S(5)}} = \dfrac{0.12(9000)}{0.8} = \dfrac{1080}{0.8} = 1350\ \text{kg}$$

Y por el balance total:

$$F_4 = F_2-F_5 = 9000-1350 = 7650\ \text{kg}\qquad(\text{agua evaporada})$$

### 3.5 Paso 3 — Balance en el mezclador (punto de unión)

**Balance total:**

$$F_6 = F_5+F_3 = 1350+1000 = 2350\ \text{kg}$$

**Balance de sólidos:** el sólido que entra al mezclador viene de dos corrientes, (5) —el concentrado— y (3) —el jugo de ajuste, con la misma composición que el jugo fresco original, $x_{S(3)}=x_{S(1)}=0.12$:

$$x_{S(5)}\,F_5 + x_{S(3)}\,F_3 = x_{S(6)}\,F_6$$

Despejando $x_{S(6)}$:

$$x_{S(6)} = \dfrac{x_{S(5)}\,F_5+x_{S(3)}\,F_3}{F_6} = \dfrac{0.8(1350)+0.12(1000)}{2350} = \dfrac{1080+120}{2350} = \dfrac{1200}{2350} = 0.5106$$

### 3.6 Paso 4 — Razón de evaporación (la magnitud que pide el enunciado)

Por definición dada en el propio enunciado: razón de evaporación = flujo de agua evaporada / peso de jugo fresco alimentado.

$$\text{Razón de evaporación} = \dfrac{F_4}{F_1} = \dfrac{7650}{10000} = 0.765$$

$$\boxed{x_{S(6)}=51.06\%\ \text{sólidos}\,,\quad x_{H_2O(6)}=48.94\%\,,\quad \text{Razón de evaporación}=0.765}$$

### 3.7 Comprobación (paso e del programa de análisis)

Conviene cerrar el balance de todo el sistema (tomando la frontera alrededor de todo el proceso, con la corriente de desvío quedando interna, exactamente como en la sección 1.2-iv): lo que entra en total ($F_1$) debe ser igual a lo que sale en total ($F_4+F_6$):

$$F_1 \overset{?}{=} F_4+F_6 \qquad\Longrightarrow\qquad 10000 \overset{?}{=} 7650+2350 = 10000\quad\checkmark$$

La igualdad se cumple exactamente, lo que confirma que el balance está correctamente cerrado.

---

## 4. Ejercicio 3 (CP6) — Filtración y secado de hidróxido de níquel

### 4.1 Enunciado completo

Se estudia la separación del hidróxido de níquel hidratado por filtración en un equipo rotatorio continuo, con posterior secado no adiabático de la torta. Datos:

- Concentración de la suspensión (base libre de sólido): $C_s=131.8$ kg sólido / m³ de **líquido**.
- Densidad del material sólido: $d_p=4360$ kg/m³.
- Densidad del líquido acompañante: $d=1100$ kg/m³.
- Humedad de la torta a la salida del filtro: $H_{t(4)}=75\%$.
- Humedad de la torta a la salida del secador: $H_{t(5)}=60\%$.
- Capacidad de la instalación: 2.8 t de sólido seco/día.
- Agua de lavado adicionada: 0.8 L por kg de sólido seco.
- Aire del secador: entra a 25 °C, $\%Y_R=30\%$; sale a 35 °C, $T_r=20\ °C$ (temperatura de rocío del aire de salida).

### 4.2 Dibujar el proceso completo

$$\text{(1) Suspensión}\ \{C_s=131.8\} \xrightarrow{\ } \boxed{\text{FILTRO}} \longrightarrow \begin{cases}\text{(2) líquido filtrado}\\ \text{(4) Torta, } H_{t}=75\%\end{cases} \longrightarrow \boxed{\text{Secador no adiabático}} \longrightarrow \begin{cases}\text{(7) aire húmedo}\\ \text{(5) Torta, } H_t=60\%,\ 2.8\ \text{t/d}\end{cases}$$

con (3) el agua de lavado entrando al filtro, y (6) el aire húmedo entrando al secador. **BC = 1 día**, porque la capacidad de la instalación se da "por día".

### 4.3 Parte (a): fracción másica de sólidos y concentración en la suspensión

**Paso 1 — De concentración en base libre ($C_s$) a fracción en base libre ($X_1$).** La fórmula de la sección 1.3, $C_s\cdot(1/d)=X$, se despeja directamente porque ya está en la forma que se necesita:

$$X_1 = C_{s1}\cdot\dfrac{1}{d} = \dfrac{131.8\ \text{kg sólido/m}^3\ \text{líquido}}{1100\ \text{kg/m}^3} = 0.1198\ \dfrac{\text{kg sólido}}{\text{kg líquido}}$$

**Por qué se dividió por $d$ (densidad del líquido) y no se multiplicó:** porque $C_s$ está en "masa de sólido por **volumen** de líquido", y para llegar a "masa de sólido por **masa** de líquido" hace falta convertir ese volumen de líquido a masa de líquido — y eso se hace multiplicando el volumen por la densidad del líquido, lo cual, al estar el volumen en el denominador, equivale a **dividir** entre $d$.

**Paso 2 — De base libre ($X_1$) a fracción en la mezcla total ($x_1$).** Usando $x=X/(1+X)$:

$$x_1 = \dfrac{X_1}{1+X_1} = \dfrac{0.1198}{1+0.1198} = \dfrac{0.1198}{1.1198} = 0.1070\ \dfrac{\text{kg sólido}}{\text{kg suspensión}}\ (10.7\%)$$

**Paso 3 — Densidad de la suspensión ($d_s$), necesaria para pasar de fracción másica a concentración en la mezcla.** Se usa la regla aditiva de volúmenes específicos de la sección 1.3:

$$\dfrac{1}{d_s} = \dfrac{x_1}{d_p}+\dfrac{1-x_1}{d} = \dfrac{0.1070}{4360}+\dfrac{1-0.1070}{1100} = \dfrac{0.1070}{4360}+\dfrac{0.8930}{1100}$$

Calculando cada término por separado: $0.1070/4360 = 0.00002454$; $0.8930/1100=0.0008118$. Sumando:

$$\dfrac{1}{d_s} = 0.00002454+0.0008118 = 0.0008363\ \dfrac{\text{m}^3}{\text{kg}} \qquad\Rightarrow\qquad d_s = \dfrac{1}{0.0008363} = 1196\ \dfrac{\text{kg suspensión}}{\text{m}^3\ \text{suspensión}}$$

**Paso 4 — Concentración en la mezcla ($C_{s1}'$).** Con la fórmula $C_s'/d_s=x$ de la sección 1.3, despejando:

$$\boxed{C_{s1}' = d_s\,x_1 = 1196(0.1070) = 127.97\ \dfrac{\text{kg sólido}}{\text{m}^3\ \text{suspensión}} \approx 128\ \text{g/L}}$$

**Por qué $C_{s1}' < C_{s1}$ (128 < 131.8):** tiene sentido físico: la concentración "en base libre" (por volumen de solo líquido) siempre es mayor o igual que la concentración "en la mezcla total" (por volumen de mezcla), porque el volumen de la mezcla incluye además el volumen ocupado por el propio sólido — un volumen "extra" en el denominador que hace más pequeño el cociente.

### 4.4 Parte (b): flujo volumétrico de la suspensión procesada

**Paso 1 — Plantear la relación entre flujo másico, densidad y flujo volumétrico.** Por definición, densidad = masa/volumen, así que para una corriente de flujo (masa por unidad de tiempo):

$$d_s = \dfrac{F_1}{V_1} \qquad\Longrightarrow\qquad V_1 = \dfrac{F_1}{d_s}$$

**Paso 2 — Hallar $F_1$ (el flujo másico de suspensión) mediante un balance de sólidos.** El sólido no se disuelve, no reacciona ni cambia de fase en todo el proceso (solo se separa mecánicamente del líquido en el filtro, y luego se seca eliminando agua): por eso, la cantidad de sólido que entra por (1) es la **misma** que sale finalmente por (5):

$$\text{sólidos}_{(1)} = \text{sólidos}_{(4)} = \text{sólidos}_{(5)} = 2800\ \text{kg/día}\qquad(\text{la capacidad dada, convertida de toneladas a kg: } 2.8\ \text{t}=2800\ \text{kg})$$

Como $\text{sólidos}_{(1)} = F_1\,x_1$ (flujo total por la fracción másica del sólido), se despeja $F_1$:

$$F_1 = \dfrac{\text{sólidos}_{(1)}}{x_1} = \dfrac{2800}{0.1070} = 26168\ \dfrac{\text{kg suspensión}}{\text{día}}$$

**Paso 3 — Convertir a volumen usando $d_s$ ya calculada:**

$$\boxed{V_1 = \dfrac{F_1}{d_s} = \dfrac{26168}{1196} = 21.9\ \dfrac{\text{m}^3}{\text{día}}}$$

### 4.5 Parte (c): flujo de líquido filtrado ($F_2$)

**Paso 1 — Balance total en el filtro.** Entran la suspensión (1) y el agua de lavado (3); salen el líquido filtrado (2) y la torta húmeda (4):

$$F_1+F_3 = F_2+F_4 \qquad\Longrightarrow\qquad F_2 = F_1+F_3-F_4$$

**Paso 2 — Calcular $F_3$ (agua de lavado), a partir del dato "0.8 L por kg de sólido seco":**

$$F_3 = 0.8\ \dfrac{\text{L agua}}{\text{kg sólido}}\times 2800\ \text{kg sólido}\times 1\ \dfrac{\text{kg agua}}{\text{L agua}} = 2240\ \text{kg}$$

(se usó $1\ \text{kg}=1\ \text{L}$ para el agua, válida porque su densidad es $\approx 1000$ kg/m³ = 1 kg/L).

**Paso 3 — Calcular $F_4$ (torta húmeda a la salida del filtro), a partir de su humedad $H_{t(4)}=75\%$.** Como $H_t=1-x_t$ (sección 1.3), la fracción de **sólido** en esa torta es $x_{t(4)}=1-0.75=0.25$, y como $\text{sólidos}_{(4)}=F_4\,x_{t(4)}=2800$ kg (mismo argumento de conservación de sólido que en la sección 4.4):

$$F_4 = \dfrac{\text{sólidos}_{(4)}}{1-H_4} = \dfrac{2800}{1-0.75} = \dfrac{2800}{0.25} = 11200\ \text{kg}$$

**Paso 4 — Sustituir en el balance total del Paso 1:**

$$\boxed{F_2 = F_1+F_3-F_4 = 26168+2240-11200 = 17208\ \text{kg/día}}$$

### 4.6 Parte (d): flujo volumétrico de aire húmedo para secar la torta hasta 60 % de humedad

**Paso 1 — Agua a evaporar en el secador.** Se calcula la torta seca de salida ($F_5$, con $H_{t(5)}=60\%$, así que $x_{t(5)}=1-0.60=0.40$ es la fracción de sólido) del mismo modo que en el Paso 3 anterior:

$$F_5 = \dfrac{\text{sólidos}_{(5)}}{1-H_5} = \dfrac{2800}{1-0.6} = \dfrac{2800}{0.4} = 7000\ \text{kg}$$

$$\text{Agua evaporada} = F_4-F_5 = 11200-7000 = 4200\ \text{kg/día}$$

**Paso 2 — Leer las humedades del aire en la carta sicrométrica** (ver [Conferencia 4 del Tema 2](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md)): a la entrada, $T=25\ °C$, $\%Y_R=30\%$, se lee $Y_6=0.006$ kg agua/kg aire seco; a la salida, $T=35\ °C$, $T_r=20\ °C$, se lee $Y_7=0.015$ kg agua/kg aire seco.

**Paso 3 — Balance de agua en el secador (masa de aire seco necesaria).** El aire seco ($mas$) **no cambia** al atravesar el secador (solo gana agua, que se evapora de la torta), así que el agua total que gana el aire (entre su humedad de entrada $Y_6$ y de salida $Y_7$) debe ser igual al agua que se evaporó de la torta:

$$\text{agua evaporada} = mas\,(Y_7-Y_6)$$

$$mas = \dfrac{\text{agua evaporada}}{Y_7-Y_6} = \dfrac{4200}{0.015-0.006} = \dfrac{4200}{0.009} = 466667\ \text{kg aire seco/día}$$

**Paso 4 — Convertir a volumen usando el volumen húmedo del aire de entrada**, $V_{H(6)}=0.85$ m³/kg a.s. (leído también de la carta sicrométrica a 25 °C, $\%Y_R=30\%$):

$$\boxed{V_6 = mas\times V_{H(6)} = 466667\times 0.85 = 396667\ \text{m}^3/\text{día}}$$

### 4.7 Reflexión de cierre del ejercicio

Como pide la propia clase práctica: la analogía entre la composición de sistemas heterogéneos ($x$, $X$, $H$) y la de las mezclas vapor-gas del Tema 2 ($y_m$, $Y_m$, humedad) **no es casual**: en ambos casos hay una fase "portadora" (el líquido aquí, el gas allá) y una fase "transportada" (el sólido aquí, el vapor allá), y las mismas relaciones algebraicas ($x=X/(1+X)$, restrictivas de composición) se aplican porque la estructura matemática del problema es idéntica. La diferencia física clave: en las mezclas vapor-gas, la fase transportada puede *cambiar de fase* (evaporarse o condensar, según $P_s(T)$); en los sistemas heterogéneos, el sólido **no** cambia de fase — solo se separa mecánicamente del líquido (filtración) o se le retira líquido por evaporación (secado).

---

## 5. Ejercicio 4 (CP7) — Tecnología del café instantáneo (proceso base)

### 5.1 Por qué este es el ejercicio más complejo del bloque sin reacción química

Integra un percolador, un mezclador, un secador spray, un separador ciclónico, una prensa y un secador adicional — **13 corrientes numeradas**. El objetivo explícito de la clase práctica es "aplicar las técnicas del balance de masa a un proceso estacionario complejo" y "analizar los efectos de determinadas variables sobre otras". Antes de calcular nada, la propia clase práctica exige repetir, para **cada** posible frontera de sistema, el mismo análisis de grados de libertad hecho "a mano" en el Ejercicio 1 (sección 2.3) — aquí con más subsistemas posibles.

### 5.2 Enunciado y diagrama

El café molido y tostado (sin agua — solo materiales solubles e insolubles, por simplificación del enunciado) se carga con agua caliente (1.2 kg agua/kg café) a un percolador, de donde se extraen los solubles. El extracto se seca por aspersión (secador spray) para dar el producto; los residuos sólidos se decantan parcialmente (separador ciclónico + prensa) antes de desecharse.

$$\text{Café (1)}\ \{32.7\%\text{Insol.},\ 67.3\%\text{Sol.}\} \to \boxed{\text{PERCOLADOR}}$$

$$\to\ \text{(3) Solubles+Agua} \to \boxed{\text{Mezclador}} \to \text{(6) Extracto } \{35\%\text{Sol.},65\%\text{Agua}\} \to \boxed{\text{Secador Spray}} \to \begin{cases}\text{(7) Agua}\\\text{(8) Café instantáneo}\end{cases}$$

$$\to\ \text{(4)} \to \boxed{\text{Separador Ciclónico}} \to \begin{cases}\text{(5) Solubles+Agua, recircula al mezclador}\\ \text{(9) Lechada, } 20\%\text{Insol.} \to \boxed{\text{Prensa}} \to \begin{cases}\text{(11) Solución de desperdicio}\\\text{(10) Lechada, } 50\%\text{Insol.} \to \boxed{\text{Secador}} \to \begin{cases}\text{(12) Agua}\\\text{(13) Residuo, } 69\%\text{Insol.}\end{cases}\end{cases}\end{cases}$$

con (2) el agua caliente de carga al percolador. **BC = 1 kg de café.**

### 5.3 Parte (a) — Recuperación de solubles: eligiendo el sistema correcto

La clase práctica pide analizar tres posibles fronteras: **percolador-mezclador-secador** (sistema 1), **percolador-separador-prensa-secador** (sistema 2) y **percolador-mezclador-separador** (sistema 3). Sus grados de libertad:

| | Sistema 1 | Sistema 2 | Sistema 3 |
|---|---|---|---|
| # Incógnitas | 10 | 14 | 5 |
| # EPB | 3 | 3 | 3 |
| # ERC | 2 | 4 | 1 |
| # ERE | 1 | 1 | 1 |
| Total ecuaciones | 6 | 8 | 5 |
| **V** | **−4** | **−6** | **0** |

**Solo el sistema 3 (percolador-mezclador-separador) tiene $V=0$**: es el único resoluble en este punto, y es el que se usa a continuación.

**Balance de insolubles** (el insoluble no se pierde entre el café de entrada (1) y la lechada de salida (9): el extracto (6) no contiene insolubles, así que todo el insoluble del café termina, tarde o temprano, en la corriente (9)):

$$F_1\,x_{i1} = F_9\,x_{i9}$$

$$1(0.327) = F_9(0.2) \qquad\Rightarrow\qquad F_9 = \dfrac{0.327}{0.2} = 1.635\ \text{kg}$$

**Balance de solubles** (entran por (1); salen repartidos entre el extracto (6) y la lechada (9)):

$$F_1\,x_{s1} = F_6\,x_{s6}+F_9\,x_{s9}$$

$$1(0.673) = 0.35\,F_6+1.635\,x_{s9}\qquad(*)$$

**Balance global** (dato del enunciado: $F_2=1.2\,F_1$):

$$F_1+F_2 = F_6+F_9$$

$$F_6 = F_1+F_2-F_9 = 1+1.2-1.635 = 0.565\ \text{kg}$$

Con $F_6$ ya conocido, se puede calcular directamente cuántos solubles hay en cada corriente **sin** necesitar despejar $x_{s9}$ de la ecuación $(*)$:

$$\text{Solubles}_{(6)} = F_6\,x_{s6} = 0.565(0.35) = 0.1978\ \text{kg} \approx 0.198\ \text{kg}$$

$$\text{Solubles}_{(9)} = F_1\,x_{s1}-\text{Solubles}_{(6)} = 0.673-0.198 = 0.475\ \text{kg}$$

**Proporción recuperados : perdidos:**

$$\dfrac{\text{Solubles}_{(6)}}{\text{Solubles}_{(9)}} = \dfrac{0.198}{0.476} = 0.416$$

$$\boxed{\%\text{Recuperación} = \dfrac{\text{Solubles}_{(6)}}{\text{Solubles}_{(1)}}\times 100 = \dfrac{0.198}{0.673}\times 100 = 29.4\%}$$

**Conclusión (la que resalta el propio material):** la recuperación de café soluble es **pobre** — menos de un tercio del café soluble alimentado termina en el producto; el resto se pierde con el residuo húmedo desechado. Esto motiva la variante con recirculación resuelta en la sección 6.

### 5.4 Parte (b) — Aire de secado y agua a eliminar

**Selección del sistema.** La clase práctica pide analizar los sistemas **secador (4)**, **prensa-secador (5)** y **prensa (6)** de la segunda mitad del proceso:

| | Sistema 4 (secador) | Sistema 5 (prensa-secador) | Sistema 6 (prensa) |
|---|---|---|---|
| # Incógnitas | 7 | 7 | 6 |
| # EPB | 3 | 3 | 3 |
| # ERC | 2 | 2 | 2 |
| # ERE | 0 | 0 | 1 |
| Total ecuaciones | 5 | 5 | 6 |
| **V** | **−2** | **−2** | **0** |

**Solo la prensa sola tiene $V=0$**: se empieza por ahí.

**Balance en la prensa** ($F_9=1.635$ kg, ya conocido de la sección 5.3):

$$\text{Insolubles: } F_9\,x_{i9}=F_{10}\,x_{i10} \qquad\Rightarrow\qquad F_{10} = \dfrac{1.635(0.2)}{0.5} = 0.654\ \text{kg}$$

$$\text{Total: } F_9=F_{10}+F_{11} \qquad\Rightarrow\qquad F_{11}=1.635-0.654=0.981\ \text{kg}$$

**Ahora el secador ya es resoluble** ($F_{10}=0.654$ kg pasó de ser incógnita a ser dato):

$$\text{Insolubles: } F_{10}\,x_{i10}=F_{13}\,x_{i13} \qquad\Rightarrow\qquad F_{13} = \dfrac{0.654(0.5)}{0.69} = 0.474\ \text{kg}$$

$$\text{Total: } F_{10}=F_{12}+F_{13} \qquad\Rightarrow\qquad F_{12} = 0.654-0.474 = 0.18\ \text{kg}\qquad(\text{agua a evaporar en el secador})$$

**Flujo de aire húmedo.** Con las humedades leídas en la carta sicrométrica ($T=25\ °C$, $\%Y_R=40\%$ → $Y_6=0.008$; el secador es **adiabático**, así que la saturación adiabática hasta $\%Y_R=95\%$ da $Y_7=0.0115$):

$$mas = \dfrac{\text{agua evaporada}}{Y_7-Y_6} = \dfrac{0.18}{0.0115-0.008} = \dfrac{0.18}{0.0035} = 51.43\ \text{kg aire seco}$$

Con $V_{H(6)}=0.856$ m³/kg a.s. (leído de la carta a 25 °C, $\%Y_R=40\%$):

$$\boxed{V = mas\times V_{H(6)} = 51.43\times 0.856 = 44.02\ \text{m}^3}$$

**Agua a eliminar en el extracto** (la que sale como vapor del secador spray, corriente 7):

$$\text{H}_2\text{O}_{(7)} = \text{H}_2\text{O}_{(6)} = F_6\left(1-x_{s6}\right) = 0.565(1-0.35) = 0.367\ \text{kg}$$

$$\boxed{mas = 51.43\ \text{kg a.s.}\,,\qquad V_6=44.02\ \text{m}^3\,,\qquad \text{H}_2\text{O a eliminar}=0.367\ \text{kg}}$$

---

## 6. Ejercicio 5 (CP7) — Variante con recirculación (resuelta de forma independiente)

### 6.1 Por qué se plantea esta variante

El propio material docente propone, como cierre de la clase práctica: recircular la solución de desperdicio de la prensa de vuelta al percolador (para no perder esos solubles), operando con una lechada de mayor contenido de agua (40 % insolubles en vez de 50 %, para reducir la liberación de sabor amargo durante el prensado) y ajustando el secador para descargar sólidos con 62.5 % de insolubles. **El material fuente deja esta variante sin resolver numéricamente** ("orientar la solución de esta alternativa y verificar cómo aumenta el % de recuperación"). Se resuelve aquí completa, paso a paso.

### 6.2 Diagrama y datos

$$\text{Café (1)}\ \{32.7\%\text{Insol.}\} \to \boxed{\substack{\text{PERCOLADOR-}\\\text{SEPARADOR-}\\\text{MEZCLADOR (PSM)}}} \to \begin{cases}\text{(3) Extracto } \{35\%\text{Sol.},65\%\text{Agua}\}\\ \text{(4) Lechada } \{20\%\text{Insol.},28\%\text{Sol.},52\%\text{Agua}\} \to \boxed{\text{PRENSA}} \to \begin{cases}\text{(5) Solución de recirculación}\to\text{PSM}\\ \text{(6) } \{40\%\text{Insol.}\} \to \boxed{\text{SECADOR}} \to \begin{cases}\text{(7) Agua}\\ \text{(8) } \{62.5\%\text{Insol.}\}\end{cases}\end{cases}\end{cases}$$

con (2) agua caliente entrando al bloque combinado PSM junto con la recirculación (5).

**Hipótesis dada en el enunciado:** "considere iguales la proporción entre solubles y agua en las dos salidas de la prensa." Esto significa que la prensa separa mecánicamente el sólido insoluble del líquido madre **sin alterar la composición relativa de ese líquido**.

### 6.3 Paso 1 — Determinar la composición del líquido madre (razón solubles:agua)

En la lechada (4) que entra a la prensa, la fase líquida (sin contar el 20 % de insolubles) tiene: 28 % solubles y 52 % agua, es decir, dentro de esos 80 puntos porcentuales de líquido:

$$r = \dfrac{\text{solubles}}{\text{solubles}+\text{agua}} = \dfrac{28}{28+52} = \dfrac{28}{80} = 0.35$$

Esta razón (35 % solubles / 65 % agua **dentro del líquido**) es, por hipótesis del problema, la **misma** en ambas salidas de la prensa — y coincide, no por casualidad, con la composición del extracto (3): es literalmente el mismo "licor madre" del percolador circulando por toda la cadena.

### 6.4 Paso 2 — Composición de la torta húmeda que va al secador (6)

La corriente (6) tiene 40 % insolubles + 60 % de líquido con la razón $r=0.35$ hallada en el paso anterior:

$$x_{s(6)} = 0.60\times 0.35 = 0.21\ (21\%)\,,\qquad x_{H_2O(6)} = 0.60\times 0.65 = 0.39\ (39\%)$$

(coincide con la etiqueta "(6) 40 % Insolubles" del diagrama original, lo que confirma que la interpretación de la hipótesis es correcta).

### 6.5 Paso 3 — Composición del residuo final del secador (8)

El secador solo retira agua (sale por (7) como vapor puro); ni los insolubles ni los solubles se van por ahí, así que su **razón** insolubles:solubles se mantiene constante entre (6) y (8):

$$\dfrac{x_{i(6)}}{x_{s(6)}} = \dfrac{40}{21} = 1.9048$$

Con $x_{i(8)}=62.5\%$ dato del enunciado, se despeja $x_{s(8)}$:

$$x_{s(8)} = \dfrac{x_{i(8)}}{1.9048} = \dfrac{62.5}{1.9048} = 32.81\%$$

$$x_{H_2O(8)} = 100-62.5-32.81 = 4.69\%$$

### 6.6 Paso 4 — Balance global del proceso completo

Frontera: café (1) + agua caliente (2) → extracto (3) + agua evaporada (7) + residuo (8); la recirculación (5) queda **interna** (exactamente como en la sección 1.2). **BC = 1 kg café.**

**Balance de insolubles** (entran solo por (1); salen solo por (8), porque ni (3) ni (7) contienen insolubles):

$$F_1\,x_{i1} = F_8\,x_{i8}$$

$$1(0.327) = F_8(0.625) \qquad\Rightarrow\qquad F_8 = \dfrac{0.327}{0.625} = 0.5232\ \text{kg}$$

**Balance de solubles** (entran solo por (1); salen por (3) y por (8)):

$$F_1\,x_{s1} = F_3\,x_{s3}+F_8\,x_{s8}$$

$$0.673 = 0.35\,F_3 + 0.5232(0.3281)$$

Calculando el segundo término: $0.5232\times 0.3281 = 0.1717$.

$$0.673 = 0.35\,F_3+0.1717 \qquad\Rightarrow\qquad F_3 = \dfrac{0.673-0.1717}{0.35} = \dfrac{0.5013}{0.35} = 1.4324\ \text{kg}$$

### 6.7 Paso 5 — Porcentaje de recuperación con recirculación

$$\boxed{\%\text{Recuperación} = \dfrac{F_3\,x_{s3}}{F_1\,x_{s1}}\times 100 = \dfrac{1.4324(0.35)}{0.673}\times 100 = \dfrac{0.5013}{0.673}\times 100 = 74.5\%}$$

### 6.8 Verificación cualitativa: ¿de verdad aumenta la recuperación?

Sí, de manera muy notable: sube de **29.4 %** (proceso original, sección 5.3) a **74.5 %** (proceso con recirculación) — más del doble. La razón física es directa: al devolver la solución de desperdicio (5) —que en el proceso original se perdía por completo junto con el residuo— de vuelta al percolador, esos solubles tienen una **segunda oportunidad** de terminar en el extracto en vez de perderse definitivamente; solo se pierde la fracción de solubles que queda atrapada en la humedad residual del sólido finalmente descartado por (8), que ahora es proporcionalmente mucho menor.

> **Nota de alcance:** no se dispone, en los archivos de esta carpeta, del flujo de agua caliente (2) ni de las condiciones del aire de secado para esta variante (a diferencia del proceso original de la sección 5.4), así que el sistema queda determinado únicamente hasta donde permite el balance de materiales secos — $F_2$ y el agua evaporada $F_7$ quedan relacionados por una sola ecuación adicional (agua/total), pero no se pueden separar individualmente sin un dato extra (como la humedad del aire de secado). Esto es coherente con el propio objetivo del ejercicio, que pide verificar el efecto sobre la **recuperación**, no resolver el secador completo de esta variante.

---

## 7. Conclusiones de este bloque de clases prácticas

1. **Cuando un subsistema pequeño no es resoluble ($V<0$), hay que ampliar la frontera** hasta encontrar una que sí lo sea (el proceso completo, casi siempre), y resolver los subsistemas restantes **después**, usando los resultados ya obtenidos como nuevos datos — este patrón se repitió en los tres ejercicios de este documento (efecto por efecto en el Ejercicio 1; sistema por sistema en el Ejercicio 4).
2. **En un sistema con desvío, las composiciones no cambian en el punto de división** — solo los flujos totales se reparten. Esto simplifica mucho los balances en el punto de desvío (Ejercicio 2, sección 3.3) y en el punto de división de la variante con recirculación (Ejercicio 5).
3. **Las formas de expresar la composición en sistemas heterogéneos** ($x$, $X$, $C_s'$, $C_s$, $H$) son formalmente análogas a las de las mezclas vapor-gas del Tema 2, y se relacionan entre sí exactamente igual — dominar unas ayuda a dominar las otras.
4. **Comprobar los resultados por dos caminos independientes** (como se hizo en la sección 2.7, calculando $B$ tanto hacia adelante desde $A$ como hacia atrás desde $C$) es la forma más confiable de detectar errores antes de dar una respuesta por buena.
5. **La recirculación puede mejorar drásticamente el aprovechamiento de un proceso** (de 29.4 % a 74.5 % de recuperación en el Ejercicio 5) — un principio que reaparecerá, de forma aún más marcada, en el ejercicio de la planta de amoníaco de la Clase Práctica 9, 10, 11 y 12.

---

## Referencias / fuentes usadas en este documento

- [PIQ1 Clase practica 5 Operaciones consecutivas y desvio Triple efecto y concentrador de jugo.pdf](PIQ1%20Clase%20practica%205%20Operaciones%20consecutivas%20y%20desvio%20Triple%20efecto%20y%20concentrador%20de%20jugo.pdf) — Ejercicios 1 y 2 (secciones 2 y 3).
- [PIQ1 Clase practica 6 Sistemas heterogeneos.pdf](PIQ1%20Clase%20practica%206%20Sistemas%20heterogeneos.pdf) — Ejercicio 3 (sección 4).
- [PIQ1 Clase practica 7 Tecnologia del cafe instantaneo.pdf](PIQ1%20Clase%20practica%207%20Tecnologia%20del%20cafe%20instantaneo.pdf) y su [enunciado](PIQ1%20Clase%20practica%207%20Tecnologia%20del%20cafe%20instantaneo_enunciado.pdf) — Ejercicios 4 y 5 (secciones 5 y 6).
- [Conferencia 5 - Expresion General del Balance de Masa y Balance sin Reaccion Quimica.md](Conferencia%205%20-%20Expresion%20General%20del%20Balance%20de%20Masa%20y%20Balance%20sin%20Reaccion%20Quimica.md) — teoría y demostraciones de las fórmulas usadas aquí.
- [../TEMA 2/Conferencia 4 - Mediciones Termometricas, Carta Sicrometrica y Procesos.md](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md) — carta sicrométrica, usada en los Ejercicios 3 y 4.
