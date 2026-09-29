# Tema 1 — Conferencia 1: Sistemas de unidades y dimensiones de las magnitudes físicas

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuente principal:** [Conferencia 1 Tema 1 Plan E.pdf](Conferencia%201%20Tema%201%20Plan%20E.pdf)
> **Apoyo:** [Guia de estudio Tema 1.pdf](Guia%20de%20estudio%20Tema%201.pdf) · [PIQ1 Clase practica 1 Consistencia dimensional.pdf](PIQ1%20Clase%20practica%201%20Consistencia%20dimensional.pdf) · [Complementos/La importancia de las unidades.pdf](Complementos/La%20importancia%20de%20las%20unidades.pdf) · [Complementos/Human error caused loss of Mars orbiter.pdf](Complementos/Human%20error%20caused%20loss%20of%20Mars%20orbiter.pdf) · [Complementos/Sistema Internacional de Unidades INIMET.pdf](Complementos/Sistema%20Internacional%20de%20Unidades%20INIMET.pdf)
>
> Este documento explica, paso a paso y sin dar nada por sabido, todo lo que la Conferencia 1 exige: qué son las magnitudes y unidades, cuáles son los sistemas de unidades usados en ingeniería química, qué es la dimensión de una magnitud física, cómo se usa para comprobar la consistencia dimensional de una ecuación, y qué son los "pares redundantes" y las "constantes dimensionales". Cada ejemplo y cada ejercicio que la conferencia deja planteado (incluida la tarea) se resuelve aquí completo, con la aritmética verificada.

---

## 0. Por qué existe este tema (motivación)

Antes de entrar en definiciones, conviene entender **para qué sirve** todo esto, porque si no, las definiciones parecen arbitrarias.

### 0.1 El lugar de este tema dentro de la asignatura

La asignatura PIQ I organiza su contenido en 4 temas, con esta distribución horaria (C = conferencias, CP = clases prácticas, CPM = clases prácticas de máquina, h = horas):

| Tema | C | CP | CPM | Evaluación | Total |
|---|---|---|---|---|---|
| 1. Unidades y Dimensiones | 4 | 4 | 0 | 0 | 8 |
| 2. Mezclas Vapor-Gas | 4 | 4 | 0 | 0 | 8 |
| 3. Balance de Masa | 4 | 14 | 2 | 2 (PP) | 22 |
| 4. Balance de Energía | 6 | 19 | 4 | 1 (TC) | 30 |
| **Total** | **18** | **41** | **6** | **3** | **68** |

Tema 1 es corto (8 horas) pero es la **base operativa** de todo lo demás: en los Temas 3 y 4 (que concentran la mayoría de las horas) constantemente se mezclan datos dados en unidades distintas, y sin dominar la conversión de unidades y el chequeo de consistencia dimensional es imposible resolver correctamente un balance de masa o de energía.

Los objetivos instructivos de toda la asignatura son:

1. Dominar el Sistema Internacional de Unidades (SI) y otros sistemas de uso común en la industria química, así como las transformaciones entre ellos.
2. Aplicar patrones generales para resolver balances de masa y energía en situaciones reales, simples y complejas, principalmente en estado estacionario.
3. Trabajar con literatura técnica para localizar o estimar propiedades físicas y termodinámicas necesarias en los balances.

El **objetivo 1** es, literalmente, el contenido de este Tema 1.

### 0.2 Los cuatro tipos de expresiones matemáticas de la ingeniería química

Para describir cualquier fenómeno de interés en la industria química (evaluar, diseñar o mejorar un proceso o equipo) se necesitan cuatro tipos de expresiones matemáticas:

1. **Balance de masa (BM).**
2. **Balance de energía (BE).**
3. Ecuaciones de **equilibrio** físico y/o químico.
4. Ecuaciones de **transferencia** (efectos cinéticos: transferencia de calor, masa o cantidad de movimiento).

Esta asignatura se concentra en los dos primeros (BM y BE), porque son los cálculos que el ingeniero químico realiza con mayor frecuencia.

### 0.3 El problema concreto que motiva el tema

En estos cálculos aparece constantemente la necesidad de combinar datos que vienen en **unidades de sistemas distintos**. Un ejemplo típico es la ecuación de los gases ideales:

$$PV = nRT$$

Si en un problema real la constante universal de los gases se reporta como $R = 0.08206\ \dfrac{\text{atm·L}}{\text{mol·K}}$, pero el volumen del problema está dado en $\text{m}^3$ y la presión en $\text{kPa}$, **no se puede sustituir directamente**: las unidades de $P$ y $V$ no coinciden con las que exige la forma de $R$ que tenemos. Hay que convertir antes de calcular, o el resultado será numéricamente incorrecto aunque la ecuación esté bien planteada.

Como este tipo de desajuste es constante en la práctica, conviene tener un **método sistemático** para (a) organizar los sistemas de unidades y (b) convertir entre ellos sin errores. Ese método sistemático es, precisamente, el concepto de **dimensión**, que se desarrolla en esta conferencia.

### 0.4 Motivación adicional: cuando las unidades se manejan mal, hay consecuencias reales

Vale la pena leer completo el material de [Complementos/Human error caused loss of Mars orbiter.pdf](Complementos/Human%20error%20caused%20loss%20de%20Mars%20orbiter.pdf) y [Complementos/La importancia de las unidades.pdf](Complementos/La%20importancia%20de%20las%20unidades.pdf). En resumen:

- En 1999 la sonda **Mars Climate Orbiter** de la NASA se destruyó al entrar en la atmósfera de Marte demasiado bajo. La causa raíz, según la investigación oficial, fue que un contratista reportó el empuje de los propulsores en **libras-fuerza (lbf)**, mientras el software de navegación de la NASA asumía que el dato venía en **newtons (N)**. Como $1\ \text{lbf} = 4.45\ \text{N}$, el error se acumuló durante meses de correcciones de trayectoria hasta ser fatal.
- Una aerolínea canadiense sufrió un incidente ("Gimli Glider") cuando el personal en tierra confundió **litros con galones** al cargar combustible: el avión se quedó sin combustible en pleno vuelo (aterrizó de emergencia sin motores, planeando).
- Una empresa de energía confundió **kilovatios-hora (kWh)** con **termias** al cotizar un contrato, comprometiéndose a pagar 800 000 USD por gas que en realidad valía 50 000 USD.

La lección es siempre la misma: **una cantidad numérica sin su unidad correctamente identificada no significa nada**, y convertir mal entre sistemas de unidades puede tener consecuencias económicas o de seguridad graves. Esa es la razón de fondo por la que este tema, aunque parece "trivial" u operativo, se estudia con tanto rigor.

---

## 1. Objetivos de la conferencia

Tal como los plantea el texto de la conferencia:

- Conocer los diferentes **sistemas de unidades** empleados en la ingeniería química.
- Definir el concepto de **dimensión**.
- Conocer la aplicación del concepto de dimensión a la **consistencia dimensional** de ecuaciones.

---

## 2. Conceptos fundamentales

### 2.1 Magnitud física

**Definición:** una magnitud física es una característica "observable" de un sistema, que puede obtenerse por medio de los órganos de los sentidos o por instrumentos de medición.

Ejemplos: la masa, la longitud, el tiempo, la temperatura, la fuerza, la energía. Todas son cosas que, de un modo u otro, se pueden **medir**.

### 2.2 Unidad de medición

**Definición:** una unidad de medición es una cantidad arbitraria, tomada del total de la magnitud física que se quiere medir, a la que se le asigna el valor numérico "1" (la unidad).

En otras palabras: para medir una magnitud hace falta primero *elegir* una porción de referencia de esa magnitud y decir "esto vale 1". Todo lo demás se mide comparando contra esa referencia.

| Magnitud física | Unidad de medición (ejemplos) |
|---|---|
| Masa | kilogramo, libra |
| Tiempo | hora, segundo |

Nótese que **una misma magnitud física puede medirse con distintas unidades** (kilogramo o libra para la masa), lo cual es exactamente la raíz del problema que motivó el tema: distintas industrias, países y textos usan unidades distintas para la misma magnitud.

### 2.3 Símbolos usados para representar las magnitudes físicas

A lo largo de esta conferencia (y de las clases prácticas asociadas) se usan estos símbolos:

| Símbolo | Magnitud física |
|---|---|
| $L$ | Longitud |
| $M$ | Masa |
| $T$ | Temperatura |
| $\theta$ | Tiempo |
| $F$ | Fuerza |
| $E$ | Energía |

> **Aclaración importante (para que no confunda):** en el Sistema Internacional "oficial" y en la mayoría de los textos de física, suele usarse $t$ o $\theta$ para el tiempo y $T$ para la temperatura, o a veces al revés. En **este material** (siguiendo exactamente la notación del texto guía de la asignatura), **$T$ representa temperatura y $\theta$ representa tiempo**. Esta convención se mantiene igual en toda la Conferencia 1, la Conferencia 2 y las clases prácticas del Tema 1, así que conviene fijarla desde ahora para no interpretar mal ninguna fórmula dimensional que aparezca más adelante (por ejemplo, una velocidad se escribirá $L\theta^{-1}$, no $LT^{-1}$).

### 2.4 Unidades fundamentales (primarias) y unidades derivadas (secundarias)

Existen muchísimas magnitudes físicas (longitud, masa, tiempo, fuerza, energía, presión, viscosidad, etc.). Sería poco práctico definir una unidad independiente para cada una desde cero. Por eso las unidades de medición se dividen en dos grandes grupos:

- **Unidades fundamentales o primarias:** se establecen de forma independiente para un pequeño número de magnitudes físicas, elegidas arbitrariamente. Son el "punto de partida" del sistema.
- **Unidades derivadas o secundarias:** se establecen *a partir* de las unidades fundamentales, apoyándose en las leyes físicas que relacionan esas magnitudes con las fundamentales.

Por ejemplo, si elegimos masa, longitud y tiempo como fundamentales, entonces la **velocidad** (longitud/tiempo) y la **fuerza** (masa × longitud/tiempo², por la segunda ley de Newton) quedan automáticamente *derivadas*: no hace falta definirlas de manera independiente, se obtienen combinando las fundamentales según la ley física correspondiente.

**La elección de qué magnitudes son fundamentales es arbitraria** — y esa arbitrariedad es precisamente lo que da lugar a los distintos *sistemas de unidades* que se estudian a continuación.

---

## 3. Sistemas de unidades empleados en ingeniería

Un **sistema de unidades** queda definido por la elección de qué magnitudes físicas se toman como fundamentales. Los sistemas más empleados en ingeniería son:

| Sistema de unidades | Magnitudes fundamentales |
|---|---|
| Absoluto | $M\,L\,\theta\,T$ |
| Gravitacional | $F\,L\,\theta\,T$ |
| Ingeniería | $M\,F\,L\,\theta\,T$ |
| Energía | $M\,F\,E\,L\,\theta\,T$ |
| Internacional (SI) | $M\,L\,\theta\,T$ |

La **diferencia entre ellos radica exclusivamente en qué unidades se toman como fundamentales**. Analicemos cada uno:

### 3.1 Sistema Absoluto

