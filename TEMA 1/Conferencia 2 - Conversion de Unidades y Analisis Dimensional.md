# Tema 1 — Conferencia 2: Conversión de unidades y análisis dimensional

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuente principal:** [Conferencia 2 Tema 1 Plan E.pdf](Conferencia%202%20Tema%201%20Plan%20E.pdf)
> **Apoyo:** [Guia de estudio Tema 1.pdf](Guia%20de%20estudio%20Tema%201.pdf) · [PIQ1 Clase practica 2a Conversion de unidades.pdf](PIQ1%20Clase%20practica%202a%20Conversion%20de%20unidades.pdf) · [PIQ1 Clase practica 2b Analisis dimensional.pdf](PIQ1%20Clase%20practica%202b%20Analisis%20dimensional.pdf)
> **Continúa de:** [Conferencia 1 - Sistemas de Unidades y Dimensiones.md](Conferencia%201%20-%20Sistemas%20de%20Unidades%20y%20Dimensiones.md)
>
> Este documento cubre, paso a paso y sin omitir ningún detalle, todo lo que exige la Conferencia 2: las tres modalidades de conversión de unidades (sobre un valor numérico, en ecuaciones empíricas, y en unidades de composición) y la técnica de análisis dimensional por el método de Rayleigh. Cada ejemplo se resuelve con la aritmética completamente verificada, y el ejemplo central de análisis dimensional (coeficiente de película $h$) se desarrolla íntegro, incluyendo la deducción de la dimensión de cada variable física a partir de sus leyes físicas.

---

## 0. Repaso de la conferencia anterior (preguntas respondidas)

La Conferencia 2 abre repasando la Conferencia 1 con varias preguntas. Se responden aquí de forma explícita antes de avanzar:

**¿Cuál es la diferencia entre el sistema gravitacional y el internacional?**
En ambos hay cuatro magnitudes fundamentales, pero son distintas: el sistema Gravitacional toma como fundamentales $F,L,\theta,T$ (la masa se deriva de la fuerza), mientras que el Internacional toma $M,L,\theta,T$ (la fuerza se deriva de la masa, vía $F=ma$, resultando en el newton). Ninguno de los dos mezcla $F$ y $M$ como fundamentales simultáneas, por eso ninguno genera pares redundantes.

**¿En cuáles sistemas de unidades es la energía una unidad fundamental?**
Únicamente en el sistema de **Energía** (por definición, es el sistema construido alrededor de esa elección). En los otros cuatro sistemas, la energía es siempre una magnitud derivada.

**¿Por qué varía la dimensión de una magnitud física al cambiar el sistema de unidades?**
Porque la fórmula dimensional de una magnitud se define en función de las magnitudes fundamentales del sistema, y esas fundamentales cambian de un sistema a otro (esa es literalmente la definición de "sistema de unidades"). Por eso, por ejemplo, la energía es $E$ en el sistema de Energía pero $ML^2\theta^{-2}$ en el Internacional.

**¿Para cada par redundante, cuál es la constante que elimina la aparente inconsistencia?**
$F$–$M$ → $g_c$; $F$–$E$ → $J$; $E$–$M$ → $K=g_cJ$ (desarrollado en detalle en la Conferencia 1, sección 5).

---

## 1. Contexto y objetivos

Hasta hace pocas décadas, la mayoría de los textos y revistas técnicas de ingeniería química empleaban el **sistema de Energía inglés** (todavía usado en algunas tecnologías puntuales). Después se generalizó el trabajo con la variante métrica, y desde 1960 se ha impuesto con fuerza, a escala internacional, el **Sistema Internacional (SI)** por las ventajas que ofrece (ausencia de constantes dimensionales, coherencia entre unidades, adopción legal casi universal — ver Conferencia 1, sección 3.5).

Esta convivencia de sistemas hace que **transformar valores de un sistema a otro sea una tarea constante** en el trabajo real del ingeniero químico. Los objetivos de esta conferencia son:

- Conocer los procedimientos generales para realizar la **conversión de unidades**.
- Conocer el fundamento y las características del **análisis dimensional**.

---

## 2. Conversión de unidades

La conferencia distingue **tres modalidades** distintas de conversión de unidades, que requieren procedimientos diferentes. Es importante no confundirlas.

### 2.1 Conversión sobre el valor numérico de una magnitud

Es el caso más simple y más frecuente: se tiene un número con una unidad, y se quiere expresar exactamente la misma cantidad física con otra unidad.

