# Tema 3 — Conferencia 5: Expresión general del balance de masa y balance de masa en procesos sin reacción química

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuente principal:** [Conferencia 5 Tema 3 Plan E.pdf](Conferencia%205%20Tema%203%20Plan%20E.pdf)
> **Apoyo:** [Guia de estudio Tema 3.pdf](Guia%20de%20estudio%20Tema%203.pdf) · [PIQ1 Clase practica 5 Operaciones consecutivas y desvio Triple efecto y concentrador de jugo.pdf](PIQ1%20Clase%20practica%205%20Operaciones%20consecutivas%20y%20desvio%20Triple%20efecto%20y%20concentrador%20de%20jugo.pdf) · [PIQ1 Clase practica 6 Sistemas heterogeneos.pdf](PIQ1%20Clase%20practica%206%20Sistemas%20heterogeneos.pdf) · [PIQ1 Clase practica 7 Tecnologia del cafe instantaneo.pdf](PIQ1%20Clase%20practica%207%20Tecnologia%20del%20cafe%20instantaneo.pdf) · [../TEMA 2/Conferencia 4 - Mediciones Termometricas, Carta Sicrometrica y Procesos.md](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md) (carta sicrométrica, usada en CP6 y CP7)
>
> Este documento explica, paso a paso y sin dar nada por sabido, todo lo que exige la Conferencia 5: la expresión general del balance de masa (deducida desde la ley de conservación de la materia), sus simplificaciones para procesos estacionarios sin reacción química, los objetivos y el programa de análisis del balance de masa (base de cálculo, grados de libertad, algoritmo de solución), y la aplicación de todo ello a sistemas con desvío (bypass) y a sistemas heterogéneos. Se resuelven completos los ejercicios de las Clases Prácticas #5, #6 y #7, verificando la aritmética de forma independiente y señalando (y corrigiendo) las erratas numéricas detectadas en los materiales fuente.

---

## 0. Dónde estamos y por qué este tema

### 0.1 Ubicación dentro del programa

Como se explicó en el [Tema 1](../TEMA%201/Conferencia%201%20-%20Sistemas%20de%20Unidades%20y%20Dimensiones.md) y el [Tema 2](../TEMA%202/Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md), la asignatura organiza su contenido en 4 temas:

| Tema | C | CP | CPM | Evaluación | Total |
|---|---|---|---|---|---|
| 1. Unidades y Dimensiones | 4 | 4 | 0 | 0 | 8 |
| 2. Mezclas Vapor-Gas | 4 | 4 | 0 | 0 | 8 |
| **3. Balance de Masa** | **4** | **14** | **2** | **2 (PP)** | **22** |
| 4. Balance de Energía | 6 | 19 | 4 | 1 (TC) | 30 |

Tema 3 es, con diferencia, el más extenso de los cuatro hasta aquí: tiene 4 conferencias (numeradas 5, 6, 7 y 8 de forma consecutiva con las de los Temas 1 y 2), 14 clases prácticas, 2 clases prácticas de máquina (cálculo asistido por computadora) y una Prueba Parcial (PP) al concluirlo. En esta carpeta del repositorio están disponibles las Conferencias 5 y 6 —las dos primeras del tema— junto con las Clases Prácticas 5, 6, 7, 9, 10, 11 y 12 que las acompañan, más una carpeta `Complementos` con material de autopreparación para la prueba parcial. Esta Conferencia 5 es, dentro del propio Tema 3, la **primera**.

### 0.2 Por qué se estudia el balance de masa

Como señala la introducción de la propia conferencia, conocer la cantidad de cada material que interviene en un proceso es esencial para:

- Coordinar los efectos totales de un fenómeno físico o químico y realizar el análisis económico de una situación de ingeniería.
- Diseñar y evaluar equipos: por ejemplo, la cantidad de calor necesaria para calentar un líquido depende de la masa que debe calentarse; el rendimiento de un reactivo de interés en una reacción química depende de las cantidades de reactivos y productos.

No siempre es posible medir directamente el flujo o la composición en cada punto de una planta (no hay instrumentación en todos los puntos, o no resulta económico instalarla). Por eso se necesita un **método de cálculo** que, a partir de un mínimo de información medida, permita conocer la cantidad de cada material en las corrientes de interés. Ese método es el **balance de masa**: el establecimiento de un número suficiente de ecuaciones independientes —basadas en el **principio de conservación de la materia**— a partir de las cuales las incógnitas del sistema pueden determinarse. En esencia, un balance de masa no es más que un **conteo exacto** de los materiales que entran, salen o se acumulan en un proceso durante un tiempo de operación.

### 0.3 Relación con los demás temas

- El balance de masa es, como dice la propia conferencia, "una de las técnicas fundamentales de la ingeniería química": prácticamente todo cálculo de proceso —diseño de equipos, evaluación de plantas existentes, proyección de nuevas tecnologías— se apoya en él.
- Los cálculos de vapor condensado o evaporado del [Tema 2](../TEMA%202/) ya eran, en esencia, balances de masa elementales; ahora se formaliza el método con todo rigor.
- Las clases prácticas de este tema (CP6 y CP7 en particular) vuelven a apoyarse en la carta sicrométrica y en la ecuación de saturación adiabática del Tema 2, esta vez aplicadas a corrientes de secado dentro de procesos más complejos.
- Todo lo desarrollado aquí para procesos **sin** reacción química es la base indispensable para la Conferencia 6, que extiende el método a procesos **con** reacción química.

---

## 1. Objetivos de la conferencia

Tal como los plantea el texto:

a) Conocer las expresiones generales del balance de masa.
b) Analizar la técnica del balance de masa en procesos donde no ocurren reacciones químicas.

---

## 2. Expresión general del balance de masa

### 2.1 Deducción desde la ley de conservación de la materia

El balance de masa es una consecuencia directa de la ley de conservación de la materia. Para **un compuesto cualquiera** dentro de un sistema, la contabilidad más general posible es:

$$\left[\begin{array}{c}\text{Masa que} \\ \text{se acumula} \\ \text{de un} \\ \text{compuesto}\end{array}\right] = \left[\begin{array}{c}\text{Masa que} \\ \text{entra de} \\ \text{un} \\ \text{compuesto}\end{array}\right] - \left[\begin{array}{c}\text{Masa que} \\ \text{sale de} \\ \text{un} \\ \text{compuesto}\end{array}\right] + \left[\begin{array}{c}\text{Masa que} \\ \text{se forma} \\ \text{de un} \\ \text{compuesto}\end{array}\right] - \left[\begin{array}{c}\text{Masa que} \\ \text{reacciona} \\ \text{de un} \\ \text{compuesto}\end{array}\right]$$

Los términos **formación** y **consumo (reacciona)** corresponden, respectivamente, a la masa del compuesto que se obtiene (si es producto) y a la masa del compuesto que se consume (si es reactivo) en una reacción química. Esta es la ecuación más general que existe: se aplica exactamente al sistema (la "frontera" imaginaria, física o no) sobre el que se quiera plantear el balance, sin importar qué ocurra dentro de él.

### 2.2 Primera simplificación: régimen estacionario

En este tema solo se trabaja con sistemas en **régimen estacionario**: las propiedades del sistema no cambian con el tiempo en ningún punto. Bajo esa condición no hay acumulación, así que el primer término desaparece siempre, para cualquier proceso (con o sin reacción):

$$\left[\begin{array}{c}\text{Masa que} \\ \text{se acumula} \\ \text{de un compuesto}\end{array}\right] = 0$$

A partir de aquí, la ecuación general se particulariza según el tipo de proceso.

### 2.3 Caso (a): procesos estacionarios sin reacción química (BM s/rq)

Si además de no acumularse, el compuesto no se forma ni reacciona (no hay transformación química), la ecuación general se reduce a:

$$0 = \left[\begin{array}{c}\text{Masa que} \\ \text{entra de} \\ \text{un compuesto}\end{array}\right] - \left[\begin{array}{c}\text{Masa que} \\ \text{sale de} \\ \text{un compuesto}\end{array}\right] + 0 - 0$$

$$\boxed{\left[\begin{array}{c}\text{Masa que} \\ \text{entra de} \\ \text{un compuesto}\end{array}\right] = \left[\begin{array}{c}\text{Masa que} \\ \text{sale de} \\ \text{un compuesto}\end{array}\right]}$$

Es decir: **lo que entra es igual a lo que sale**, componente por componente. Esta expresión también es válida para el flujo **total** de las corrientes (basta con "sumar" el balance de todos los componentes). Es el resultado central de esta conferencia y el que se usa en absolutamente todos los ejercicios de las Clases Prácticas #5, #6 y #7.

### 2.4 Caso (b): procesos estacionarios con reacción química (BM c/rq) — anticipo

Aunque el desarrollo completo de este caso es el contenido de la [Conferencia 6](Conferencia%206%20-%20Balance%20de%20Masa%20con%20Reaccion%20Quimica.md), conviene ver aquí cómo se deriva, porque nace exactamente de la misma ecuación general (sección 2.1), solo que ahora hay que **separar el balance según el compuesto sea reactivo o producto**, porque para uno se forma cero y para el otro reacciona cero.

**b.1 — Para un reactivo** (no se forma, pero sí reacciona/se consume):

$$0 = \left[\text{entra}\right] - \left[\text{sale}\right] + 0 - \left[\text{reacciona}\right] \quad\Longrightarrow\quad \boxed{\left[\text{entra}\right] = \left[\text{sale}\right] + \left[\text{reacciona}\right]}$$

**b.2 — Para un producto** (no reacciona —ya se formó—, pero sí se forma):

$$0 = \left[\text{entra}\right] - \left[\text{sale}\right] + \left[\text{forma}\right] - 0 \quad\Longrightarrow\quad \boxed{\left[\text{sale}\right] = \left[\text{entra}\right] + \left[\text{forma}\right]}$$

Estas dos expresiones son la base de toda la Conferencia 6. El texto guía remite, para más detalle, al epígrafe 3.3 (pág. 212), donde se presenta una clasificación de los procesos que, si bien no es la única posible en ingeniería, ayuda a visualizar estas categorías con claridad.

---

## 3. Objetivos y programa de análisis del balance de masa

### 3.1 Para qué sirve un balance de masa: tres objetivos posibles

1. **Comprobar** una medición: si las corrientes de entrada y salida de un proceso pueden medirse y analizarse directamente, el balance de masa solo sirve para verificar que esas mediciones sean consistentes entre sí.
2. **Obtener** información no medible: si hay corrientes donde medir el flujo o la composición es imposible o antieconómico, y se cuenta con el mínimo de datos necesario en las demás corrientes, el balance de masa permite calcular los parámetros desconocidos.
3. **Diseñar o evaluar económicamente** procesos en fase de proyecto (procesos "perspectivos"): el balance de masa contribuye al dimensionamiento de equipos y a la evaluación de la economía del proceso.

### 3.2 El programa de análisis (algoritmo general de solución)

Para aplicar la técnica de forma ordenada, la conferencia propone un esquema lógico de cinco pasos:

**a) Interpretación del problema.** Se realiza con ayuda de un **diagrama de bloques**, donde se destacan los equipos, las corrientes (numeradas o con letras), los componentes que integran cada corriente y los datos disponibles. Este paso —sintetizar visualmente el problema— es el primero e indispensable en todos los ejercicios que siguen.

**b) Selección de una base de cálculo (BC) adecuada.** Tiene dos objetivos: simplificar los cálculos y resolver problemas que, sin una base de cálculo, aparentan no tener solución (más adelante se verá un ejemplo exacto de esto). La base de cálculo es un **factor de escala**: si se cambia, hay que reconvertir todas las respuestas extensivas (flujos, masas) proporcionalmente, pero las respuestas **intensivas** (composiciones, fracciones) no cambian. Es crucial recordar que **solo puede establecerse una base de cálculo por problema**: mezclar valores calculados con bases de cálculo distintas produce resultados incorrectos.

 Las bases de cálculo más convenientes suelen ser:
 - El flujo o cantidad de una de las corrientes de entrada o salida, eligiendo aquella de la que se tenga más información.
 - Un caso particular de la anterior: el flujo de un **componente inerte** o **elemento de correlación**, es decir, aquel cuya masa no cambia al atravesar el proceso. *Pregunta que deja planteada la conferencia: "En el caso de la oxidación del SO₂ por empleo de aire seco, ¿cuál sería el elemento de correlación?"* — La respuesta es el **N₂** del aire: el nitrógeno no participa en la reacción de oxidación (2 SO₂ + O₂ → 2 SO₃) y por tanto su cantidad de moles se mantiene idéntica entre la entrada y la salida del reactor, lo que lo convierte en un "hilo conductor" natural para relacionar ambas corrientes.
 - Para sistemas de flujo estacionario donde ya se conoce el valor de uno o más flujos, la base de cálculo más conveniente es directamente el **tiempo** (p. ej., 1 hora, 1 minuto, 1 día), de forma que los datos "por unidad de tiempo" del enunciado se puedan usar tal cual.

**c) Determinación de los grados de libertad del proceso (V).** Ver sección 4 (a continuación), que desarrolla este concepto con el detalle que merece por ser, junto con la base de cálculo, el paso más importante del programa de análisis.

**d) Solución numérica del problema.** Una vez comprobado que el sistema tiene solución (V = 0), se seleccionan las ecuaciones, se establece el **orden de cálculo** (qué incógnita conviene despejar primero) y se obtienen los valores numéricos.

**e) Comprobación de los resultados**, si se estima conveniente (por ejemplo, cerrando el balance por una vía alternativa, como se hace en varios de los ejercicios resueltos más adelante).

---

## 4. Grados de libertad (V)

### 4.1 Definición y convenio de signos de este curso