Toma como fundamentales masa ($M$), longitud ($L$), tiempo ($\theta$) y temperatura ($T$). La fuerza y la energía **no** son fundamentales: se derivan mediante las leyes físicas (segunda ley de Newton para la fuerza, trabajo = fuerza × distancia para la energía). Es el sistema "clásico" de la mecánica newtoniana (unidades cgs: gramo, centímetro, segundo).

### 3.2 Sistema Gravitacional

Toma como fundamentales fuerza ($F$), longitud ($L$), tiempo ($\theta$) y temperatura ($T$). Aquí la **masa** no es fundamental — se deriva a partir de la fuerza mediante la segunda ley de Newton (más adelante se muestra la deducción completa). Este sistema es común en ingeniería mecánica/civil cuando se trabaja directamente con fuerzas medidas (por ejemplo, con el kilogramo-fuerza, $kgf$).

### 3.3 Sistema de Ingeniería

Toma como fundamentales **tanto** la masa ($M$) **como** la fuerza ($F$), además de $L$, $\theta$, $T$. Esta es una elección "cómoda" para la práctica de ingeniería (se puede hablar de libras-masa y libras-fuerza por separado), pero tiene un costo: como masa y fuerza están relacionadas entre sí por una ley física (F = ma), el hecho de tratarlas *ambas* como independientes genera una inconsistencia aparente que hay que corregir con una **constante dimensional** (esto se explica en la sección 5).

### 3.4 Sistema de Energía

Toma como fundamentales masa ($M$), fuerza ($F$) **y** energía ($E$), además de $L$, $\theta$, $T$. Es el sistema con más magnitudes fundamentales de los cinco, y por eso es el que más "pares redundantes" genera (dos, en vez de uno): al tratar simultáneamente masa, fuerza y energía como independientes, aparecen dos relaciones físicas "de más" que hay que corregir con constantes dimensionales.

### 3.5 Sistema Internacional (SI)

Toma como fundamentales masa ($M$), longitud ($L$), tiempo ($\theta$) y temperatura ($T$) — la misma estructura que el sistema Absoluto. Es el sistema legal de medidas adoptado internacionalmente y el que se emplea preferentemente en la ciencia y en la mayoría de la industria mundial (con la notable excepción histórica de EE.UU.).

Formalmente, el SI (según el documento [Complementos/Sistema Internacional de Unidades INIMET.pdf](Complementos/Sistema%20Internacional%20de%20Unidades%20INIMET.pdf), que recoge la normativa cubana basada en las resoluciones de la Conferencia General de Pesas y Medidas) define **siete** magnitudes básicas, no solo cuatro — pero para los cálculos mecánicos y térmicos típicos de un balance de masa y energía, solo se usan activamente cuatro de ellas:

| Magnitud básica SI | Unidad SI | Símbolo | ¿Se usa en este curso? |
|---|---|---|---|
| Longitud | metro | m | Sí ($L$) |
| Masa | kilogramo | kg | Sí ($M$) |
| Tiempo | segundo | s | Sí ($\theta$) |
| Temperatura termodinámica | kelvin | K | Sí ($T$) |
| Corriente eléctrica | ampere | A | No (fuera del alcance de este curso) |
| Cantidad de sustancia | mol | mol | Aparece indirectamente (ver nota abajo) |
| Intensidad luminosa | candela | cd | No |

> **Nota sobre el "mol" y las magnitudes fundamentales de este curso:** el SI oficial trata la cantidad de sustancia (mol) como una octava... perdón, séptima magnitud básica, independiente de la masa. Sin embargo, en el marco simplificado que usan estas conferencias (pensado para cálculos de ingeniería con $M, L, \theta, T, F, E$), no se introduce una dimensión separada para "cantidad de sustancia": cuando aparece una magnitud "molar" (como la capacidad calorífica molar), su dimensión se construye tratando los moles como si tuvieran dimensión de masa ($M$), ya que la masa molar es solo un factor de conversión (no una nueva magnitud fundamental independiente). Esto se ve explícitamente en la sección 4.4 más abajo, al calcular la dimensión de $Cp$.

Para dar una imagen más completa del SI (útil para el resto de la carrera, aunque no se necesite todo en este tema), estos son los **prefijos multiplicativos** oficiales, tomados de [Complementos/La importancia de las unidades.pdf](Complementos/La%20importancia%20de%20las%20unidades.pdf):

| Factor | Prefijo | Símbolo | | Factor | Prefijo | Símbolo |
|---|---|---|---|---|---|---|
| $10^{24}$ | yotta | Y | | $10^{-1}$ | deci | d |
| $10^{21}$ | zetta | Z | | $10^{-2}$ | centi | c |
| $10^{18}$ | exa | E | | $10^{-3}$ | mili | m |
| $10^{15}$ | peta | P | | $10^{-6}$ | micro | µ |
| $10^{12}$ | tera | T | | $10^{-9}$ | nano | n |
| $10^{9}$ | giga | G | | $10^{-12}$ | pico | p |
| $10^{6}$ | mega | M | | $10^{-15}$ | femto | f |
| $10^{3}$ | kilo | k | | $10^{-18}$ | atto | a |
| $10^{2}$ | hecto | h | | $10^{-21}$ | zepto | z |
| $10^{1}$ | deca | da | | $10^{-24}$ | yocto | y |

Un detalle importante que señala el mismo documento: **el exponente de una unidad con prefijo afecta también al prefijo**. Es decir, $\text{km}^2$ significa $(\text{km})^2 = \text{km}\cdot\text{km} = 10^6\ \text{m}^2$ (un millón de metros cuadrados), **no** $10^3\ \text{m}^2$. Este tipo de detalle "trivial" es exactamente el que, mal aplicado, provoca los errores costosos mencionados en la sección 0.4.