**Método (método de los factores unitarios o "cadena de conversión"):** se buscan en tablas de equivalencias los factores de conversión necesarios (por ejemplo, en la Tabla B2 del texto base, en la sección I del tomo 1 de Perry's *Handbook of Chemical Engineering*, o en las tablas de vapor de J. Keenan) y se colocan **en forma de fracción que vale exactamente 1** (porque numerador y denominador representan la misma cantidad física, solo que en unidades distintas), multiplicando la cantidad original por esas fracciones de modo que las unidades no deseadas se van cancelando (como si fueran factores algebraicos) hasta llegar únicamente a las unidades deseadas.

**¿Por qué funciona esto?** Porque si, por ejemplo, $1\ \text{pie} = 30.48\ \text{cm}$, entonces la fracción $\dfrac{1\ \text{pie}}{30.48\ \text{cm}}$ vale exactamente **1** (es una igualdad, dividida entre sí misma). Multiplicar cualquier cantidad por "1" no cambia su valor físico, solo cambia la forma en que se expresa numéricamente.

#### Ejemplo resuelto: convertir $10\,000\ \text{m}^3/\text{día}$ a $\text{pie}^3/\text{s}$

Se necesita relacionar metros con pies y días con segundos. Se encadenan las equivalencias necesarias:

$$1\ \text{m}=100\ \text{cm}\,,\quad 1\ \text{pulg}=2.54\ \text{cm}\,,\quad 1\ \text{pie}=12\ \text{pulg}\,,\quad 1\ \text{día}=24\ \text{h}\,,\quad 1\ \text{h}=3600\ \text{s}$$

Se arma la cadena, con **cada fracción de equivalencia elevada al cubo** cuando la unidad a convertir es de volumen (metros cúbicos), y a la primera potencia cuando es de tiempo (días → horas → segundos):

$$10\,000\ \dfrac{\text{m}^3}{\text{día}}\left(\dfrac{100\ \text{cm}}{1\ \text{m}}\right)^{3}\left(\dfrac{1\ \text{pulg}}{2.54\ \text{cm}}\right)^{3}\left(\dfrac{1\ \text{pie}}{12\ \text{pulg}}\right)^{3}\left(\dfrac{1\ \text{día}}{24\ \text{h}}\right)\left(\dfrac{1\ \text{h}}{3600\ \text{s}}\right)$$

**Verificación numérica paso a paso:**

- $\dfrac{100}{2.54} = 39.3701$ (cm→pulg, invertido: cuántas pulgadas hay en 100 cm)
- $\dfrac{39.3701}{12} = 3.28084$ (esto es exactamente cuántos pies hay en 1 metro: $1\ \text{m} = 3.28084\ \text{pie}$)
- Al elevar al cubo: $3.28084^3 = 35.3147$ (cuántos pies cúbicos hay en 1 metro cúbico)
- El factor de tiempo: $\dfrac{1}{24\times 3600} = \dfrac{1}{86\,400} = 1.15741\times10^{-5}$ (cuántos días-equivalentes hay en 1 segundo... realmente cuántas fracciones de día representa 1 s, ya que se está convirtiendo "por día" a "por segundo")
- Multiplicando ambos factores: $35.3147 \times 1.15741\times10^{-5} = 4.087\times10^{-4}$

Este es el **factor de conversión global**: $f_{\text{conv}} = 0.0004087$. Finalmente:

$$10\,000 \times 0.0004087 = 4.087\ \text{pie}^3/\text{s}$$

**¿Por qué se puede elevar al cubo la relación de equivalencia?** Porque si $1\ \text{m} = 100\ \text{cm}$ es una igualdad entre longitudes, entonces elevar ambos lados de esa igualdad a la tercera potencia sigue siendo una igualdad válida: $(1\ \text{m})^3 = (100\ \text{cm})^3$, es decir $1\ \text{m}^3 = 10^6\ \text{cm}^3$. La igualdad se preserva porque se aplica la **misma** operación a ambos lados; por tanto la fracción $\left(\dfrac{100\ \text{cm}}{1\ \text{m}}\right)^3$ sigue valiendo exactamente 1, y se puede usar para convertir volúmenes exactamente igual que se usó la fracción original (sin elevar) para convertir longitudes.

> **Nota práctica:** las tablas de equivalencias pueden variar ligeramente según la fuente (por ejemplo, si se toma $1\ \text{pie}=0.3048\ \text{m}$ exactamente en vez de encadenar cm→pulg→pie, se pueden eliminar pasos intermedios de la conversión anterior y llegar al mismo resultado con menos operaciones). Lo importante es ser consistente dentro de un mismo cálculo y trabajar de forma organizada para minimizar el riesgo de error — precisamente la recomendación con la que abre la Conferencia 1 (sección 0.3 del documento anterior).

### 2.2 Conversión de unidades en ecuaciones empíricas

Este caso es distinto y merece explicarse con cuidado, porque **no** es una simple conversión de un número: es la transformación de toda una fórmula.

**¿Por qué es diferente?** Las ecuaciones empíricas se obtienen ajustando una expresión matemática a datos experimentales (no se derivan de leyes físicas puras), por lo que —como se vio en la Conferencia 1— **generalmente no son dimensionalmente consistentes**: sus constantes numéricas ya llevan "escondida" la información de en qué unidades específicas se midieron las variables durante el experimento. Por eso, una ecuación empírica **solo puede usarse correctamente con las unidades para las que fue ajustada**. Si se quiere usar con variables en otras unidades, hay que obtener una **nueva constante** que compense el cambio.

**Procedimiento general (el método "c" del texto, el único que se usa en este curso):**

1. Se escribe la variable en sus unidades **originales** (las de la ecuación empírica tal como está dada).
2. Se iguala esa variable a la misma variable expresada en las unidades **nuevas** que se desean usar.
3. Con las equivalencias de unidades (igual que en la sección 2.1), se obtiene un **factor de conversión** $\Phi$ que relaciona ambas.
4. Se sustituye esa relación en la ecuación original y se despeja, obteniendo una ecuación equivalente pero con una constante numérica distinta, válida para las nuevas unidades.

#### Ejemplo resuelto: coeficiente de transferencia de calor

La ecuación empírica dada es:

$$h_0 = 0.026\ \dfrac{G^{0.6}}{D^{0.4}}$$

con $h_0$ en $\text{BTU}/(\text{h·pie}^2\text{·°F})$, $G$ (velocidad másica) en $\text{lb}/(\text{h·pie}^2)$ y $D$ (diámetro) en pie. Se pide transformar la ecuación de modo que $G$ y $D$ mantengan sus unidades originales, pero $h_0$ quede expresada en $\text{cal}/(\text{h·cm}^2\text{·°C})$.

**Paso 1 — plantear la igualdad entre la variable en ambos sistemas de unidades:**

$$h_0\left(\dfrac{\text{BTU}}{\text{h·pie}^2\text{·°F}}\right) \equiv h_0'\left(\dfrac{\text{cal}}{\text{h·cm}^2\text{·°C}}\right)$$

**Paso 2 — construir el factor de conversión** encadenando las equivalencias necesarias: BTU↔cal, pie↔cm (al cuadrado, porque el área está al cuadrado), y °F↔°C (como diferencia de temperatura, es decir, escala, no punto fijo — de ahí que se use el factor $1.8$, que relaciona *tamaños de grado*, y no la fórmula completa de conversión de temperatura con el desplazamiento de 32°):

$$h_0 = h_0'\left(\dfrac{1\ \text{BTU}}{252\ \text{cal}}\right)\left(\dfrac{30.48\ \text{cm}}{1\ \text{pie}}\right)^2\left(\dfrac{1\ ^\circ\text{C}}{1.8\ ^\circ\text{F}}\right)$$

**Verificación numérica:** $30.48^2 = 929.03$; luego $929.03/252 = 3.687$; luego $3.687/1.8 = 2.048$. Es decir:

$$h_0 = 2.048\ h_0'$$

**Paso 3 — sustituir en la ecuación original** y despejar $h_0'$:

$$2.048\ h_0' = 0.026\ \dfrac{G^{0.6}}{D^{0.4}} \quad\Longrightarrow\quad h_0' = \dfrac{0.026}{2.048}\ \dfrac{G^{0.6}}{D^{0.4}} = 0.01267\ \dfrac{G^{0.6}}{D^{0.4}}$$

Esta ya es la respuesta a la primera parte: $h_0'$ en $\text{cal}/(\text{h·cm}^2\text{·°C})$, manteniendo $G$ y $D$ en sus unidades originales.

**Ahora, si además se quiere $G'$ en $\text{g}/(\text{h·cm}^2)$ y $D'$ en cm** (es decir, cambiar *todas* las variables), se repite el mismo procedimiento para cada una:

$$G\left(\dfrac{\text{lb}}{\text{h·pie}^2}\right) = G'\left(\dfrac{\text{g}}{\text{h·cm}^2}\right)\left(\dfrac{1\ \text{lb}}{453.6\ \text{g}}\right)\left(\dfrac{30.48\ \text{cm}}{1\ \text{pie}}\right)^2 = 2.048\ G'$$

(numéricamente: $929.03/453.6 = 2.048$ — coincide por casualidad numérica con el factor de $h_0$, pero surge de un cociente distinto: aquí no interviene ningún factor de temperatura).

$$D(\text{pie}) = D'(\text{cm})\left(\dfrac{1\ \text{pie}}{30.48\ \text{cm}}\right) = 0.0328\ D'$$

**Sustituyendo ambos** en la ecuación ya obtenida ($2.048\ h_0' = 0.026\ G^{0.6}/D^{0.4}$, pero ahora con $G=2.048\,G'$ y $D=0.0328\,D'$):

$$2.048\ h_0' = 0.026\ \dfrac{(2.048\ G')^{0.6}}{(0.0328\ D')^{0.4}}$$

**Verificación numérica del coeficiente final:** $2.048^{0.6} = 1.538$ y $0.0328^{0.4}=0.2548$, por lo que

$$0.026 \times \dfrac{1.538}{0.2548} = 0.026 \times 6.036 = 0.1569$$

$$h_0' = \dfrac{0.1569}{2.048}\ \dfrac{G'^{0.6}}{D'^{0.4}} = 0.0766\ \dfrac{G'^{0.6}}{D'^{0.4}}$$

**¿Qué semejanzas y diferencias hay entre la ecuación original y las transformadas?** Los **exponentes** (0.6 y −0.4) son exactamente los mismos en las tres versiones de la ecuación: el exponente de una variable no cambia al convertir unidades, porque el cambio de unidades es solo una **reescala** lineal (o de potencia fija) de cada variable, no una modificación de la relación funcional entre ellas. Lo único que cambia es el **coeficiente numérico** (0.026 → 0.01267 → 0.0766), que absorbe todos los factores de conversión de las distintas variables involucradas. Esto es justamente lo que distingue este caso del caso de las ecuaciones *teóricas* (Conferencia 1): allí la consistencia dimensional garantiza que la forma se mantiene sin ajustar nada; aquí, al no haber consistencia dimensional de partida, cada cambio de unidad exige recalcular el coeficiente.

### 2.3 Conversión de unidades de composición

Esta es la tercera modalidad, y es conceptualmente distinta de las dos anteriores porque no se trata de convertir una magnitud física "pura" (como longitud o tiempo) sino de **re-expresar cómo está distribuida una mezcla** entre sus componentes.

Las formas más comunes de expresar composición son:

- Concentración molar y concentración másica (por ejemplo, kmol/L o g/L).
- Fracciones (o porcentajes) másicas y molares.
- Moles (o masa) de una sustancia por mol (o masa) de mezcla **libre** de algún componente seleccionado (composición "en base libre de" cierto componente).

Para convertir entre estas formas hace falta, casi siempre, información **adicional** sobre la mezcla: densidad, volumen específico o molar, y masa molar promedio. Estas propiedades actúan, en la práctica, como **factores de conversión específicos de esa mezcla particular** (a diferencia de los factores de la sección 2.1, que son universales — 1 pie siempre son 30.48 cm — estos dependen de qué sustancias forman la mezcla).

#### Ejemplo resuelto: de composición másica a composición molar

Una mezcla binaria tiene la composición másica: $\text{O}_2 = 60\%$, $\text{Cl}_2 = 40\%$. Se pide expresarla en porcentajes molares.

**Paso 1 — tomar una base de cálculo cómoda:** 100 kg de mezcla. Con esa base, los porcentajes másicos se convierten directamente en kilogramos: 60 kg de O₂ y 40 kg de Cl₂.

**Paso 2 — convertir masa a moles usando la masa molar de cada sustancia** ($M_{\text{O}_2}=32\ \text{g/mol}=32\ \text{kg/kmol}$; $M_{\text{Cl}_2}\approx 70.9\ \text{kg/kmol}$):

$$n_{\text{O}_2} = \dfrac{60\ \text{kg}}{32\ \text{kg/kmol}} = 1.875\ \text{kmol}\,,\qquad n_{\text{Cl}_2} = \dfrac{40\ \text{kg}}{70.9\ \text{kg/kmol}} = 0.564\ \text{kmol}$$

**Paso 3 — sumar para obtener el total de moles:**

$$n_T = 1.875 + 0.564 = 2.439\ \text{kmol}$$

**Paso 4 — calcular las fracciones molares como "la parte sobre el todo", multiplicado por 100:**

$$\%\text{O}_2 = \dfrac{1.875}{2.439}\times100 = 76.87\%\,,\qquad \%\text{Cl}_2 = \dfrac{0.564}{2.439}\times100 = 23.13\%$$

> *Nota:* el material original de la conferencia reporta 76.91 % y 23.09 %, usando $M_{\text{Cl}_2}=71\ \text{kg/kmol}$ exactamente (un redondeo habitual, ya que $\text{Cl}=35.45$ y $2\times35.45=70.9\approx71$). La pequeña diferencia frente al 76.87 %/23.13 % calculado aquí con $M_{\text{Cl}_2}=70.9$ es solo cuestión de redondeo de la masa molar utilizada — el **procedimiento** es idéntico y es lo que realmente importa retener.

**¿Existe alguna "correspondencia numérica" entre ambos conjuntos de porcentajes?** Aquí conviene ser muy preciso para evitar una confusión común: el **60 %/40 % másico no es igual, ni tiene por qué acercarse, al 76.9 %/23.1 % molar** — de hecho son bastante distintos, precisamente *porque* el O₂ y el Cl₂ tienen masas molares diferentes (32 frente a ~71 kg/kmol). Si ambos gases tuvieran la misma masa molar, entonces sí, el porcentaje másico y el molar coincidirían exactamente. **Lo que sí es cierto siempre** (y es probablemente lo que la conferencia quiere resaltar con esa observación) es que, dentro de *cada* forma de expresar la composición, los porcentajes de todos los componentes **deben sumar 100 %** — eso no es una coincidencia sino una consecuencia directa de que no se pierde masa ni moles al pasar de un componente a otro: $76.87+23.13=100$, igual que $60+40=100$. Esa es la única "correspondencia" garantizada matemáticamente; los valores concretos de cada porcentaje, en general, **sí cambian** al pasar de base másica a base molar.

**¿Cuál es la masa molar promedio de esta mezcla?** Es una **suma ponderada** de las masas molares de cada componente puro, usando la fracción *molar* como factor de ponderación:

$$\overline{MM} = \sum x_i\,M_i = 0.7687(32) + 0.2313(70.9) \approx 24.60 + 16.40 = 41.0\ \text{kg/kmol}$$

(coherente con el orden de magnitud esperado para una mezcla de O₂ y Cl₂: entre 32 y 71 kg/kmol.)

#### Ejemplo complementario resuelto: el proceso inverso (de composición molar a másica)

La propia Conferencia 2 señala que el proceso inverso (de % molar a % másico) sigue "el mismo procedimiento realizado en la conferencia", y ese proceso inverso se completa en la Clase Práctica 2a con un caso de la salida de un reformador de metano. Se incluye aquí completo porque cierra el ciclo del concepto (permite ver la conversión en ambos sentidos):

Composición molar de salida: $\text{CH}_4=6\%$, $\text{H}_2\text{O}=3\%$, $\text{CO}_2=10\%$, $\text{CO}=28\%$, $\text{H}_2=53\%$.

**Base de cálculo:** 100 kmol de mezcla ⟹ cada porcentaje molar se convierte directamente en kmol.

| Sustancia | % molar = kmol | $M_i$ (kg/kmol) | $F_i = \text{kmol}\times M_i$ (kg) | $x_i$ (másica) | $X_i$ (%) |
|---|---|---|---|---|---|
| CH₄ | 6 | 16 | 96 | 96/1480 | 6.49 |
| H₂O | 3 | 18 | 54 | 54/1480 | 3.65 |
| CO₂ | 10 | 44 | 440 | 440/1480 | 29.73 |
| CO | 28 | 28 | 784 | 784/1480 | 52.97 |
| H₂ | 53 | 2 | 106 | 106/1480 | 7.16 |
| **Total** | **100** | — | **1480** | 1.000 | **100.00** |

Los pasos son exactamente simétricos a los del ejemplo anterior, solo que en la dirección opuesta: (1) tomar 100 kmol como base, (2) convertir kmol a kg multiplicando por la masa molar de cada especie, (3) sumar para obtener la masa total de mezcla (1480 kg), (4) dividir cada masa parcial entre la masa total para obtener la fracción másica. De paso, la masa molar promedio de esta mezcla es:

$$\overline{MM} = 0.06(16)+0.03(18)+0.10(44)+0.28(28)+0.53(2) = 0.96+0.54+4.4+7.84+1.06 = 14.8\ \text{kg/kmol}$$

que también puede verificarse como $\overline{MM} = \dfrac{\text{masa total}}{\text{moles totales}} = \dfrac{1480\ \text{kg}}{100\ \text{kmol}} = 14.8\ \text{kg/kmol}$ — la misma cifra por dos caminos distintos, lo cual confirma que el cálculo es consistente.

---

## 3. Análisis dimensional

### 3.1 El problema que resuelve

Uno de los problemas centrales de la ingeniería química es **obtener expresiones matemáticas que describan un fenómeno físico**. Hay tres vías posibles para lograrlo:

1. Obtener la expresión matemática directamente a partir de **leyes básicas** (físicas) ya conocidas.
2. Plantear **ecuaciones diferenciales** que describan el fenómeno, e integrarlas.
3. Obtener una **ecuación empírica** mediante experimentación pura (variar cada variable, medir la respuesta, ajustar una curva).

Cuando el fenómeno depende de **muchas variables**, las dos primeras vías se vuelven extremadamente complejas de resolver analíticamente, y la tercera se vuelve extremadamente costosa: si hay, por ejemplo, 5 variables independientes y se quisieran probar 10 valores de cada una manteniendo las demás fijas, el número de experimentos necesarios crece muy rápido. Aquí es donde interviene el **análisis dimensional**: un método intermedio, algebraico, entre el desarrollo analítico puro y la experimentación pura.

### 3.2 Características fundamentales del método

1. Es un **método algebraico** intermedio entre el desarrollo analítico y la experimentación: no requiere resolver ecuaciones diferenciales, pero tampoco es "probar al azar" — usa la estructura dimensional de las variables para guiar el resultado.
2. Se apoya en la **consistencia dimensional** que debe tener cualquier ecuación teórica que describa el fenómeno (el mismo principio de la Conferencia 1, sección 5.1), aunque la ecuación final en sí no se conozca todavía.
3. Opera con las **dimensiones** de las magnitudes físicas del fenómeno, de acuerdo con el sistema de unidades elegido.
4. Permite obtener la **forma** en que están relacionadas las magnitudes (qué variables se agrupan y cómo), pero **no** puede dar resultados numéricos (los exponentes y coeficientes finales) a menos que se complementen con pruebas experimentales.
5. Los grupos de variables obtenidos son siempre **adimensionales** (sin unidades).
6. Es imprescindible **conocer de antemano todas las variables** que influyen en el fenómeno (si se omite una variable relevante, el resultado será incorrecto o incompleto), así como las constantes dimensionales necesarias según el sistema de unidades empleado.

### 3.3 Ejemplo introductorio: fuerza de arrastre sobre una esfera

Una esfera que se mueve dentro de un fluido experimenta una **fuerza de arrastre** $F_D$ que depende de: la densidad del fluido $\rho$, la velocidad del fluido $v$, el diámetro de la esfera $D$, y la viscosidad del fluido $\mu$. Es decir:

$$F_D = f(\rho,\,v,\,D,\,\mu)$$

Esto son **5 variables** ($F_D,\rho,v,D,\mu$) relacionadas por una función desconocida $f$. El análisis dimensional permite demostrar que esta relación puede reescribirse usando solamente **2 grupos adimensionales**:

$$\dfrac{F_D}{\rho\,D^2\,v^2}\ =\ \Phi\!\left(\dfrac{\rho\,D\,v}{\mu}\right)$$

(la conferencia lo escribe de forma equivalente como $\left(\dfrac{F_D}{\rho D v \mu}\right)$ y $\left(\dfrac{\rho D v}{\mu}\right)$ como los dos grupos, y señala que la forma funcional exacta entre ellos, $\Phi$, solo puede obtenerse mediante diseño experimental — el análisis dimensional da la *estructura*, no los números).

Vale la pena notar, como observación adicional (no está en el texto original, pero es información estándar de ingeniería química directamente relevante): el grupo $\dfrac{\rho\,D\,v}{\mu}$ es exactamente el **número de Reynolds**, y el grupo que involucra a $F_D$ es (una variante de) el **coeficiente de arrastre**. Este es el ejemplo clásico con el que se suele introducir el análisis dimensional en mecánica de fluidos, precisamente porque **reduce el problema de 5 variables a solo 2 grupos**, lo que significa que, en vez de diseñar experimentos variando 4 variables independientes por separado, basta con variar **un solo grupo** (el número de Reynolds) y medir la respuesta de **un solo grupo** (el coeficiente de arrastre) — un ahorro enorme de tiempo y recursos experimentales.

### 3.4 Los métodos existentes

Existen tres métodos clásicos para realizar análisis dimensional: el **método de Rayleigh**, el **de Buckingham** (teorema $\pi$) y el **de Hunsaker**. La conferencia aclara que solo es necesario dominar uno de ellos para este curso, y se elige el **método de Rayleigh**.

### 3.5 Método de Rayleigh

#### 3.5.1 Las tres suposiciones del método

1. La relación entre las variables del fenómeno es **dimensionalmente consistente** (aunque no se conozca todavía su forma exacta).
2. Cada variable tiene una fórmula dimensional definida, de acuerdo con el sistema de unidades empleado (exactamente como en la Conferencia 1).
3. Cualquier variable del fenómeno puede expresarse como una **serie infinita de potencias** de las restantes variables.

#### 3.5.2 Los seis pasos de la metodología

1. Se establece la relación funcional entre las variables: por ejemplo, $h = f(C_p,\,k,\,\mu,\,l,\,\Delta T)$.
2. La variable dependiente ($h$, en este caso) se expresa como una **serie infinita** de potencias del resto de variables:
   $$h = \sum_{i=1}^{\infty} \alpha_i\; C_p^{\,a_i}\,k^{\,b_i}\,\mu^{\,c_i}\,l^{\,d_i}\,\Delta T^{\,e_i}$$
3. Como **todos** los términos de esa serie deben tener la misma dimensión (para que la suma tenga sentido dimensionalmente), basta con analizar el **primer término**:
   $$[h] = [C_p]^{a}\,[k]^{b}\,[\mu]^{c}\,[l]^{d}\,[\Delta T]^{e}$$
4. Se busca, en el sistema de unidades elegido, la dimensión de **cada** variable física, y se sustituyen en la ecuación anterior. Igualando los exponentes de cada magnitud fundamental en ambos lados de la igualdad, se obtiene un **sistema de ecuaciones lineales** (una ecuación por cada magnitud fundamental del sistema de unidades).
5. Se resuelve ese sistema de ecuaciones, dejando los exponentes en función de una o más variables "libres" (alfanuméricas), ya que —como se verá— casi siempre hay **menos ecuaciones que incógnitas**.
6. Finalmente, se agrupan las variables originales según los exponentes obtenidos, formando los **grupos adimensionales**.

#### 3.5.3 Ejemplo completo y resuelto: coeficiente de enfriamiento de un sólido en aire

Este es el ejemplo con el que la propia Conferencia 2 introduce el método (y que se completa numéricamente en la Clase Práctica 2b). El coeficiente de enfriamiento (o coeficiente de película) $h$ de un sólido en contacto con aire depende de:

- $C_p$ — capacidad calorífica
- $k$ — conductividad térmica
- $\mu$ — viscosidad
- $l$ (o $L$) — longitud característica
- $\Delta T$ — diferencia de temperatura

Es decir: $h = f(C_p,\,k,\,\mu,\,l,\,\Delta T)$.

**Paso 1 y 2 — planteamiento:** siguiendo la metodología, se toma solo el primer término de la serie:

$$[h] = [C_p]^{a}\,[k]^{b}\,[\mu]^{c}\,[l]^{d}\,[\Delta T]^{e}$$

**Paso 3 — obtener la dimensión de cada variable en el sistema Internacional.**

Aquí conviene detenerse, porque la conferencia da estas dimensiones directamente, pero vale la pena **deducirlas** desde las leyes físicas correspondientes (ninguna es arbitraria):

- **Viscosidad $\mu$** — de la ley de viscosidad de Newton, $\tau = \mu\,\dfrac{dv}{dy}$, donde $\tau$ es un esfuerzo cortante (fuerza/área). En el SI, $[\tau] = [F]/[L^2] = (ML\theta^{-2})/L^2 = ML^{-1}\theta^{-2}$, y $\left[\dfrac{dv}{dy}\right] = \dfrac{L\theta^{-1}}{L} = \theta^{-1}$. Despejando: $[\mu] = [\tau]/\theta^{-1} = ML^{-1}\theta^{-2}\cdot\theta = ML^{-1}\theta^{-1}$.
- **Conductividad térmica $k$** — de la ley de Fourier, $q = -k\,A\,\dfrac{dT}{dx}$, donde $q$ es un flujo de calor (energía/tiempo): $[q]=[E]/\theta = ML^2\theta^{-2}/\theta = ML^2\theta^{-3}$. Con $[A]=L^2$ y $\left[\dfrac{dT}{dx}\right]=T/L$: despejando, $[k] = \dfrac{[q]}{[A]\cdot[dT/dx]} = \dfrac{ML^2\theta^{-3}}{L^2\cdot(T/L)} = ML\theta^{-3}T^{-1}$.
- **Coeficiente de película $h$** — de la ley de enfriamiento de Newton, $q = h\,A\,\Delta T$: despejando, $[h] = \dfrac{[q]}{[A]\cdot[\Delta T]} = \dfrac{ML^2\theta^{-3}}{L^2\cdot T} = M\theta^{-3}T^{-1}$.
- **Capacidad calorífica $C_p$** — ya deducida en la Conferencia 1 (sección 4.4) para el sistema Internacional: $[C_p]=L^2\theta^{-2}T^{-1}$.
- **Longitud característica $l$** — trivialmente $[l]=L$.
- **Diferencia de temperatura $\Delta T$** — trivialmente $[\Delta T]=T$.

En resumen:

$$[h]=M\theta^{-3}T^{-1}\,,\ \ [\mu]=ML^{-1}\theta^{-1}\,,\ \ [C_p]=L^2\theta^{-2}T^{-1}\,,\ \ [l]=L\,,\ \ [k]=ML\theta^{-3}T^{-1}\,,\ \ [\Delta T]=T$$

Nótese que el sistema Internacional se elige aquí precisamente porque, como se vio en la Conferencia 1, **no requiere ninguna constante dimensional adicional**, simplificando el álgebra.

**Paso 4 — ecuación de homogeneidad dimensional.** Sustituyendo todas las dimensiones en $[h] = [C_p]^{a}[k]^{b}[\mu]^{c}[l]^{d}[\Delta T]^{e}$:

$$M\theta^{-3}T^{-1} = \left(L^2\theta^{-2}T^{-1}\right)^{a}\left(ML\theta^{-3}T^{-1}\right)^{b}\left(ML^{-1}\theta^{-1}\right)^{c}\,L^{d}\,T^{e}$$

Ahora se **iguala el exponente de cada magnitud fundamental** en ambos lados (esto es lo que garantiza que la igualdad tenga sentido dimensional: para que dos expresiones con $M,L,\theta,T$ sean iguales, cada una de esas cuatro "bases" debe tener el mismo exponente a ambos lados):

$$
\begin{aligned}
M:&\quad 1 = b + c\\
L:&\quad 0 = 2a + b - c + d\\
\theta:&\quad -3 = -2a -3b -c\\
T:&\quad -1 = -a - b + e
\end{aligned}
$$

**Paso 5 — resolver el sistema.** Hay **4 ecuaciones** y **5 incógnitas** ($a,b,c,d,e$), así que el sistema no tiene solución única: queda **1 variable independiente** (grado de libertad = incógnitas − ecuaciones = 5 − 4 = 1). La elección de cuál variable dejar libre es **arbitraria** — cualquier elección válida conduce a un conjunto de grupos adimensionales igualmente correcto (aunque distinto en su forma explícita; ver la discusión de la pregunta (a) más abajo). Siguiendo la conferencia, se elige la variable $b$ como libre.

Despejando todo en función de $b$:

- De la ecuación de $M$: $c = 1-b$.
- Sustituyendo en la ecuación de $\theta$: $-3 = -2a - 3b - (1-b) = -2a - 3b - 1 + b = -2a -2b -1$, de donde $-2=-2a-2b$, es decir $1=a+b$, luego $a = 1-b$.
- Sustituyendo $a$ y $b$ en la ecuación de $T$: $-1 = -(1-b) - b + e = -1+b-b+e = -1+e$, de donde $e=0$.
- Sustituyendo $a,b,c$ en la ecuación de $L$: $0 = 2(1-b) + b - (1-b) + d = 2-2b+b-1+b+d = 1+d$, de donde $d=-1$.

**Resumen de exponentes:**

$$a=1-b\,,\quad c=1-b\,,\quad d=-1\,,\quad e=0\,,\quad b=b\ \text{(libre)}$$

**Paso 6 — sustituir de vuelta y agrupar.** Sustituyendo estos exponentes en $[h]=[C_p]^{a}[k]^{b}[\mu]^{c}[l]^{d}[\Delta T]^{e}$:

$$h = C_p^{\,1-b}\;k^{\,b}\;\mu^{\,1-b}\;l^{-1}\;\Delta T^{\,0}$$

Reagrupando los términos con exponente $b$ por un lado y los que tienen exponente $(1-b)$ por otro (separando la parte "fija" de la parte que depende del parámetro libre $b$):

$$h = C_p\,\mu^{-1}\;l^{-1}\;\left(\dfrac{k}{C_p\,\mu}\right)^{b}\quad\Longrightarrow\quad \dfrac{h\,l}{C_p\,\mu} = \left(\dfrac{k}{C_p\,\mu}\right)^{b}$$

Que también puede escribirse como una función implícita de dos grupos adimensionales:

$$f\!\left(\dfrac{h\,l}{C_p\,\mu},\ \dfrac{k}{C_p\,\mu}\right) = 0$$

**Se obtuvieron exactamente $n+1=2$ grupos** (donde $n=1$ es el número de variables independientes del sistema de ecuaciones) — este resultado coincide con la regla general del **teorema $\pi$ de Buckingham** (el segundo de los tres métodos mencionados en la sección 3.4): el número de grupos adimensionales que se pueden formar con un conjunto de variables es igual al número de variables totales menos el número de magnitudes fundamentales independientes involucradas ($6$ variables $- 4$ magnitudes fundamentales $= 2$ grupos), confirmando que el método de Rayleigh y el de Buckingham, aunque procedimentalmente distintos, deben coincidir en este número.

**La ecuación final que describe el fenómeno** (asumiendo, como es típico en estas correlaciones empíricas de transferencia de calor, una relación potencial entre los dos grupos, con una constante $\alpha$ y un exponente $b$ que deben determinarse experimentalmente):

$$\dfrac{h\,l}{C_p\,\mu} = \alpha\left(\dfrac{k}{C_p\,\mu}\right)^{b}$$

Aquí es donde el análisis dimensional **llega hasta donde puede llegar por sí solo**: da la estructura de la ecuación (qué grupos y cómo se combinan), pero los valores numéricos de $\alpha$ y $b$ solo pueden obtenerse realizando **experimentos reales** y ajustando los datos (regresión), exactamente como señala la característica #4 del método (sección 3.2).

**Prueba de que los grupos son realmente adimensionales.** Esta comprobación es análoga a la de consistencia dimensional de la Conferencia 1: se sustituyen las dimensiones de cada variable y se verifica que todo se cancela, dando 1 (es decir, sin dimensión):

$$\dfrac{h\,l}{C_p\,\mu} = \dfrac{(M\theta^{-3}T^{-1})(L)}{(L^2\theta^{-2}T^{-1})(ML^{-1}\theta^{-1})} = \dfrac{M L\,\theta^{-3}T^{-1}}{M L\,\theta^{-3}T^{-1}} = 1\ \checkmark$$

$$\dfrac{k}{C_p\,\mu} = \dfrac{ML\theta^{-3}T^{-1}}{(L^2\theta^{-2}T^{-1})(ML^{-1}\theta^{-1})} = \dfrac{ML\theta^{-3}T^{-1}}{ML\theta^{-3}T^{-1}} = 1\ \checkmark$$

Ambos grupos son, en efecto, adimensionales. Esto confirma, con un ejemplo concreto, por qué es preferible trabajar con la ecuación en términos de estos 2 grupos en lugar de la relación original entre las 6 variables: **cada grupo adimensional actúa como una sola "variable" nueva**, reduciendo drásticamente la complejidad del problema experimental (igual que en el ejemplo de la esfera de la sección 3.3, donde 5 variables se redujeron a 2 grupos).

### 3.6 Preguntas de discusión (respondidas)

**a) ¿Se obtendrían los mismos grupos adimensionales si se hubiera tomado $a$ o $c$ como variable independiente en lugar de $b$?**
No. La elección de la variable libre es arbitraria en el sentido de que **cualquier elección es igualmente válida**, pero conduce a una representación distinta (aunque equivalente en información) de los grupos adimensionales. Todos los conjuntos de grupos obtenidos por distintas elecciones son **combinaciones algebraicas unos de otros** (ver la siguiente pregunta), así que ninguno es "más correcto" que otro — simplemente son formas alternativas de agrupar la misma información física.

**b) ¿Cómo se pueden obtener grupos distintos a los ya hallados?**
Por **combinación** de los grupos originales (multiplicándolos o dividiéndolos entre sí, ya que el producto o cociente de dos cantidades adimensionales sigue siendo adimensional). Por ejemplo, definiendo:

$$\pi_1 = \dfrac{hl}{C_p\mu}\,,\qquad \pi_2=\dfrac{k}{C_p\mu}\,,\qquad \pi_3=\dfrac{\pi_1}{\pi_2}=\dfrac{hl}{k}\ \ (\textbf{número de Nusselt, } Nu)\,,\qquad \pi_4=\dfrac{1}{\pi_2}=\dfrac{C_p\mu}{k}\ \ (\textbf{número de Prandtl, } Pr)$$

Estos dos últimos grupos ($Nu$ y $Pr$) son, de hecho, **números adimensionales clásicos y ampliamente usados en toda la ingeniería de transferencia de calor**: el número de Nusselt compara la transferencia de calor por convección con la que habría solo por conducción, y el número de Prandtl compara la difusividad de cantidad de movimiento (viscosidad) con la difusividad térmica. Que aparezcan exactamente aquí, a partir de un ejercicio de análisis dimensional relativamente sencillo, ilustra el poder real del método: estos números no se "inventaron" arbitrariamente, sino que emergen naturalmente del análisis dimensional del fenómeno físico de convección.

**c) Si se desea describir el fenómeno con tres grupos adimensionales, ¿qué hay que hacer?**
Seleccionar **dos** variables independientes en vez de una sola (en el paso 5 de la metodología), lo cual generaría $n+1$ grupos con $n=2$, es decir, 3 grupos. La conferencia aclara que la selección de esas dos variables también es arbitraria, y que si se elige $c$ (el exponente de la viscosidad) como una de ellas, el resultado son precisamente los números de Nusselt y Prandtl obtenidos directamente (sin necesidad del paso de combinación de la pregunta b).