$$\boxed{V = \#\text{Ecuaciones Linealmente Independientes (ELI)} - \#\text{Incógnitas}}$$

**Importante:** obsérvese que esta definición es *ecuaciones menos incógnitas* (no al revés, como en otros textos). Con este convenio:

- **V = 0** → el sistema tiene exactamente tantas ecuaciones independientes como incógnitas: **tiene solución única**.
- **V < 0** → hay **más incógnitas que ecuaciones**: el sistema está subdeterminado, **no tiene solución** con la información disponible. Hace falta más información —típicamente, fijar una base de cálculo que antes no estaba fijada— para reducir el número de incógnitas hasta que V llegue a 0.
- **V > 0** → hay **más ecuaciones que incógnitas**: el sistema está sobredeterminado. En un problema correctamente planteado esto no debería ocurrir con ecuaciones genuinamente independientes; si aparece, es señal de que alguna de las "ecuaciones" en realidad es redundante (combinación lineal de las otras) o de que los datos del problema son inconsistentes entre sí y deben revisarse.

### 4.2 Cómo contar el número de ecuaciones linealmente independientes (ELI)

$$\#\text{ELI} = \#\text{Componentes (ecuaciones propias del balance, EPB)} + \#\text{ERC} + \#\text{ERE}$$

- **EPB — Ecuaciones propias del balance.** Para un sistema sin reacción química con $n$ componentes, es posible escribir $n+1$ balances (el balance total más uno por cada componente), pero solo $n$ de ellos son linealmente independientes —porque el balance total es la **suma** de los balances por componente—. Por eso: **tantas EPB como componentes tenga el sistema**.
- **ERC — Ecuaciones restrictivas de composición.** En cada corriente, la suma de las fracciones (másicas o molares) de todos sus componentes debe ser igual a 1. Por tanto: **tantas ERC como corrientes de composición indefinida (parcialmente desconocida) tenga el sistema**.
- **ERE — Ecuaciones restrictivas específicas (o especiales).** Cualquier relación adicional, propia del problema, que vincule variables de distintas corrientes o compuestos sin ser una ecuación de balance ni una restrictiva de composición — por ejemplo, "R = ½Q" o "R·x_{aR} = (1/5)·Q·x_{aQ}".

### 4.3 Ejemplo guiado: el mezclador binario de la propia conferencia

Para un mezclador con corrientes $P$, $R$ (entradas) y $Q$ (salida), cada una con dos componentes $a$ y $b$:

$$P + R = Q \quad (1)\ \text{Balance Total} \qquad P x_{aP} + R x_{aR} = Q x_{aQ}\quad (2)\ \text{Balance de } a \qquad P x_{bP} + R x_{bR} = Q x_{bQ}\quad (3)\ \text{Balance de } b$$

**¿Por qué el producto (flujo total)×(composición) da la cantidad del componente?** Porque si $x_{aP}$ es la fracción (másica o molar) del componente $a$ en la corriente $P$, y $P$ es el flujo total (másico o molar, según corresponda) de esa corriente, entonces $P\cdot x_{aP}$ es, por la propia definición de fracción, la cantidad (masa o moles) de $a$ que transporta la corriente $P$. **Regla de coherencia:** si $F$ es un flujo másico, $x_{iF}$ debe ser una fracción másica; si $F$ es un flujo molar, $x_{iF}$ debe ser una fracción molar — nunca se debe mezclar un flujo másico con una fracción molar (o viceversa) dentro del mismo producto.

De las tres ecuaciones (1)-(3), solo **dos son independientes** (tantas como componentes, $n=2$): si se suman (2) y (3) se obtiene exactamente (1), porque $x_{aP}+x_{bP}=1$, etc. Esto confirma la regla de la sección 4.2 ("tantas EPB como componentes").

Además, para cada corriente de composición no totalmente conocida se agrega su ERC: $x_{aP}+x_{bP}=1$, $x_{aR}+x_{bR}=1$, $x_{aQ}+x_{bQ}=1$. En total, para este sistema (sin ninguna ERE): $\#\text{ELI} = 2\ (\text{EPB}) + 3\ (\text{ERC}) = 5$.

**Interpretación de $x_{bQ}$:** es la fracción (másica o molar) del componente $b$ en la corriente de salida $Q$.

---

## 5. Ejemplo resuelto en la propia conferencia: destilación de benceno-tolueno

**Enunciado:** una mezcla de benceno y tolueno se alimenta a una columna de destilación de manera que el 5 % del benceno alimentado sale en la corriente de fondo (R). Calcular el flujo y la composición de la corriente R.

$$F \left\{\begin{array}{l}x_{B(F)}=0.65\\x_{T(F)}=0.35\end{array}\right. \longrightarrow \boxed{\text{Torre de Destilación}} \longrightarrow D \left\{\begin{array}{l}x_{B(D)}=0.99\\x_{T(D)}=0.01\end{array}\right. \quad ;\quad R\left\{x_{B(R)},\ x_{T(R)}\right\}$$

**Paso 1 — Grados de libertad, sin base de cálculo.** Las incógnitas son $F, D, R, x_{B(R)}, x_{T(R)}$ (5 incógnitas: nótese que $x_{B(F)}, x_{T(F)}, x_{B(D)}, x_{T(D)}$ ya son datos). Las ecuaciones: 2 EPB (benceno, tolueno) + 1 ERC (la de R) + 1 ERE ($R\,x_{BR}=0.05\,F\,x_{BF}$) = 4 ELI.

$$V = 4 - 5 = -1 \quad\Rightarrow\quad \text{no tiene solución: sobra una incógnita.}$$

**Paso 2 — Elegir base de cálculo.** Como no se conoce ningún flujo, se toma **BC = 100 kg/h de F**. Esto convierte $F$ en un dato, reduciendo las incógnitas a 4 ($D, R, x_{BR}, x_{TR}$), con lo que $V = 4-4=0$: ya tiene solución.

**Paso 3 — Plantear y resolver el sistema.**

$$100 = D + R \quad(1)\qquad 100(0.65) = 0.99\,D + R\,x_{BR} = 65 \quad(2)\qquad x_{BR}+x_{TR}=1\quad(4)\qquad R\,x_{BR}=0.05(100)(0.65)=3.25\quad(5)$$

Sustituyendo (5) en (2): $65 = 0.99\,D + 3.25 \;\Rightarrow\; D = \dfrac{65-3.25}{0.99} = 62.37\ \text{kg/h}$.

De (1): $R = 100 - 62.37 = 37.63\ \text{kg/h}$.

De (5): $x_{BR} = \dfrac{3.25}{37.63} = 0.0864$.

De (4): $x_{TR} = 1 - 0.0864 = 0.9136$.

$$\boxed{D = 62.37\ \text{kg/h}\,,\qquad R = 37.63\ \text{kg/h}\,,\qquad x_{BR}=0.0864\ (8.64\%)\,,\qquad x_{TR}=0.9136\ (91.36\%)}$$

> **Nota sobre el material fuente:** el documento original de la Conferencia 5 reporta "$x_{TR} = 0.0914$", lo cual es incompatible con $x_{BR}+x_{TR}=1$ (0.086 + 0.0914 ≠ 1) y es, con casi total seguridad, una errata de transcripción (posiblemente "$0.9136$" truncado/mal copiado). El valor correcto, verificado aquí de forma independiente a partir de las propias ecuaciones del problema, es $x_{TR}=0.9136$ (91.36 %), consistente con la ecuación restrictiva de composición.

**Pregunta que deja planteada la conferencia: "¿Cuál sería la respuesta si se tomaran 500 kg de la corriente F?"** — Como la base de cálculo es un factor de escala (sección 3.2-b), si $F=500$ kg/h (5 veces mayor que los 100 kg/h usados), **todas las variables extensivas** se multiplican por 5: $D = 5\times 62.37 = 311.85$ kg/h, $R = 5\times 37.63 = 188.15$ kg/h. Las variables **intensivas** (las composiciones $x_{BR}$, $x_{TR}$) no cambian en absoluto, porque son razones entre cantidades que escalan por igual: $x_{BR}=0.0864$ y $x_{TR}=0.9136$ siguen siendo las mismas.

---

## 6. Sistemas con desvío (bypass): teoría (Clase Práctica #5)

### 6.1 El concepto de desvío

En la industria química es frecuente controlar las variables de operación de un proceso empleando sus propias corrientes: son los llamados **procesos con desvío y recirculación**. El **desvío** (o *bypass*) es la parte de la corriente fresca alimentada al sistema que **no** entra al equipo de proceso y por tanto no sufre ningún cambio físico o químico, a diferencia de la corriente que sí es procesada.

$$\text{Corriente fresca} \longrightarrow \underbrace{\bullet}_{\text{punto de desvío}} \longrightarrow \boxed{\text{Proceso}} \longrightarrow \underbrace{\bullet}_{\text{punto de unión}} \longrightarrow \text{Corriente producto}$$
$$\text{(con el desvío conectando directamente el punto de desvío con el punto de unión, "por arriba")}$$

Sobre un esquema como este pueden plantearse balances de masa en **cuatro sistemas distintos**, cada uno útil según qué se quiera calcular:

1. **En el punto de desvío** — solo tiene sentido para las cantidades **totales** de flujo, ya que en un punto de desvío las composiciones de las corrientes que se separan son idénticas (es una división mecánica de un mismo flujo, no una separación por composición).
2. **Alrededor del proceso** (equipo) únicamente.
3. **En el punto de unión.**
4. **Para el sistema completo**, tomando como frontera las corrientes fresca y producto; en este caso, la corriente de desvío queda **como una corriente interna** al sistema (no cruza la frontera) y por tanto no aparece explícitamente en su balance.

Para el caso de **recirculación** (reciclo), el análisis es exactamente el mismo, con la salvedad de que los puntos de desvío y de unión se invierten en su papel topológico: la recirculación sale de después del proceso y se reincorpora antes de él.

---

## 7. Ejercicios resueltos de la Clase Práctica #5

### 7.1 Ejercicio #1 — Evaporador de tres efectos (operaciones consecutivas)

**Enunciado:** una solución acuosa de un sólido al 50 % másico se concentra en un evaporador de tres efectos en serie. El flujo de alimentación es 50 000 kg/h y la producción final, 35 000 kg/h. En cada efecto se evapora **igual** cantidad de agua. Determinar las corrientes que salen del 2.º y 3.er efecto.

$$50000\ \tfrac{kg}{h}\Big\{x_{s(F)}=0.5 \atop x_{H_2O(F)}=0.5\Big\} \to \boxed{1^{er}} \xrightarrow{A} \boxed{2^{do}} \xrightarrow{B} \boxed{3^{er}} \to 35000\ \tfrac{kg}{h}\ (C)$$

con $m_1, m_2, m_3$ el agua evaporada en cada efecto (todas iguales entre sí, por dato del problema).

**Análisis de grados de libertad por sistema (BC = 1 h):**

| Sistema | #EPB | #ERC | #ERE | Total ELI | #Incógnitas | V |
|---|---|---|---|---|---|---|
| Solo el 1.er efecto | 2 | 1 (de A) | 0 | 3 | 4 ($m_1$, $A$, $x_{s(A)}$, $x_{H_2O(A)}$) | −1 |
| Solo el 2.do efecto | 2 | 2 (de A y B) | 0 | 4 | 7 | −3 |
| Solo el 3.er efecto | 2 | 2 (de B y C) | 0 | 4 | 6 | −2 |
| **El proceso completo** | 2 | 1 (de C) | 2 ($m_1=m_2=m_3$) | **5** | **5** ($m_1,m_2,m_3,x_{s(C)},x_{H_2O(C)}$) | **0** |

**Ninguno de los sistemas parciales tiene solución por sí solo**; solo el **proceso completo** tiene $V=0$. Esto ilustra un patrón que se repetirá en toda la conferencia: cuando un subsistema no es resoluble, hay que ampliar la frontera del balance (aquí, al proceso completo) hasta encontrar una que sí lo sea, y resolver los subsistemas restantes **después**, usando los resultados ya obtenidos como nuevos datos conocidos.

**Paso 1 — Balance en el proceso completo.**

Global: $F = C + m_1+m_2+m_3 \;\Rightarrow\; 50000 = 35000 + (m_1+m_2+m_3) \;\Rightarrow\; m_1+m_2+m_3 = 15000\ \text{kg}$

Sólido: $F\,x_{s(F)} = C\,x_{s(C)} \;\Rightarrow\; x_{s(C)} = \dfrac{50000(0.5)}{35000} = 0.714$

Restrictiva de C: $x_{H_2O(C)} = 1-0.714 = 0.286$

Restrictiva especial ($m_1=m_2=m_3$): $3m_1 = 15000 \;\Rightarrow\; \boxed{m_1=m_2=m_3=5000\ \text{kg}}$

**Paso 2 — Balance en el 3.er efecto** (ahora resoluble: $m_3$ y la composición de $C$ ya son conocidos).

Global: $B = C + m_3 = 35000+5000 = 40000\ \text{kg}$

Sólido: $B\,x_{s(B)} = C\,x_{s(C)} \;\Rightarrow\; x_{s(B)} = \dfrac{35000(0.714)}{40000} = 0.625 \;\Rightarrow\; x_{H_2O(B)}=0.375$

$$\boxed{B = 40000\ \text{kg/h}\,,\quad x_{s(B)}=0.625\,,\quad x_{H_2O(B)}=0.375}$$

**Trabajo independiente propuesto en la clase práctica: hallar $A$ tomando como sistema el 1.er efecto, y verificar con el 2.do efecto.**

Sistema: 1.er efecto ($F\to A + m_1$), con $F=50000$ kg, $m_1=5000$ kg (ya conocido tras resolver el proceso completo):

Global: $A = F - m_1 = 50000-5000 = 45000\ \text{kg}$

Sólido: $F\,x_{s(F)}=A\,x_{s(A)} \;\Rightarrow\; x_{s(A)} = \dfrac{50000(0.5)}{45000}=0.5556 \;\Rightarrow\; x_{H_2O(A)}=0.4444$

**Verificación con el 2.do efecto** ($A \to B + m_2$, con $m_2=5000$ kg ya conocido):

Global: $B = A-m_2 = 45000-5000=40000\ \text{kg}$ ✓ (coincide exactamente con el valor de $B$ obtenido arriba desde el 3.er efecto)

Sólido: $x_{s(B)} = \dfrac{A\,x_{s(A)}}{B} = \dfrac{45000(0.5556)}{40000} = 0.625$ ✓ (coincide exactamente)

$$\boxed{A = 45000\ \text{kg/h}\,,\quad x_{s(A)}=0.5556\ (55.56\%)\,,\quad x_{H_2O(A)}=0.4444\ (44.44\%)}$$

La coincidencia perfecta entre los dos caminos de cálculo (desde el 3.er efecto hacia atrás, y desde el 1.er efecto hacia adelante) confirma que la solución es correcta: es exactamente el tipo de comprobación cruzada que recomienda el paso (e) del programa de análisis (sección 3.2).

### 7.2 Ejercicio #2 — Concentrador de jugo de naranja (con corriente de ajuste)

**Enunciado:** el jugo de naranja fresco se concentra en un evaporador especial antes de embarcarse (para reducir costos de traslado) y luego se reconstituye con una corriente de ajuste de jugo fresco (que no pasa por el evaporador) para lograr mejor sabor y aroma. Si se usa el 10 % de la alimentación de jugo fresco como corriente de ajuste, calcular la composición del producto concentrado y la razón de evaporación (flujo de agua evaporada / peso de jugo fresco) cuando se alimentan 10 000 kg/h de jugo fresco.

$$(1)\ \text{Jugo fresco}\ x_{S(1)}=12\% \xrightarrow{\ } \underbrace{\bullet}_{\text{desvío}} \xrightarrow{(2)} \boxed{\text{Evaporador}} \xrightarrow[x_{S(5)}=80\%]{(5)} \underbrace{\bullet}_{\text{mezclador}} \xrightarrow{(6)\ \text{Concentrado}}$$

con la corriente (3) —el 10 % de (1)— yendo directamente del punto de desvío al mezclador, y (4) el agua evaporada.

**Este es exactamente el esquema de desvío de la sección 6.1**, con el mezclador jugando el papel de "punto de unión". BC = 1 h.

**Paso 1 — Balance en el punto de desvío.**

$$F_1 = F_2+F_3\,,\qquad F_1=10000\ \text{kg}\,,\qquad F_3=0.1\,F_1=1000\ \text{kg} \;\Rightarrow\; F_2 = 10000-1000=9000\ \text{kg}$$

**Paso 2 — Balance en el evaporador** ($x_{S(2)}=x_{S(1)}=0.12$, porque el desvío no altera la composición de la corriente restante):

$$F_2\,x_{S(2)} = F_5\,x_{S(5)} \;\Rightarrow\; F_5 = \dfrac{0.12(9000)}{0.8} = 1350\ \text{kg}\,,\qquad F_4 = F_2-F_5 = 9000-1350=7650\ \text{kg}$$

**Paso 3 — Balance en el mezclador (punto de unión).**

$$F_6 = F_5+F_3 = 1350+1000 = 2350\ \text{kg}$$

$$x_{S(6)} = \dfrac{x_{S(5)}F_5 + x_{S(3)}F_3}{F_6} = \dfrac{0.8(1350)+0.12(1000)}{2350} = \dfrac{1080+120}{2350}=\dfrac{1200}{2350}=0.51$$

**Paso 4 — Razón de evaporación.**

$$\text{Razón de evaporación} = \dfrac{F_4}{F_1} = \dfrac{7650}{10000} = 0.765$$

$$\boxed{x_{S(6)} = 51\%\ \text{sólidos}\,,\qquad x_{H_2O(6)}=49\%\,,\qquad \text{Razón de evaporación} = 0.765}$$

**Comprobación global** (frontera de todo el sistema, con la corriente de desvío quedando interna): $F_1 = F_4+F_6 \;\Rightarrow\; 10000 \stackrel{?}{=} 7650+2350 = 10000$ ✓.

---

## 8. Sistemas heterogéneos: teoría y ejercicio de la Clase Práctica #6

### 8.1 Por qué son distintos de las mezclas vapor-gas

Los sistemas heterogéneos aparecen con frecuencia en los procesos de **separación mecánica** de la industria química, como la **filtración** y la **sedimentación**. La suspensión (alimentación al equipo de separación) y la torta o pulpa (sólido húmedo que resulta de la separación) son mezclas de un **sólido seco** y un **líquido**, para las cuales se define un conjunto de formas de expresar la composición **formalmente análogo** al de las mezclas vapor-gas del [Tema 2](../TEMA%202/Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md), pero adaptado a un sistema **sólido-líquido**:

$$\text{Suspensión} \longrightarrow \boxed{\text{Equipo de separación}} \longrightarrow \begin{cases}\text{Filtrado o líquido claro}\\ \text{Torta o pulpa}\end{cases}$$

### 8.2 Las formas de expresar la composición (subíndices $s$ = suspensión, $t$ = torta/pulpa)

| Magnitud | Definición | Fórmula |
|---|---|---|
| Fracción másica del sólido en la mezcla | masa de sólido seco / masa de mezcla | $x,\ x_t$ |
| Fracción másica del sólido en base libre de sólido | masa de sólido seco / masa de **líquido** | $X,\ X_t$ |
| Concentración de sólidos en la mezcla | masa de sólido seco / volumen de mezcla | $C_s',\ C_t'$ |
| Concentración de sólidos en base libre | masa de sólido seco / volumen de **líquido** | $C_s$ |
| Humedad de la mezcla | masa de líquido / masa de mezcla | $H$ |

La analogía con el Tema 2 es exacta: $x$ (fracción másica en la mezcla total) juega el papel de la fracción másica del vapor $y$; $X$ (base libre de sólido) juega el papel de la saturación $Y$; y la relación entre ambas es idéntica en forma:

$$x = \dfrac{X}{1+X}\ \text{(suspensión)}\,,\qquad x_t=\dfrac{X_t}{1+X_t}\ \text{(torta)}$$

**Ecuaciones que se cumplen:**

**a) Restrictiva de composición** (análoga a $y+Y_{gas}=1$ del Tema 2, pero aquí entre sólido y líquido):

$$x+H=1\,,\qquad x_t+H=1$$

**b) Relación entre concentración en la mezcla y fracción másica**, vía la densidad de la mezcla $d_s$ (o $d_t$):

$$\dfrac{C_s'}{d_s}=x\,,\qquad \dfrac{C_t'}{d_t}=x_t$$

**c) Relación entre concentración en base libre y fracción en base libre**, vía la densidad del líquido $d$:

$$C_s\cdot\dfrac{1}{d}=X$$

**d) Densidad de la mezcla por regla aditiva de volúmenes específicos**, con $d_p$ la densidad del sólido seco:

$$\dfrac{1}{d_s\ \text{ó}\ d_t} = \dfrac{x}{d_p}+\dfrac{1-x}{d}$$

Esta última ecuación expresa que el **volumen** de la mezcla es la suma del volumen que ocupa el sólido más el volumen que ocupa el líquido (regla aditiva de volúmenes, válida cuando no hay contracción o expansión de volumen al mezclar, lo cual es una excelente aproximación para suspensiones sólido-líquido diluidas).

### 8.3 Ejercicio resuelto — Filtración y secado de hidróxido de níquel hidratado

**Enunciado (resumen de datos):** se filtra una suspensión de Ni(OH)₂ con $C_s = 131.8$ kg sólido/m³ de líquido, $d_p=4360$ kg/m³ (sólido), $d=1100$ kg/m³ (líquido). La torta sale del filtro con humedad $H_{t(4)}=75\%$ y, tras secarse, con $H_{t(5)}=60\%$. Capacidad: 2.8 t sólido seco/día. Agua de lavado: 0.8 L/kg sólido seco. Aire del secador: entra a 25 °C, $\%Y_R=30\%$; sale a 35 °C, $T_r=20$ °C. BC = 1 día.