### 3.6 Ejemplo guiado: obtener las unidades de fuerza y energía del SI a partir de $F = ma$

La conferencia propone este ejercicio de forma explícita: usar la segunda ley de Newton para deducir las unidades derivadas de fuerza y energía en el SI. Vamos a resolverlo completo.

**Paso 1 — unidades fundamentales del SI:** masa en kilogramos (kg), longitud en metros (m), tiempo en segundos (s).

**Paso 2 — segunda ley de Newton:** $F = m\,a$, donde $a$ (aceleración) tiene unidades de $\text{longitud}/\text{tiempo}^2 = \text{m/s}^2$.

**Paso 3 — sustituir unidades:**
$$[F] = [m][a] = \text{kg}\cdot\dfrac{\text{m}}{\text{s}^2} = \text{kg·m/s}^2$$

Esta combinación de unidades recibe un nombre propio: el **newton (N)**. Por definición, $1\ \text{N} \equiv 1\ \text{kg·m/s}^2$. Nótese que en el SI **no hace falta ninguna constante de conversión**: la fuerza queda automáticamente en newtons al usar kg, m y s — esto es justamente lo que distingue al SI (y al sistema Absoluto) de los sistemas de Ingeniería y de Energía, como se explicará en la sección 5.

**Paso 4 — energía como trabajo (fuerza × distancia):**
$$[E] = [F][L] = (\text{kg·m/s}^2)(\text{m}) = \text{kg·m}^2/\text{s}^2$$

Esta combinación recibe el nombre de **joule (J)**: $1\ \text{J} \equiv 1\ \text{kg·m}^2/\text{s}^2$.

Este pequeño ejercicio ilustra exactamente el mecanismo general de las **unidades derivadas**: se combinan las fundamentales de acuerdo con la ley física correspondiente (aquí, $F=ma$ y trabajo $=F\cdot L$), y si el sistema está bien construido (como el SI), el resultado no necesita factores de ajuste.

---

## 4. Dimensión de las magnitudes físicas

### 4.1 Definición formal

Ya vimos que las unidades derivadas se construyen a partir de las fundamentales usando leyes físicas. La **fórmula dimensional** (o simplemente **dimensión**) de una magnitud física $B$ es precisamente la expresión que muestra *cómo* se relaciona $B$ con las magnitudes fundamentales $A_i$ de un sistema dado:

$$[B] = [A_1]^{n_1}\,[A_2]^{n_2}\,\cdots\,[A_k]^{n_k}$$

Es decir: la dimensión de $B$ es un producto de potencias de las magnitudes fundamentales del sistema. Los corchetes $[\ \cdot\ ]$ se leen "la dimensión de".

Dos observaciones clave de esta definición:

1. **La dimensión de una magnitud depende del sistema de unidades elegido**, porque depende de cuáles son las magnitudes fundamentales $A_i$. La misma magnitud física (por ejemplo, la energía) puede tener una fórmula dimensional distinta según el sistema (fundamental en el sistema de Energía, pero derivada — combinación de $F$ y $L$, o de $M$, $L$ y $\theta$ — en los demás).
2. La dimensión **no** es lo mismo que la unidad concreta (kg, N, J...); es la *estructura* de esa unidad en términos de las magnitudes fundamentales.

### 4.2 Ejemplo: dimensión de la masa en el sistema Gravitacional

En el sistema Gravitacional, la masa **no** es fundamental (solo lo son $F, L, \theta, T$), así que hay que derivarla usando la segunda ley de Newton:

$$f = m\,a = m\,l\,t^{-2}$$

(aquí, siguiendo la notación algebraica del texto, se usan letras minúsculas para los valores y $t$ para el símbolo genérico de tiempo dentro de la fórmula de aceleración — recordando que la dimensión de tiempo es $\theta$). Despejando la masa:

$$m = f\,l^{-1}\,t^{2} \quad\Longrightarrow\quad [M] = F\,\theta^{2}\,L^{-1}$$

Esta es la **dimensión de la masa en el sistema gravitacional**: no es "$M$" (símbolo fundamental), sino una combinación de $F$, $\theta$ y $L$. Esto tiene sentido físico: si la fuerza es lo fundamental, entonces la masa —que mide "cuánta fuerza hace falta para producir cierta aceleración"— se define en términos de esa fuerza.

### 4.3 Ejemplo: dimensión de la energía en cada sistema

**a) En los sistemas de Ingeniería y Gravitacional** (donde $F$ y $L$ son fundamentales), se usa la relación trabajo = fuerza × distancia (la conferencia la llama "ley de la palanca"):

$$e = f\,l \quad\Longrightarrow\quad [E] = F\,L$$

**b) En el sistema Absoluto** (donde $M$, $L$, $\theta$ son fundamentales, no $F$), hay que sustituir también la fuerza en función de sus fundamentales:

$$e = f\,l\,,\qquad f = m\,l\,t^{-2} \quad\Longrightarrow\quad e = m\,l^{2}\,t^{-2} \quad\Longrightarrow\quad [E] = M\,L^{2}\,\theta^{-2}$$

**c) En el sistema Internacional**, al tener la misma estructura fundamental que el sistema Absoluto ($M,L,\theta,T$), se obtiene exactamente el mismo resultado: $[E] = M\,L^{2}\,\theta^{-2}$ (que es justamente lo que vimos en el paso 4 de la sección 3.6: $\text{kg·m}^2/\text{s}^2$).

**d) En el sistema de Energía**, la energía es fundamental por definición: $[E] = E$.

### 4.4 Ejercicio resuelto: dimensión de la capacidad calorífica ($C_p$) en los cinco sistemas