**d) Si el método se aplicara en el sistema de Energía en lugar del Internacional, ¿habría que empezar todo de nuevo?**
No necesariamente: **se pueden probar los mismos grupos ya obtenidos**, sustituyendo ahora las dimensiones de cada variable según el sistema de Energía. Puede ocurrir que aparezcan pares redundantes (ver Conferencia 1, sección 5.2), en cuyo caso hay que introducir la constante dimensional correspondiente. Para este ejemplo en particular, verificando con las dimensiones del sistema de Energía ($[h]=E\theta^{-1}L^{-2}T^{-1}$, $[\mu]=ML^{-1}\theta^{-1}$, $[C_p]=EM^{-1}T^{-1}$, $[k]=E\theta^{-1}L^{-1}T^{-1}$, $[l]=L$):

$$\dfrac{hl}{C_p\mu} = \dfrac{(E\theta^{-1}L^{-2}T^{-1})(L)}{(EM^{-1}T^{-1})(ML^{-1}\theta^{-1})} = \dfrac{E\theta^{-1}L^{-1}T^{-1}}{E\theta^{-1}L^{-1}T^{-1}} = 1\ \checkmark$$

$$\dfrac{k}{C_p\mu} = \dfrac{E\theta^{-1}L^{-1}T^{-1}}{(EM^{-1}T^{-1})(ML^{-1}\theta^{-1})} = \dfrac{E\theta^{-1}L^{-1}T^{-1}}{E\theta^{-1}L^{-1}T^{-1}} = 1\ \checkmark$$