$$\text{(1) Suspensión} \left(C_s=131.8\ \tfrac{kg}{m^3}\right) \to \boxed{\text{FILTRO}} \to \begin{cases}\text{(2) líquido filtrado}\\ \text{(4) Torta } H_t=75\%\end{cases} \to \boxed{\text{Secador no adiabático}} \to \begin{cases}\text{(7) aire húmedo}\\\text{(5) Torta } H_t=60\%,\ 2.8\ \text{t/d}\end{cases}$$

con (3) el agua de lavado (0.8 L/kg sólido) entrando al filtro y (6) el aire húmedo entrando al secador.

**a) Fracción másica de sólidos en la suspensión ($x_1$) y concentración en g sólido/L suspensión ($C_{s1}'$).**

Primero se pasa la concentración en base libre a fracción en base libre (ecuación (c) de la sección 8.2):

$$X_1 = C_{s1}\cdot\dfrac{1}{d} = \dfrac{131.8}{1100} = 0.1198\ \dfrac{\text{kg sólido}}{\text{kg líquido}}$$

Luego a fracción másica en la mezcla:

$$x_1 = \dfrac{X_1}{1+X_1} = \dfrac{0.1198}{1.1198} = 0.107\ \dfrac{\text{kg sólido}}{\text{kg susp.}}\ (10.7\%)$$

Para $C_{s1}'$ hace falta la densidad de la suspensión, por la regla aditiva (ecuación (d)):

$$\dfrac{1}{d_s} = \dfrac{x_1}{d_p}+\dfrac{1-x_1}{d} = \dfrac{0.107}{4360}+\dfrac{0.893}{1100} = 0.0000245+0.0008118=0.0008363 \;\Rightarrow\; d_s = 1196\ \dfrac{\text{kg susp.}}{\text{m}^3}$$

$$\boxed{C_{s1}' = d_s\,x_1 = 1196(0.107) = 127.97\ \dfrac{\text{kg sólido}}{\text{m}^3\ \text{susp.}} \approx 128\ \dfrac{\text{g}}{\text{L}}}$$

**b) Flujo volumétrico de la suspensión procesada (m³/día).**

Balance de sólidos (el sólido no cambia de fase en el filtro ni en el secador, así que su masa se conserva desde (1) hasta (5)): $\text{sólidos}_{(1)} = \text{sólidos}_{(4)} = \text{sólidos}_{(5)} = 2800$ kg/día.

$$F_1 = \dfrac{\text{sólidos}_{(1)}}{x_1} = \dfrac{2800}{0.107} = 26168\ \dfrac{\text{kg susp.}}{\text{día}} \;\Rightarrow\; \boxed{V_1 = \dfrac{F_1}{d_s} = \dfrac{26168}{1196} = 21.9\ \text{m}^3/\text{día}}$$

**c) Flujo de líquido filtrado ($F_2$, en kg).**