La conferencia deja este ejercicio planteado ("obtenga para la capacidad calorífica las dimensiones que para cada sistema aparecen en la tabla 1.3 del texto"), remitiendo a una tabla del libro de texto (Cruz/Pons) que no forma parte de los archivos de esta carpeta. Sin embargo, **sí podemos resolverlo por completo aplicando el mismo método de las secciones 4.2 y 4.3**, y el resultado puede verificarse de forma independiente porque coincide exactamente con los valores que usa la [Clase Práctica 1](PIQ1%20Clase%20practica%201%20Consistencia%20dimensional.pdf) para $C_p$ (capacidad calorífica **molar**) en sus ejercicios de consistencia dimensional.

**Idea física:** la capacidad calorífica molar mide la energía necesaria para cambiar la temperatura de **una cantidad de sustancia** (moles) en una unidad de temperatura:

$$C_p = \dfrac{\text{energía}}{\text{cantidad de sustancia}\times\text{variación de temperatura}}$$

Como se explicó en la nota de la sección 3.5, en este marco de trabajo la "cantidad de sustancia" (moles) se trata dimensionalmente como si tuviera dimensión de masa $M$ (la masa molar es solo el factor numérico de conversión entre kg y kmol, no una magnitud fundamental adicional). Entonces:

$$[C_p] = \dfrac{[E]}{M\cdot T}$$

Sustituyendo la dimensión de $E$ que ya calculamos para cada sistema en la sección 4.3:

| Sistema | $[E]$ | $[M]$ | $[C_p] = [E]/(M\cdot T)$ |
|---|---|---|---|
| Absoluto | $ML^{2}\theta^{-2}$ | $M$ (fundamental) | $L^{2}\theta^{-2}T^{-1}$ |
| Internacional | $ML^{2}\theta^{-2}$ | $M$ (fundamental) | $L^{2}\theta^{-2}T^{-1}$ |
| Gravitacional | $FL$ | $F\theta^{2}L^{-1}$ (derivada, sección 4.2) | $\dfrac{FL}{F\theta^{2}L^{-1}\cdot T} = L^{2}\theta^{-2}T^{-1}$ |
| Ingeniería | $FL$ | $M$ (fundamental) | $F\,L\,M^{-1}\,T^{-1}$ |
| Energía | $E$ (fundamental) | $M$ (fundamental) | $E\,M^{-1}\,T^{-1}$ |

Los resultados de Internacional ($L^{2}\theta^{-2}T^{-1}$) y de Energía ($EM^{-1}T^{-1}$) **coinciden exactamente** con los que usa la Clase Práctica 1 al comprobar la consistencia de la ecuación termodinámica $\left(\frac{\partial T}{\partial P}\right) = \frac{T}{C_p}\left(\frac{\partial V}{\partial T}\right)$ — lo cual confirma que el procedimiento es correcto.

Vale la pena notar algo interesante en la tabla: en Absoluto, Internacional **y** Gravitacional se obtiene la *misma* dimensión para $C_p$ ($L^2\theta^{-2}T^{-1}$), mientras que en Ingeniería y Energía aparece explícitamente la fuerza o la energía como magnitud independiente. Esto es un primer indicio de un patrón que se va a formalizar en la próxima sección: **los sistemas Absoluto, Gravitacional e Internacional nunca mezclan $F$ y $M$ (o $E$) como fundamentales simultáneamente, por lo que sus fórmulas dimensionales son "limpias"; en cambio, Ingeniería y Energía sí las mezclan, lo que genera complicaciones** que hay que resolver con constantes dimensionales.

### 4.5 Para qué sirve la dimensión

Dos usos fundamentales, mencionados explícitamente por la conferencia:

1. **Control de exactitud de los cálculos:** solo se pueden sumar, restar o igualar magnitudes que tengan la **misma** fórmula dimensional. Si en un cálculo intermedio aparece, por ejemplo, "masa + longitud", eso es una señal inequívoca de que hay un error, porque $M \neq L$.
2. **Comprobación de la consistencia dimensional de ecuaciones teóricas** (sección 5) y **análisis dimensional** para obtener ecuaciones empíricas (esto se desarrolla en la Conferencia 2).

También es importante remarcar: **la fórmula dimensional de una magnitud física es función de las variables fundamentales del sistema empleado**. Por tanto, la misma magnitud (energía, capacidad calorífica, lo que sea) puede tener una fórmula dimensional distinta según el sistema, como acabamos de comprobar con $C_p$.

---

## 5. Consistencia dimensional de ecuaciones teóricas

### 5.1 Definición

Se llama **ecuación teórica** a aquella que se obtiene mediante un desarrollo matemático formal a partir de leyes físicas (no por ajuste experimental de datos). **Toda ecuación teórica es, por construcción, dimensionalmente consistente**: es decir, todos sus términos tienen la misma fórmula dimensional.

**Una ecuación es dimensionalmente consistente cuando todos sus términos tienen la misma fórmula dimensional.**

### 5.2 El problema de los pares redundantes

Aquí aparece un matiz importante: aunque una ecuación teórica *siempre* es consistente en el sentido físico, al comprobarla dimensionalmente en un sistema de unidades concreto **puede parecer que no lo es**. Esto ocurre cuando el sistema de unidades elegido tomó como fundamentales dos (o más) magnitudes físicas que **están relacionadas entre sí por una ley física** (por ejemplo, fuerza y masa, relacionadas por $F=ma$). A esa situación se le llama **par redundante**.