En este caso particular, **no aparece ningún problema en el sistema de Energía**: ambos grupos se conservan perfectamente adimensionales sin necesidad de ninguna constante dimensional adicional. Esto ocurre porque, en cada grupo, los exponentes de $M$, $F$ y $E$ nunca quedan "sueltos" de forma independiente — siempre se cancelan entre sí antes de que pueda manifestarse un par redundante.

---

## 4. Preguntas de repaso finales de la conferencia (respondidas)

**Si cambian las unidades de las variables de una ecuación empírica, ¿qué se debe hacer?**
No se puede simplemente sustituir los nuevos valores numéricos en la ecuación original (porque, al no ser dimensionalmente consistente, el coeficiente numérico de la ecuación es válido *solo* para el conjunto específico de unidades con el que fue ajustada). Es obligatorio repetir el procedimiento de la sección 2.2: obtener el factor de conversión $\Phi$ para cada variable que cambie de unidad, sustituirlo en la ecuación original, y despejar el **nuevo coeficiente numérico** válido para las nuevas unidades.

**¿Para qué tipo de fenómeno físico el análisis dimensional presenta más utilidad?**
Para fenómenos físicos en los que intervienen **muchas variables** y para los cuales derivar la ecuación exacta a partir de primeros principios (leyes físicas o ecuaciones diferenciales) resultaría extremadamente complejo, mientras que determinarla puramente por experimentación (variando cada variable por separado) sería extremadamente costoso en tiempo y recursos. Es el caso típico de los fenómenos de **transporte** (mecánica de fluidos, transferencia de calor y transferencia de masa) que se estudian en cursos posteriores de la carrera — el ejemplo de la esfera (sección 3.3) y el del coeficiente de película (sección 3.5.3) son representativos de ese tipo de fenómeno.