Balance total en el filtro: $F_1+F_3 = F_2+F_4$.

$$F_3 = 0.8\ \dfrac{\text{L}}{\text{kg sólido}}\times 2800\ \text{kg sólido}\times 1\ \dfrac{\text{kg}}{\text{L}} = 2240\ \text{kg (agua de lavado)}$$

$$F_4 = \dfrac{\text{sólidos}_{(4)}}{1-H_4} = \dfrac{2800}{1-0.75}=11200\ \text{kg (torta húmeda que sale del filtro)}$$

$$\boxed{F_2 = F_1+F_3-F_4 = 26168+2240-11200 = 17208\ \text{kg/día}}$$

**d) Flujo volumétrico de aire húmedo necesario en el secador.**

Agua evaporada en el secador: $F_4-F_5$, con $F_5=\dfrac{2800}{1-0.6}=7000$ kg (torta seca a la salida)... 

*Nota de verificación:* el material fuente calcula $\text{agua evaporada} = F_4-\dfrac{2800}{1-0.6} = 11200-7000=4200$ kg, cifra que se usa a continuación; se confirma aquí que es correcta.

Con las humedades leídas en la [carta sicrométrica](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md) para el aire de entrada (25 °C, $\%Y_R=30\%$) y salida (35 °C, $T_r=20$ °C): $Y_6=0.006$ y $Y_7=0.015$ kg agua/kg aire seco.

$$mas = \dfrac{\text{agua evaporada}}{Y_7-Y_6} = \dfrac{4200}{0.015-0.006} = \dfrac{4200}{0.009} = 466667\ \text{kg aire seco/día}$$

Con el volumen húmedo del aire de entrada, $V_{H(6)}=0.85\ \text{m}^3/\text{kg a.s.}$ (leído también de la carta a 25 °C, $\%Y_R=30\%$):

$$\boxed{V_6 = mas\times V_{H(6)} = 466667\times 0.85 = 396667\ \text{m}^3/\text{día}}$$

**Reflexión de cierre (la que pide la propia clase práctica):** la analogía entre la composición de sistemas heterogéneos ($x$, $X$, $H$) y la de mezclas vapor-gas ($y_m$, $Y_m$, humedad) no es casual — en ambos casos se tiene una fase "portadora" (el líquido aquí, el gas allá) y una fase "transportada" (el sólido aquí, el vapor allá), y las mismas relaciones algebraicas ($x=X/(1+X)$, restrictivas de composición, etc.) se aplican en ambos contextos porque la estructura matemática del problema —dos fases, una base "total" y una base "libre de la fase transportada"— es idéntica. La diferencia clave es conceptual: en las mezclas vapor-gas, la fase transportada (el vapor) puede *evaporarse o condensarse* dependiendo de $P_s(T)$; en los sistemas heterogéneos, el sólido no cambia de fase — solo se separa mecánicamente del líquido.

---

## 9. Ejercicios resueltos de la Clase Práctica #7 — Tecnología del café instantáneo

### 9.1 El proceso base

Este ejercicio es el más complejo de balance sin reacción química del tema: integra un percolador, un mezclador, un secador spray, un separador ciclónico, una prensa y un secador adicional, con **13 corrientes**. Su objetivo pedagógico explícito es "aplicar las técnicas del balance de masa a un proceso estacionario complejo" y "analizar los efectos de determinadas variables sobre otras variables del proceso".

**Enunciado:** el café molido y tostado (sin agua; solo materiales solubles e insolubles) se carga con agua caliente (1.2 kg agua/kg café) a un percolador, de donde se extraen los solubles. El extracto se seca por aspersión (secador spray) para dar el producto; los residuos sólidos se decantan parcialmente (separador ciclónico + prensa) antes de desecharse.

$$\text{Café (1)}\ 32.7\%\text{Insol.},\ 67.3\%\text{Sol.} \to \boxed{\text{PERCOLADOR}} \begin{cases}\text{(3) Solubles+Agua} \to \boxed{\text{Mezclador}} \to \text{(6) Extracto } 35\%\text{Sol.},65\%\text{Agua} \to \boxed{\text{Secador Spray}} \to \begin{cases}\text{(7) Agua}\\\text{(8) Café instantáneo}\end{cases}\\ \text{(4)} \to \boxed{\text{Separador Ciclónico}} \to \begin{cases}\text{(5) Solubles+Agua (recircula al mezclador)}\\ \text{(9) Lechada } 20\%\text{Insol.} \to \boxed{\text{Prensa}} \to \begin{cases}\text{(11) Solución de desperdicio}\\\text{(10) Lechada } 50\%\text{Insol.} \to \boxed{\text{Secador}} \to \begin{cases}\text{(12) Agua}\\\text{(13) Residuo } 69\%\text{Insol.}\end{cases}\end{cases}\end{cases}$$

con (2) el agua caliente de carga al percolador.

### 9.2 Parte (a): recuperación de solubles

**Selección del sistema.** El material fuente analiza tres posibles fronteras y sus grados de libertad; solo el sistema **percolador-mezclador-separador** tiene $V=0$ (10 incógnitas, 3 EPB + 2 ERC + 1 ERE = 6 ELI para el "sistema 1" da V=−4; el "sistema 2" da V=−6; el sistema percolador-mezclador-separador, con solo 5 incógnitas y 5 ELI, da $V=0$). BC = 1 kg de café.

**Balance de insolubles** (el insoluble no se pierde entre el café de entrada (1) y la lechada de salida (9), porque ni el mezclador ni el separador alteran su masa total, solo la redistribuyen entre corrientes; el extracto (6) no contiene insolubles):

$$F_1\,x_{i1} = F_9\,x_{i9} \;\Rightarrow\; 1(0.327) = F_9(0.2) \;\Rightarrow\; F_9 = \dfrac{0.327}{0.2}=1.635\ \text{kg}$$

**Balance de solubles:**

$$F_1\,x_{s1} = F_6\,x_{s6}+F_9\,x_{s9} \;\Rightarrow\; 1(0.673) = 0.35\,F_6 + 1.635\,x_{s9}$$

**Balance global** (con $F_2=1.2\,F_1=1.2$ kg, dato del enunciado):

$$F_1+F_2 = F_6+F_9 \;\Rightarrow\; F_6 = 1+1.2-1.635 = 0.565\ \text{kg}$$

Con $F_6$ conocido, la ecuación de solubles queda con una sola incógnita, $x_{s9}$; pero como el problema pide directamente la relación de solubles entre (6) y (9), basta con:

$$\text{Solubles}_{(6)} = F_6\,x_{s6} = 0.565(0.35) = 0.198\ \text{kg}\,,\qquad \text{Solubles}_{(9)} = 1(0.673)-0.198 = 0.475\ \text{kg}$$

*(El material fuente reporta $x_{s9}=0.291$, de donde Solubles$_{(9)}=1.635(0.291)=0.476$ kg — coincide, dentro del redondeo, con el valor 0.475 kg obtenido aquí directamente del balance global de solubles; se usa 0.476 kg, el valor con la composición explícita, para el resto del cálculo.)*

$$\text{Proporción}\ \dfrac{\text{recuperados}}{\text{perdidos}} = \dfrac{0.198}{0.476} = 0.416$$

$$\boxed{\%\text{Recuperación} = \dfrac{\text{Solubles}_{(6)}}{\text{Solubles}_{(1)}}\times 100 = \dfrac{0.198}{0.673}\times 100 = 29.4\%}$$

**Conclusión del propio ejercicio: la recuperación de café soluble es pobre** (menos de un tercio del café soluble termina en el producto; el resto se pierde en el residuo húmedo que se desecha).