¿Por qué pasa esto? Porque si $F$ y $M$ son *ambas* fundamentales (como en el sistema de Ingeniería), el sistema está tratando como "independientes" dos magnitudes que en realidad la física vincula mediante $F=ma$. Esa duplicidad hace que, al sustituir dimensiones en una ecuación teórica, los exponentes de $F$ y de $M\,L\,\theta^{-2}$ (que es "lo mismo" que $F$, según Newton) no encajen automáticamente, y la ecuación *parezca* inconsistente aunque no lo sea.

**La solución** es introducir una **constante dimensional** adecuada: una constante cuyo *valor numérico* depende del sistema de unidades (a diferencia de las constantes "puras" como $\pi$), y cuya *dimensión* es exactamente la que hace falta para "arreglar" el desajuste entre el par redundante.

La conferencia identifica tres pares redundantes posibles y sus constantes asociadas:

| Par redundante | Constante | Dimensión de la constante | Sistema(s) donde ocurre |
|---|---|---|---|
| $F$–$M$ | $g_c$ | $M\,L\,/\,F\,\theta^{2}$ | Ingeniería, Energía |
| $F$–$E$ | $J$ | $F\,L\,/\,E$ | Energía |
| $E$–$M$ | $K = g_c\,J$ | $M\,L^{2}\,/\,E\,\theta^{2}$ | Energía |

Nótese cómo esto explica exactamente por qué el sistema de **Ingeniería** (que hace fundamentales a $M$ *y* $F$) solo necesita la constante $g_c$, mientras que el sistema de **Energía** (que hace fundamentales a $M$, $F$ *y* $E$ simultáneamente) necesita las tres constantes, porque ahí se forman **dos** pares redundantes independientes ($F$–$E$ y $E$–$M$; el par $F$–$M$ de este sistema se resuelve con la misma $g_c$).

### 5.3 ¿Por qué Absoluto, Gravitacional e Internacional no necesitan constantes?

Respondiendo la pregunta que la propia conferencia deja planteada ("¿necesitan los sistemas absoluto, internacional y gravitacional emplear las constantes dimensionales?"): **no**, y la razón es directa a partir de la tabla de sistemas de la sección 3:

- **Absoluto** e **Internacional**: fundamentales $M,L,\theta,T$. Ni $F$ ni $E$ son fundamentales — ambas se derivan limpiamente a partir de $M,L,\theta$ sin ambigüedad. No hay dos magnitudes fundamentales relacionadas entre sí por una ley física: no hay par redundante.
- **Gravitacional**: fundamentales $F,L,\theta,T$. Aquí $M$ no es fundamental (se deriva de $F$, como vimos en la sección 4.2). De nuevo, solo una de las dos magnitudes relacionadas por $F=ma$ es fundamental — no hay redundancia.

En cambio, **Ingeniería** hace fundamentales a $M$ *y* $F$ al mismo tiempo (de ahí el par $F$–$M$), y **Energía** hace fundamentales a $M$, $F$ *y* $E$ al mismo tiempo (de ahí los dos pares). Esta es la causa raíz de por qué estos dos sistemas requieren constantes dimensionales y los otros tres no.

> Los valores numéricos concretos de estas constantes (por ejemplo, $g_c = 9.81\ \dfrac{\text{kg·m}}{\text{kgf·s}^2}$ o $g_c = 32.17\ \dfrac{\text{lb·pie}}{\text{lbf·s}^2}$, según las unidades específicas) se encuentran tabulados en el texto base de la asignatura (Cruz/Pons, epígrafe 3.8), el cual no forma parte de los PDF disponibles en esta carpeta — conviene consultarlo directamente si se necesita el valor numérico para un cálculo concreto. La [Clase Práctica 1](PIQ1%20Clase%20practica%201%20Consistencia%20dimensional.pdf), sin embargo, sí usa y reporta el valor $g_c = 9.81\ \text{kg·m/(kgf·s}^2)$ en sus ejercicios numéricos, que puede tomarse como referencia directa.

---

## 6. Ejemplos resueltos de comprobación de consistencia dimensional

A continuación se resuelven, completos y explicados, los tres ejemplos que deja planteados la conferencia (los dos primeros ya vienen resueltos en el material original; aquí se presentan con cada paso razonado en palabras; el tercero es la **tarea** y se resuelve íntegramente).

### 6.1 Ejemplo 1: $f = m\,a$ (segunda ley de Newton)

**En el sistema Internacional:**

$$[f] = M\,L\,\theta^{-2}\,,\qquad [m] = M\,,\qquad [a] = L\,\theta^{-2}$$

Sustituyendo en la ecuación:

$$M\,L\,\theta^{-2} \overset{?}{=} M\cdot L\,\theta^{-2} = M\,L\,\theta^{-2}$$

Ambos lados coinciden exactamente ⟹ **consistente**, sin necesidad de ninguna constante. Esto confirma lo dicho en la sección 5.3: el SI no genera pares redundantes.

**En el sistema de Energía:**

$$[f] = F\,,\qquad [m] = M\,,\qquad [a] = L\,\theta^{-2}$$

Sustituyendo:

$$F \overset{?}{=} M\cdot L\,\theta^{-2}$$

El lado izquierdo es $F$ (dimensión fundamental) y el lado derecho es $M\,L\,\theta^{-2}$: **no son la misma expresión simbólica**, aunque sabemos por física que ambas representan "fuerza". Esto es exactamente el par redundante $F$–$M$: el sistema de Energía trata a $F$ y a $M$ como independientes, así que $F$ y $M L\theta^{-2}$ no se cancelan automáticamente. **Aparentemente no es consistente.**

**Corrección con $g_c$:** como $[g_c] = M\,L\,/(F\,\theta^{2})$, se reescribe la ecuación como

$$f = \dfrac{m\,a}{g_c}$$