---

## 5. Cierre del Tema 1

Con esta conferencia se completa el **estudio teórico del Tema 1**, que —como señala el propio material— es de "uso y aplicación general": sus herramientas (sistemas de unidades, dimensión, consistencia dimensional, conversión de unidades y análisis dimensional) no se usan solo en este tema, sino en **toda** la asignatura (Temas 2, 3 y 4) y, en general, en cualquier asignatura de la carrera que involucre cálculos de ingeniería.

Conviene señalar, según indica la [Guia de estudio Tema 1.pdf](Guia%20de%20estudio%20Tema%201.pdf), que en la evaluación de este tema **no se evalúa el análisis dimensional** (queda como contenido de autoestudio, desarrollado en la segunda parte de esta conferencia y de la Clase Práctica 2b); sí se evalúan los **sistemas y conversión de unidades** y la **consistencia dimensional**.

### Orientaciones para el estudio

- **Texto tomo I, páginas 25–29 y 37–40** (Cruz, Luis; Pons, Antonio. *Introducción a la Ingeniería Química*) — no incluido entre los archivos de esta carpeta; hacer especial énfasis en los ejemplos resueltos 1.4 (pág. 27), 1.5 (pág. 28), 1.6 (pág. 29), 1.7 (pág. 33, solo el método c) y 1.8 (pág. 40, solo por Rayleigh), todos referenciados explícitamente por la conferencia.
- Dentro de esta carpeta, el material que complementa directamente esta conferencia es [PIQ1 Clase practica 2a Conversion de unidades.pdf](PIQ1%20Clase%20practica%202a%20Conversion%20de%20unidades.pdf) (ejercicios adicionales resueltos de las tres modalidades de conversión) y [PIQ1 Clase practica 2b Analisis dimensional.pdf](PIQ1%20Clase%20practica%202b%20Analisis%20dimensional.pdf) (desarrollo numérico completo del ejemplo de la sección 3.5.3 de este documento).