### 9.3 Parte (b): aire de secado y agua a eliminar

**Selección del sistema para la cadena separador→prensa→secador.** De los tres sistemas analizados (secador solo, prensa-secador, prensa sola), solo la **prensa** tiene $V=0$ inicialmente resoluble con los datos disponibles en ese punto de la cadena de cálculo.

**Balance en la prensa** ($F_9=1.635$ kg, ya conocido):

Insolubles: $F_9\,x_{i9}=F_{10}\,x_{i10} \;\Rightarrow\; 1.635(0.2)=F_{10}(0.5) \;\Rightarrow\; F_{10}=0.654\ \text{kg}$

Total: $F_{11}=F_9-F_{10}=1.635-0.654=0.981\ \text{kg}$

**Balance en el secador** ($F_{10}=0.654$ kg, ya conocido):

Insolubles: $F_{10}\,x_{i10}=F_{13}\,x_{i13} \;\Rightarrow\; 0.654(0.5)=F_{13}(0.69) \;\Rightarrow\; F_{13}=0.474\ \text{kg}$

Total: $F_{12}=F_{10}-F_{13}=0.654-0.474=0.18\ \text{kg}\quad\text{(agua a evaporar en el secador)}$

**Cálculo del aire seco y su volumen** (usando la [carta sicrométrica](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md), con el secador operando en régimen **adiabático**): a 25 °C, $\%Y_R=40\%$, $Y_6=0.008$ kg agua/kg a.s.; a $\%Y_R=95\%$ tras la saturación adiabática, $Y_7=0.0115$ kg agua/kg a.s.

$$mas = \dfrac{\text{agua evaporada}}{\Delta Y} = \dfrac{0.18}{0.0115-0.008}=\dfrac{0.18}{0.0035}=51.43\ \text{kg a.s.}$$

$$V = mas\times V_{H(6)} = 51.43\times 0.856 = 44.02\ \text{m}^3 \quad (V_{H(6)}=0.856\ \text{m}^3/\text{kg a.s.}\ \text{a } 25\text{°C},\ \%Y_R=40\%,\ \text{de la carta})$$

**El agua a eliminar en el extracto** (la que sale como vapor del secador spray, corriente (7)) se obtiene del contenido de agua del extracto (6):

$$\text{H}_2\text{O}_{(7)} = \text{H}_2\text{O}_{(6)} = F_6\,x_{H_2O(6)} = 0.565(1-0.35) = 0.367\ \text{kg}$$

$$\boxed{mas = 51.43\ \text{kg a.s.}\,,\qquad V_6 = 44.02\ \text{m}^3\,,\qquad \text{H}_2\text{O a eliminar} = 0.367\ \text{kg}}$$

### 9.4 Análisis de alternativas: mejorando la recuperación mediante recirculación

El propio material docente plantea, como cierre de la clase práctica, una **variante con recirculación**: se recircula la solución de desperdicio de la prensa de vuelta al percolador (para no perder esos solubles), pero para reducir la liberación de sabor amargo durante el prensado se opera con una lechada de mayor contenido de agua (40 % insolubles en la torta, en vez del 50 % anterior), y se ajusta el secador para descargar sólidos con 62.5 % de insolubles. El material fuente deja esta variante como ejercicio ("orientar la solución de esta alternativa y verificar cómo aumenta el % de recuperación"), sin resolverla numéricamente. **A continuación se resuelve completa**, de forma independiente.

$$\text{Café (1)}\ 32.7\%\text{Insol.} \to \boxed{\substack{\text{PERCOLADOR-}\\\text{SEPARADOR-}\\\text{MEZCLADOR}}} \to \begin{cases}\text{(3) Extracto } 35\%\text{Sol.},65\%\text{Agua}\\ \text{(4) Lechada } 20\%\text{Insol.},28\%\text{Sol.},52\%\text{Agua} \to \boxed{\text{PRENSA}} \to \begin{cases}\text{(5) Solución de recirculación (0\% Insol.)}\to\ \text{regresa al PSM}\\ \text{(6) } 40\%\text{Insol.} \to \boxed{\text{SECADOR}} \to \begin{cases}\text{(7) Agua}\\ \text{(8) } 62.5\%\text{Insol.}\end{cases}\end{cases}\end{cases}$$

con (2) el agua caliente entrando al bloque combinado percolador-separador-mezclador (PSM), junto con la recirculación (5).

**Hipótesis de trabajo (dada en el propio enunciado):** "Considere iguales la proporción entre solubles y agua en las dos salidas de la prensa." Esto significa que la prensa separa mecánicamente el sólido insoluble del líquido madre, **sin alterar la composición relativa de ese líquido**: tanto la solución de recirculación (5) —que es prácticamente líquido puro, 0 % insolubles— como el líquido que queda retenido dentro de la torta húmeda (6) tienen la misma razón solubles:agua. Esa razón es, por conservarse desde la lechada (4) que entra a la prensa, la que trae (4) en su fracción líquida: $\dfrac{28}{28+52}=\dfrac{28}{80}=0.35$ (35 % solubles / 65 % agua en la fase líquida) — exactamente la misma composición que el extracto (3), lo cual tiene sentido físico: es el mismo "licor madre" del percolador en toda la cadena.

**Composición de la torta húmeda (6):** 40 % insolubles + 60 % de líquido con razón 0.35/0.65:

$$x_{s(6)} = 0.60\times 0.35 = 0.21\ (21\%)\,,\qquad x_{H_2O(6)}=0.60\times 0.65=0.39\ (39\%)$$

(coincide exactamente con la etiqueta "(6) 40 % Insolubles" del diagrama original, confirmando la interpretación).

**Composición del residuo final (8):** el secador solo retira agua (vapor puro por (7)); insolubles y solubles se conservan entre (6) y (8), así que su **razón** insolubles:solubles no cambia:

$$\dfrac{x_{i(6)}}{x_{s(6)}} = \dfrac{40}{21} = 1.9048 = \dfrac{x_{i(8)}}{x_{s(8)}} = \dfrac{62.5}{x_{s(8)}} \;\Rightarrow\; x_{s(8)} = \dfrac{62.5}{1.9048}=32.81\%\,,\qquad x_{H_2O(8)}=100-62.5-32.81=4.69\%$$

**Balance global del proceso completo** (frontera: café (1) + agua caliente (2) → extracto (3) + agua evaporada (7) + residuo (8); la recirculación (5) queda **interna**, exactamente como en el esquema general de desvío/reciclo de la sección 6.1). BC = 1 kg café.

**Insolubles** (solo entran por (1) y solo salen por (8), ya que (3) y (7) no tienen insolubles):

$$F_1\,x_{i1} = F_8\,x_{i8} \;\Rightarrow\; 1(0.327) = F_8(0.625) \;\Rightarrow\; F_8 = \dfrac{0.327}{0.625}=0.5232\ \text{kg}$$

**Solubles** (entran solo por (1); salen por (3) y por (8)):

$$F_1\,x_{s1} = F_3\,x_{s3}+F_8\,x_{s8} \;\Rightarrow\; 0.673 = 0.35\,F_3 + 0.5232(0.3281)$$

$$0.673 = 0.35\,F_3 + 0.1717 \;\Rightarrow\; F_3 = \dfrac{0.673-0.1717}{0.35} = \dfrac{0.5013}{0.35}=1.4324\ \text{kg}$$

**Porcentaje de recuperación de solubles:**

$$\boxed{\%\text{Recuperación} = \dfrac{F_3\,x_{s3}}{F_1\,x_{s1}}\times 100 = \dfrac{1.4324(0.35)}{0.673}\times 100 = \dfrac{0.5013}{0.673}\times 100 = 74.5\%}$$