Comprobando dimensiones:

$$F \overset{?}{=} \dfrac{M\cdot L\,\theta^{-2}}{M\,L\,/(F\,\theta^{2})} = M\,L\,\theta^{-2}\cdot\dfrac{F\,\theta^{2}}{M\,L} = F$$

Ahora sí: $F = F$ ⟹ **consistente**. Esta es, de hecho, la forma general y muy conocida en ingeniería de la segunda ley de Newton cuando se usan libra-masa y libra-fuerza simultáneamente: $F = \dfrac{m\,a}{g_c}$.

### 6.2 Ejemplo 2: $w = f\,l$ (trabajo)

**En el sistema Internacional:**

$$[w] = [E] = M\,L^{2}\,\theta^{-2}\,,\qquad [f] = M\,L\,\theta^{-2}\,,\qquad [l] = L$$

Sustituyendo:

$$M\,L^{2}\,\theta^{-2} \overset{?}{=} (M\,L\,\theta^{-2})\cdot L = M\,L^{2}\,\theta^{-2}$$

Coinciden ⟹ **consistente** (sin constantes, de nuevo por ser el SI).

**En el sistema de Energía:**

$$[w] = [E] = E\,,\qquad [f] = F\,,\qquad [l] = L$$

Sustituyendo:

$$E \overset{?}{=} F\cdot L$$

Aquí aparece el par redundante $F$–$E$: tanto $E$ como $F$ son fundamentales en este sistema, así que $E$ y $F\,L$ no se cancelan por sí solos. **Aparentemente no es consistente.**

**Corrección con $J$:** como $[J] = F\,L\,/\,E$, se reescribe la ecuación dividiendo entre $J$:

$$w = \dfrac{f\,l}{J}$$

Comprobando:

$$E \overset{?}{=} \dfrac{F\cdot L}{F\,L\,/\,E} = F\,L\cdot\dfrac{E}{F\,L} = E$$

**Consistente.** (Este es, físicamente, el conocido "equivalente mecánico del calor": $J$ convierte unidades de trabajo mecánico en unidades de calor cuando ambas se manejan como fundamentales independientes.)

### 6.3 Tarea resuelta: $E_c = \dfrac{1}{2}\,m\,v^{2}$ (energía cinética)

La conferencia deja esta ecuación como tarea, sin resolverla en el material. A continuación se resuelve completa en **los cinco sistemas de unidades**, siguiendo exactamente el mismo procedimiento de los ejemplos anteriores. El factor $\frac{1}{2}$ es un número puro (adimensional) y no afecta el análisis dimensional.

$$[E_c] \overset{?}{=} [m]\,[v]^{2}$$

**Sistema Internacional:** $[E_c]=ML^2\theta^{-2}$ (sección 4.3-c), $[m]=M$, $[v]=L\theta^{-1}$.

$$ML^2\theta^{-2} \overset{?}{=} M\cdot (L\theta^{-1})^2 = M\,L^2\,\theta^{-2}\ \checkmark\quad\textbf{Consistente (sin constante).}$$

**Sistema Absoluto:** idéntica estructura fundamental que el Internacional ⟹ mismo resultado, **consistente sin constante**.

**Sistema Gravitacional:** $[E_c]=FL$ (sección 4.3-a), $[m]=F\theta^2L^{-1}$ (sección 4.2), $[v]=L\theta^{-1}$.

$$FL \overset{?}{=} (F\theta^2L^{-1})\cdot(L\theta^{-1})^2 = F\theta^2L^{-1}\cdot L^2\theta^{-2} = FL\ \checkmark\quad\textbf{Consistente (sin constante).}$$

Esto confirma, con un tercer ejemplo, que el sistema Gravitacional tampoco genera pares redundantes.

**Sistema de Ingeniería:** $[E_c]=FL$, $[m]=M$ (aquí sí es fundamental), $[v]=L\theta^{-1}$.

$$FL \overset{?}{=} M\cdot(L\theta^{-1})^2 = M\,L^2\,\theta^{-2}$$

$F\,L$ y $M\,L^2\,\theta^{-2}$ no son la misma expresión simbólica ⟹ **aparentemente no consistente** (par redundante $F$–$M$, esperado, porque Ingeniería hace fundamentales a $M$ y a $F$ simultáneamente). Se corrige dividiendo entre $g_c$:

$$E_c = \dfrac{m\,v^2}{2\,g_c}$$

Comprobando: $\dfrac{M\,L^2\,\theta^{-2}}{M L/(F\theta^2)} = M L^2\theta^{-2}\cdot\dfrac{F\theta^2}{ML} = F L\ \checkmark$ ⟹ **consistente.**

**Sistema de Energía:** $[E_c]=E$ (fundamental), $[m]=M$ (fundamental), $[v]=L\theta^{-1}$.

$$E \overset{?}{=} M\cdot(L\theta^{-1})^2 = M\,L^2\,\theta^{-2}$$

$E$ y $M L^2\theta^{-2}$ no coinciden simbólicamente ⟹ **aparentemente no consistente**. Aquí el par redundante involucrado es $E$–$M$ (no $F$–$M$, porque en esta ecuación no aparece $F$ explícitamente), así que la constante adecuada es $K = g_c\,J$, con $[K] = M\,L^2/(E\,\theta^2)$. Se corrige:

$$E_c = \dfrac{m\,v^2}{2\,K}$$

Comprobando: $\dfrac{M L^2\theta^{-2}}{ML^2/(E\theta^2)} = M L^2\theta^{-2}\cdot\dfrac{E\theta^2}{ML^2} = E\ \checkmark$ ⟹ **consistente.**

**Resumen de la tarea:**