El siguiente tema de la asignatura (Tema 2) inicia el estudio de técnicas de ingeniería propiamente dichas, comenzando por las **mezclas vapor–gas**, y ya no se centra en herramientas de cálculo generales sino en fenómenos físico-químicos específicos.

---

## Referencias / fuentes usadas en este documento

- [Conferencia 2 Tema 1 Plan E.pdf](Conferencia%202%20Tema%201%20Plan%20E.pdf) — fuente principal del contenido teórico y de los ejemplos.
- [Guia de estudio Tema 1.pdf](Guia%20de%20estudio%20Tema%201.pdf) — alcance de la evaluación del tema.
- [PIQ1 Clase practica 2a Conversion de unidades.pdf](PIQ1%20Clase%20practica%202a%20Conversion%20de%20unidades.pdf) — ejemplo complementario de composición (reformación del metano).
- [PIQ1 Clase practica 2b Analisis dimensional.pdf](PIQ1%20Clase%20practica%202b%20Analisis%20dimensional.pdf) — desarrollo numérico completo del método de Rayleigh aplicado al coeficiente de película.
- [Conferencia 1 - Sistemas de Unidades y Dimensiones.md](Conferencia%201%20-%20Sistemas%20de%20Unidades%20y%20Dimensiones.md) — base conceptual (sistemas de unidades, dimensión, pares redundantes) sobre la que se construye esta conferencia.