**Verificación cualitativa:** la recuperación sube de **29.4 %** (proceso sin recirculación, sección 9.2) a **74.5 %** (proceso con recirculación) — una mejora de más del doble, exactamente la tendencia que anticipa el enunciado ("verificar cómo aumenta el % de recuperación"). La razón física es directa: al devolver la solución de desperdicio (5) —que en el proceso original se perdía por completo junto con el residuo— de vuelta al percolador, esos solubles tienen una segunda oportunidad de terminar en el extracto (3) en vez de perderse; solo se pierde definitivamente la fracción de solubles que queda atrapada en la humedad residual del sólido descartado por (8), que ahora es mucho menor porque el residuo (8) es un sólido bastante más seco en términos relativos de solubles perdidos por unidad de café procesado.

> **Nota de alcance:** no se dispone, en los archivos de esta carpeta, del flujo de agua caliente (2) ni del aire del secador para esta variante (a diferencia del proceso original, aquí no se especifican las condiciones de temperatura/humedad del aire de secado), así que el sistema queda determinado únicamente hasta donde permite el balance de materiales secos: $F_2$ y el agua evaporada $F_7$ quedan relacionados por una sola ecuación (el balance total/de agua), pero no pueden separarse individualmente sin un dato adicional (p. ej., la humedad del aire de secado, como en el proceso original). Esto es coherente con el propio objetivo del ejercicio, que pide verificar el efecto sobre la **recuperación**, no resolver el secador completo.

---

## 10. Preguntas de repaso (respondidas)

La conferencia y las clases prácticas intercalan preguntas a lo largo del desarrollo. Se recopilan y responden aquí:

**¿Cómo se interpreta $x_{bQ}$?**
Es la fracción (másica o molar, según se use para flujos másicos o molares) del componente $b$ en la corriente de salida $Q$ del mezclador.

**¿Se cumple lo planteado para el número de ecuaciones de balance ($n+1$ posibles, $n$ independientes)?**
Sí: con $n=2$ componentes hay 3 ecuaciones de balance posibles (total + 2 por componente), pero solo 2 son independientes, porque la suma de los balances por componente reproduce exactamente el balance total.

**En el caso de la oxidación del SO₂ con aire seco, ¿cuál sería el elemento de correlación?**
El **N₂** del aire: no participa en la reacción de oxidación, así que su cantidad (en moles) es idéntica en la entrada y en la salida del reactor, lo que permite usarlo como "hilo conductor" para relacionar ambas corrientes sin necesidad de conocer directamente el flujo total de gas.

**¿A qué conclusión se llega si $V>0$? ¿Y si $V<0$?**
Con el convenio $V=\#\text{ELI}-\#\text{Incógnitas}$ de este curso: $V<0$ significa que sobran incógnitas respecto a las ecuaciones disponibles — el sistema **no tiene solución** con los datos actuales y hace falta más información (típicamente, fijar una base de cálculo). $V>0$ significa que sobran ecuaciones — en un problema bien planteado, con ecuaciones genuinamente independientes, esto no debería ocurrir; si aparece, indica que alguna "ecuación" es en realidad redundante o que los datos son inconsistentes y deben revisarse.

**¿Cuál sería la respuesta del ejercicio de destilación benceno-tolueno si se tomaran 500 kg de la corriente F?**
Como la base de cálculo es un factor de escala, todas las variables extensivas se multiplican por el mismo factor (5, en este caso): $D=311.85$ kg/h, $R=188.15$ kg/h. Las composiciones ($x_{BR}=0.0864$, $x_{TR}=0.9136$) no cambian, porque son variables intensivas.

---

## 11. Para seguir estudiando

- **Texto, páginas 209–237** (no incluido entre los archivos de esta carpeta): contiene la clasificación de procesos del epígrafe 3.3 (pág. 212) y los ejemplos resueltos 3.1 (pág. 224), 3.2 (pág. 226) y 3.6 (pág. 236), así como los ejemplos 3.9 (pág. 251) y 3.10 (pág. 254), señalados por la propia conferencia como los de mayor énfasis. Los epígrafes recomendados para estudio son el 3.0, 3.1, 3.2, 3.4 y 3.5 (estudio detallado) y el 3.3 (solo lectura).
- **Epígrafes 3.11 (pág. 315), 3.12 (pág. 320) y 3.13 (pág. 324)**, con el ejemplo resuelto 3.18 (pág. 316): cubren en detalle los sistemas con desvío y recirculación que sustentan la sección 6 de este documento. Los ejercicios propuestos #2 (pág. 328) y #12 (pág. 332) del texto se dejan como trabajo independiente adicional.
- **[PIQ1 Clase practica 8 (en maquina).zip](PIQ1%20Clase%20practica%208%20(en%20maquina).zip):** es la clase práctica de máquina (CPM) que sigue a la #7 en la secuencia del tema; a diferencia de las demás, se resuelve con software (hoja de cálculo) en vez de a mano, por lo que no se desarrolla en este documento de teoría.
- **Carpeta [Complementos](Complementos/)** de esta carpeta: contiene el documento [Autopreparacion Balance de masa srq.pdf](Complementos/Autopreparacion%20Balance%20de%20masa%20srq.pdf) — seis problemas adicionales de auto-preparación para la Prueba Parcial, exclusivamente de balance de masa **sin** reacción química (destilación, secado, evaporación multietapa, sistemas heterogéneos), con las respuestas numéricas incluidas para autoevaluación. La propia Guía de estudio del tema recomienda resolverlos íntegramente antes de la prueba parcial. El problema #6 (destilación multicomponente con especificaciones de recuperación) está señalado en el propio documento como el de mayor dificultad.
- El estudio del balance de masa **sin** reacción química concluye aquí. Por ser la reacción química un fenómeno presente en casi todas las tecnologías de la industria química, la [Conferencia 6](Conferencia%206%20-%20Balance%20de%20Masa%20con%20Reaccion%20Quimica.md) extiende exactamente el mismo programa de análisis (interpretación, base de cálculo, grados de libertad, solución numérica) al caso en que sí ocurren reacciones.

---

## Referencias / fuentes usadas en este documento

- [Conferencia 5 Tema 3 Plan E.pdf](Conferencia%205%20Tema%203%20Plan%20E.pdf) — fuente principal del contenido teórico (secciones 2–6).
- [Guia de estudio Tema 3.pdf](Guia%20de%20estudio%20Tema%203.pdf) — conocimientos, objetivos y habilidades del tema completo.
- [PIQ1 Clase practica 5 Operaciones consecutivas y desvio Triple efecto y concentrador de jugo.pdf](PIQ1%20Clase%20practica%205%20Operaciones%20consecutivas%20y%20desvio%20Triple%20efecto%20y%20concentrador%20de%20jugo.pdf) — ejercicios resueltos en la sección 7.
- [PIQ1 Clase practica 6 Sistemas heterogeneos.pdf](PIQ1%20Clase%20practica%206%20Sistemas%20heterogeneos.pdf) — teoría y ejercicio de la sección 8.
- [PIQ1 Clase practica 7 Tecnologia del cafe instantaneo.pdf](PIQ1%20Clase%20practica%207%20Tecnologia%20del%20cafe%20instantaneo.pdf) y su [enunciado](PIQ1%20Clase%20practica%207%20Tecnologia%20del%20cafe%20instantaneo_enunciado.pdf) — ejercicio integral resuelto (y su variante con recirculación) en la sección 9.
- [../TEMA 2/Conferencia 4 - Mediciones Termometricas, Carta Sicrometrica y Procesos.md](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md) — carta sicrométrica y saturación adiabática, usadas en los ejercicios de las secciones 8 y 9.
- [Complementos/Autopreparacion Balance de masa srq.pdf](Complementos/Autopreparacion%20Balance%20de%20masa%20srq.pdf) — problemas adicionales de autopreparación, referenciados en la sección 11.