| Sistema | ¿Consistente directamente? | Constante necesaria | Ecuación corregida |
|---|---|---|---|
| Absoluto | Sí | — | $E_c=\tfrac12 mv^2$ |
| Internacional | Sí | — | $E_c=\tfrac12 mv^2$ |
| Gravitacional | Sí | — | $E_c=\tfrac12 mv^2$ |
| Ingeniería | No (aparente) | $g_c$ (par $F$–$M$) | $E_c=\dfrac{mv^2}{2g_c}$ |
| Energía | No (aparente) | $K=g_cJ$ (par $E$–$M$) | $E_c=\dfrac{mv^2}{2K}$ |

Este resultado es totalmente coherente con la conclusión general de la conferencia (sección 5.3): solo Ingeniería y Energía requieren constantes, y solo para los pares redundantes que efectivamente involucra cada ecuación.

---

## 7. Preguntas de repaso (respondidas)

La propia conferencia cierra con una serie de preguntas guía. Se responden aquí de forma explícita, a modo de resumen:

**¿Podría citar algunos de los sistemas de unidades usados en ingeniería química?**
Absoluto, Gravitacional, de Ingeniería, de Energía e Internacional (SI). La diferencia entre ellos radica en qué magnitudes se toman como fundamentales (ver tabla de la sección 3).

**¿Qué es la fórmula dimensional?**
Es la expresión que relaciona cualquier magnitud física con las magnitudes definidas como fundamentales en un sistema dado, a través de las leyes físicas que las vinculan: $[B]=[A_1]^{n_1}[A_2]^{n_2}\cdots[A_k]^{n_k}$.

**Mencione alguna aplicación de la dimensión.**
(1) Comprobar la consistencia dimensional de ecuaciones teóricas; (2) controlar la exactitud de los cálculos (solo se suman/igualan magnitudes de igual dimensión); (3) —como se verá en la Conferencia 2— servir de base al análisis dimensional para obtener ecuaciones empíricas.

**¿Qué son los pares redundantes y qué constantes se usan para eliminarlos?**
Son parejas de magnitudes físicas que un sistema de unidades trata como fundamentales de forma simultánea, a pesar de estar relacionadas entre sí por una ley física, lo que genera una inconsistencia dimensional aparente. Los tres pares posibles en este curso y sus constantes son: $F$–$M$ → $g_c$; $F$–$E$ → $J$; $E$–$M$ → $K=g_cJ$ (ver tabla de la sección 5.2).

---

## 8. Para seguir estudiando

Estas son las orientaciones de estudio que deja la conferencia, junto con una precisión sobre qué material de esta carpeta las cubre y cuál requiere el libro de texto:

- **Texto tomo I, páginas 5–27** (Cruz, Luis; Pons, Antonio. *Introducción a la Ingeniería Química*). **Este libro no está incluido entre los archivos de esta carpeta**; para revisar la Tabla 1.1 (sistemas de unidades detallados), la Tabla 1.3 (dimensiones de magnitudes físicas comunes) y los ejemplos numerados 1.2 y 1.3 (páginas 21–23), es necesario consultar el texto físico o su versión digital si se dispone de ella.
- **Epígrafe 1.8** del texto (valores numéricos de $g_c$, $J$ y $K$ en distintas unidades).
- **Traer el tomo I del texto a la clase práctica**, según indica la conferencia.
- Dentro de esta carpeta, el material que **sí** complementa directamente lo anterior es: [PIQ1 Clase practica 1 Consistencia dimensional.pdf](PIQ1%20Clase%20practica%201%20Consistencia%20dimensional.pdf) (tres ejercicios adicionales de consistencia dimensional, totalmente resueltos, incluyendo cálculos numéricos con $g_c$) y los documentos de [Complementos](Complementos/) para el contexto histórico y la importancia práctica del SI.

La conferencia cierra anunciando el siguiente tema: además de comprobar la consistencia de ecuaciones *teóricas*, la dimensión tiene otra aplicación — obtener ecuaciones *empíricas* a partir de las variables involucradas en un fenómeno, mediante la técnica llamada **análisis dimensional**. Eso, junto con la **conversión de unidades**, es el contenido completo de la Conferencia 2 (ver [Conferencia 2 - Conversión de Unidades y Análisis Dimensional.md](Conferencia%202%20-%20Conversion%20de%20Unidades%20y%20Analisis%20Dimensional.md)).

---

## Referencias / fuentes usadas en este documento

- [Conferencia 1 Tema 1 Plan E.pdf](Conferencia%201%20Tema%201%20Plan%20E.pdf) — fuente principal del contenido teórico y de los ejemplos y la tarea.
- [Guia de estudio Tema 1.pdf](Guia%20de%20estudio%20Tema%201.pdf) — objetivos, conocimientos y habilidades del tema.
- [PIQ1 Clase practica 1 Consistencia dimensional.pdf](PIQ1%20Clase%20practica%201%20Consistencia%20dimensional.pdf) — verificación cruzada de la dimensión de $C_p$ y de los valores numéricos de $g_c$.
- [Complementos/La importancia de las unidades.pdf](Complementos/La%20importancia%20de%20las%20unidades.pdf) — motivación histórica, tabla de prefijos SI, casos reales de error de unidades.
- [Complementos/Human error caused loss of Mars orbiter.pdf](Complementos/Human%20error%20caused%20loss%20of%20Mars%20orbiter.pdf) — caso del Mars Climate Orbiter.
- [Complementos/Sistema Internacional de Unidades INIMET.pdf](Complementos/Sistema%20Internacional%20de%20Unidades%20INIMET.pdf) — definición oficial de las 7 magnitudes básicas del SI.
