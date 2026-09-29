# Tema 3 — Clases Prácticas 9, 10, 11 y 12: balance de masa con reacción química (paso a paso)

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuentes principales:** [PIQ1 Clase practica 9 Reactor secador Reactor catalitico.pdf](PIQ1%20Clase%20practica%209%20Reactor%20secador%20Reactor%20catalitico.pdf) · [PIQ1 Clase practica 10 Reacciones de combustion Mezclador horno.pdf](PIQ1%20Clase%20practica%2010%20Reacciones%20de%20combustion%20Mezclador%20horno.pdf) · [PIQ1 Clases practicas 11 y 12 Planta de produccion de amoniaco.pdf](PIQ1%20Clases%20practicas%2011%20y%2012%20Planta%20de%20produccion%20de%20amoniaco.pdf)
> **Teoría de base (léase antes si algo no se entiende):** [Conferencia 6 - Balance de Masa con Reaccion Quimica.md](Conferencia%206%20-%20Balance%20de%20Masa%20con%20Reaccion%20Quimica.md)
> **Apoyo numérico:** [../TEMA 2/Conferencia 4 - Mediciones Termometricas, Carta Sicrometrica y Procesos.md](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md) (carta sicrométrica y punto de rocío, usados en CP10)
>
> Este documento es un desarrollo **independiente** de las Clases Prácticas 9, 10, 11 y 12, pensado para poder seguirse sin tener que ir y venir a otro archivo: cada fórmula se recuerda antes de usarse, cada sustitución numérica se muestra completa (no se "saltan" pasos de álgebra ni conversiones de unidades), y se explica el **porqué** de cada decisión de cálculo. Los cuatro ejercicios de estas cuatro clases prácticas se resuelven íntegros, verificando toda la aritmética de forma independiente y señalando (y corrigiendo) las erratas numéricas detectadas en el material fuente.

---

## 0. Qué son estas clases prácticas y qué se espera lograr con ellas

Una "clase práctica" (CP), a diferencia de una conferencia, no introduce teoría nueva: **ejercita** la teoría ya explicada en la conferencia correspondiente. Las cuatro clases prácticas de este documento ejercitan, todas, el balance de masa **con** reacción química de la [Conferencia 6](Conferencia%206%20-%20Balance%20de%20Masa%20con%20Reaccion%20Quimica.md), en orden creciente de dificultad:

- **CP9** ejercita lo más básico: un reactor de neutralización sencillo (balance por componente) y un reactor catalítico con reacciones desconocidas o múltiples (balance por elementos).
- **CP10** se enfoca en las particularidades de la **combustión**: aire teórico, % de exceso, % de completamiento, y el cálculo del punto de rocío de los gases de combustión.
- **CP11-12** es el ejercicio integrador de cierre de todo el Tema 3: una planta de producción de amoníaco con **reciclo y purga**, que obliga a distinguir entre la conversión de un solo paso por el reactor y la conversión global de todo el proceso.

---

## 1. Formulario de partida (recordatorio, sin re-derivar)

### 1.1 Balance con reacción química

$$\textbf{Para un reactivo:}\qquad \left[\text{entra}\right] = \left[\text{sale}\right] + \left[\text{reacciona}\right]$$

$$\textbf{Para un producto:}\qquad \left[\text{sale}\right] = \left[\text{entra}\right] + \left[\text{forma}\right]$$

$$\textbf{Para un inerte (no reacciona ni se forma):}\qquad \left[\text{sale}\right] = \left[\text{entra}\right]$$

**La "tabla de balance"**, la herramienta que se usa en todos los ejercicios de este documento para no perder de vista ningún término:

| Compuesto | Entra | Reacciona | Forma | Sale |
|---|---|---|---|---|

### 1.2 % de Conversión y % de Exceso

$$\%\text{Conversión} = \dfrac{\text{Cantidad de reactivo (limitante) que reacciona}}{\text{Cantidad total de ese reactivo alimentado}}\times 100$$

$$\%\text{Exceso} = \dfrac{\text{Cantidad alimentada del reactivo no limitante} - \text{Cantidad teórica (estequiométrica)}}{\text{Cantidad teórica}}\times 100$$

**Cómo identificar el reactivo limitante:** dividir la cantidad alimentada de cada reactivo entre su coeficiente estequiométrico; el que dé el **menor** valor es el limitante.

### 1.3 Grados de libertad con reacción química

$$V = \#\text{ELI} - \#\text{Incógnitas}\,,\qquad \#\text{Incógnitas} = \left[\begin{array}{c}\text{compuestos no definidos}\\\text{en cada corriente}\end{array}\right] + \left[\begin{array}{c}\text{una incógnita por cada}\\\text{conversión desconocida}\end{array}\right]$$

$$\#\text{ELI} = \left[\begin{array}{c}\text{tantos compuestos}\\\text{tenga el sistema}\end{array}\right] + \left[\begin{array}{c}\text{composiciones o cantidades}\\\text{definidas independientes}\end{array}\right] + \left[\begin{array}{c}\text{relaciones}\\\text{particulares}\end{array}\right]$$

Igual convenio de signos que en el balance sin reacción química (Conferencia 5, sección 4.1): $V=0$ → solución única; $V<0$ → faltan datos; $V>0$ → sobran ecuaciones, revisar consistencia.

### 1.4 Particularidades de la combustión

- El **combustible** es siempre el reactivo limitante (habitualmente con 100 % de conversión).
- El **% de exceso** se refiere casi siempre al **aire** (y da el mismo valor numérico que si se refiriera solo al O₂, porque el aire tiene una fracción fija de O₂).
- El **% de completamiento** es el % del combustible que reacciona hasta CO₂ (combustión completa) en vez de CO (incompleta) — un concepto distinto de la conversión.
- Productos típicos: CO₂ y CO (del carbono), H₂O (del hidrógeno + humedad del aire/combustible), O₂ (el exceso) y N₂ (elemento de correlación del aire).

---

## 2. Ejercicio 1 (CP9) — Neutralización de H₃PO₄ con NaOH y secado adiabático

### 2.1 Enunciado completo

$$\text{H}_3\text{PO}_4(1)\ 25\ \tfrac{\text{kmol}}{\text{min}} \longrightarrow \boxed{\text{Reactor}} \xrightarrow{(3)} \boxed{\text{Secado Adiabático}} \longrightarrow (6)$$

con NaOH (2), 25 kmol/min, entrando también al reactor; aire (4), 18 900 m³/min a 40 °C y $\%Y_R=30\%$, entrando al secador; y (5) el aire de salida del secador, a 25 °C. La reacción: $\text{H}_3\text{PO}_4+2\text{NaOH}=\text{Na}_2\text{HPO}_4+2\text{H}_2\text{O}$.

a) Si la conversión en el reactor es 80 %, calcular la composición de la mezcla a la salida del secado.
b) Calcular el % de exceso de H₃PO₄.

### 2.2 Por qué conviene empezar por el reactor

El proceso tiene dos equipos en serie; el reactor es el único donde ocurre la reacción, así que hay que resolverlo primero para obtener la composición de (3), que es precisamente lo que necesita el secador como dato de entrada. **BC = 1 min** (los datos ya vienen "por minuto").

### 2.3 Grados de libertad en el reactor

**Incógnitas:** $F_3$ (flujo total de salida del reactor), $x_{H_3PO_4(3)}$, $x_{NaOH(3)}$, $x_{Na_2HPO_4(3)}$, $x_{H_2O(3)}$ → **5 incógnitas**. La conversión **no** se cuenta como incógnita adicional porque ya es un dato del enunciado (80 %).

**Ecuaciones:** 4 EPB (una por cada compuesto: H₃PO₄, NaOH, Na₂HPO₄, H₂O) + 1 ERC (la de la corriente 3, $\sum x_i=1$) = **5 ecuaciones**.

$$V = 5-5 = 0 \qquad\Rightarrow\qquad \text{tiene solución única}$$

### 2.4 Paso 1 — Identificar el reactivo limitante

Entran 25 kmol/min de H₃PO₄ y 25 kmol/min de NaOH. Según la reacción, se necesitan **2 mol de NaOH por cada mol de H₃PO₄**. Dividiendo cada cantidad alimentada entre su coeficiente estequiométrico:

$$\dfrac{25\ \text{kmol H}_3\text{PO}_4}{1} = 25 \qquad\text{vs.}\qquad \dfrac{25\ \text{kmol NaOH}}{2} = 12.5$$

Como $12.5 < 25$: **el NaOH es el reactivo limitante**; el H₃PO₄ está en exceso (aunque ambos entran en igual cantidad molar, porque la estequiometría no es 1:1 sino 1:2).

### 2.5 Paso 2 — Construir la tabla de balance, componente por componente

**NaOH (reactivo limitante), con conversión 80 % dato del enunciado:**

$$NaOH_{reacc} = 0.80\times 25 = 20\ \text{kmol/min}$$

$$NaOH_{sale} = NaOH_{entra}-NaOH_{reacc} = 25-20 = 5\ \text{kmol/min}$$

**H₃PO₄ (reactivo en exceso).** Por la estequiometría (1 mol H₃PO₄ reacciona por cada 2 mol de NaOH que reaccionan):

$$H_3PO_{4\ reacc} = NaOH_{reacc}\left(\dfrac{1\ \text{H}_3\text{PO}_4}{2\ \text{NaOH}}\right) = 20\left(\dfrac{1}{2}\right) = 10\ \text{kmol/min}$$

$$H_3PO_{4\ sale} = 25-10 = 15\ \text{kmol/min}$$

**Na₂HPO₄ (producto).** Por la estequiometría (1 mol de producto por cada 2 mol de NaOH que reaccionan):

$$Na_2HPO_{4\ forma} = NaOH_{reacc}\left(\dfrac{1\ \text{Na}_2\text{HPO}_4}{2\ \text{NaOH}}\right) = 20\left(\dfrac{1}{2}\right) = 10\ \text{kmol/min} = Na_2HPO_{4\ sale}$$

**H₂O (producto).** Por la estequiometría (2 mol de agua por cada 2 mol de NaOH que reaccionan, es decir, razón 1:1 con el NaOH):

$$H_2O_{forma} = NaOH_{reacc}\left(\dfrac{2\ \text{H}_2\text{O}}{2\ \text{NaOH}}\right) = 20(1) = 20\ \text{kmol/min} = H_2O_{sale}$$

**Tabla completa (kmol/min):**

| Compuesto | Entra | Reacciona | Forma | Sale |
|---|---|---|---|---|
| H₃PO₄ | 25 | 10 | – | 15 |
| NaOH | 25 | 20 | – | 5 |
| H₂O | – | – | 20 | 20 |
| Na₂HPO₄ | – | – | 10 | 10 |

**Flujo total de la corriente 3:** $F_3 = 15+5+20+10 = 50$ kmol/min.

### 2.6 Paso 3 — Agua evaporada en el secador adiabático

**Convertir el flujo de aire de m³/min a kmol/min.** El dato de "0.907 m³/kg" es el **volumen húmedo** del aire de entrada (leído de la carta sicrométrica a 40 °C, $\%Y_R=30\%$):

$$n_{as} = \dfrac{18900\ \text{m}^3/\text{min}}{0.907\ \text{m}^3/\text{kg}} = 20838\ \text{kg/min}$$

Convirtiendo a kmol (masa molar del aire, 29 kg/kmol):

$$n_{as} = 20838\ \text{kg/min}\times\dfrac{1\ \text{kmol}}{29\ \text{kg}} = 718.6\ \text{kmol/min}$$

**Leer las humedades molares en la carta sicrométrica:** a la entrada (40 °C, $\%Y_R=30\%$), $Y_{6,\text{molar}}=0.02$ mol H₂O/mol aire seco; a la salida (25 °C, tras la saturación adiabática), $Y_{5,\text{molar}}=0.014$ mol H₂O/mol aire seco.

**Balance de agua en el secador** (el aire seco no cambia; solo gana la humedad que se evapora de la mezcla sólida, en términos molares, con el factor 29/18 para pasar de "por mol de aire" a "kmol de H₂O" usando las masas molares del aire y del agua dentro de la propia definición dada):

$$H_2O_{evap} = n_{as}\left[(0.02-0.014)\dfrac{29}{18}\right] = 718.6\left[0.006\times 1.6111\right] = 718.6(0.009667) \approx 6.95 \approx 7\ \text{kmol/min}$$

### 2.7 Paso 4 — Composición final de la corriente 6

Como el secador solo retira agua, **H₃PO₄, NaOH y Na₂HPO₄ se conservan** exactamente entre (3) y (6); solo el H₂O cambia (pierde lo que se evapora):

| | (3) kmol/min | (6) kmol/min | $x_i = n_i/n_t \times 100$ |
|---|---|---|---|
| H₃PO₄ | 15 | 15 | $15/43=34.9\%$ |
| NaOH | 5 | 5 | $5/43=11.6\%$ |
| H₂O | 20 | $20-7=13$ | $13/43=30.2\%$ |
| Na₂HPO₄ | 10 | 10 | $10/43=23.3\%$ |
| **Total** | **50** | **43** | **100 %** |

$$\boxed{\text{Composición de (6): } 34.9\%\ \text{H}_3\text{PO}_4,\ 11.6\%\ \text{NaOH},\ 30.2\%\ \text{H}_2\text{O},\ 23.3\%\ \text{Na}_2\text{HPO}_4}$$

### 2.8 Paso 5 — Parte (b): % de exceso de H₃PO₄

**Paso 1 — Calcular el H₃PO₄ teórico (estequiométrico).** Es el que sería exactamente necesario para consumir **todo** el NaOH alimentado (25 kmol/min), sin que sobre ni falte nada de H₃PO₄:

$$H_3PO_{4\ teórico} = 25\ \text{kmol}_{NaOH}\left(\dfrac{1\ \text{H}_3\text{PO}_4}{2\ \text{NaOH}}\right) = 12.5\ \text{kmol/min}$$

**Paso 2 — Aplicar la fórmula de % de exceso:**

$$\%\text{Exceso} = \dfrac{H_3PO_{4\ entra}-H_3PO_{4\ teórico}}{H_3PO_{4\ teórico}}\times 100 = \dfrac{25-12.5}{12.5}\times 100$$

$$\boxed{\%\text{Exceso} = 100\%}$$

**Interpretación:** un 100 % de exceso significa que se alimentó **el doble** de lo estrictamente necesario (25 kmol frente a solo 12.5 kmol requeridos). Esto explica por qué, aunque H₃PO₄ y NaOH entraron en **igual** cantidad molar (25 y 25), el NaOH resultó ser el limitante: la reacción no consume ambos reactivos en proporción 1:1, sino 1:2.

---

## 3. Ejercicio 2 (CP9) — Deshidrogenación catalítica del propano (balance por elementos)

### 3.1 Enunciado

El propileno (C₃H₆) se produce por deshidrogenación catalítica del propano (C₃H₈), pero ocurren también varias reacciones paralelas que producen otros hidrocarburos, además de descomposición de carbono sobre el catalizador. Se alimentan 58.2 kmol/día de C₃H₈ puro; la composición molar de salida es: C₃H₈=45 %, C₃H₆=20 %, C₂H₆=6 %, C₂H₄=1 %, CH₄=3 %, H₂=25 %. Calcular el carbono que se deposita (corriente 3).

$$\text{C}_3\text{H}_8\ (1) \longrightarrow \boxed{\text{Reactor Catalítico}} \longrightarrow \begin{cases}\text{(2) Gases}\\ \text{(3) Carbono}\end{cases}$$

### 3.2 Por qué debe ser un balance por elementos (y no por componente)

El enunciado dice explícitamente que ocurren "varias reacciones paralelas" cuyas estequiometrías individuales **no se conocen todas**. Sin conocer cada reacción por separado, es imposible plantear un balance "reactivo → producto" para cada una (sección 1.1). La única salida es un **balance elemental**: sobre el **Carbono** (C) y el **Hidrógeno** (H), que se conservan sin importar cuántas reacciones distintas hayan ocurrido — cada átomo de C o de H que entra en la molécula de propano tiene que aparecer, tarde o temprano, en alguna de las moléculas de salida (o en el depósito de carbono, para el caso del C).

### 3.3 Grados de libertad

**BC = 1 día.**

- Incógnitas: $F_2$ (flujo de gases de salida) y $F_3$ (carbono depositado) → 2. (La conversión no aparece como incógnita: este es un balance elemental, no de conversión de un reactivo específico.)
- Ecuaciones: 2 EPB, una para el balance de C y otra para el de H.
- $V=2-2=0$: tiene solución.

### 3.4 Paso 1 — Elegir por cuál elemento empezar

**Conviene empezar por el Hidrógeno**, porque el carbono depositado (corriente 3) **no contiene H** — así que esa corriente desaparece del balance de H, dejando una sola incógnita ($F_2$) en una sola ecuación.

### 3.5 Paso 2 — Balance de Hidrógeno

**Contar los átomos de H por mol de cada especie:** C₃H₈ tiene 8 H; C₃H₆ tiene 6 H; C₂H₆ tiene 6 H; C₂H₄ tiene 4 H; CH₄ tiene 4 H; H₂ tiene 2 H.

**H que entra** (todo el H viene del propano puro alimentado):

$$H_{entra} = 58.2\ \text{kmol C}_3\text{H}_8\times\dfrac{8\ \text{átomos H}}{1\ \text{molécula}} = 465.6\ \text{kmol H}$$

**H que sale**, sumando la contribución de cada especie de la corriente 2 (cada una multiplicada por su fracción molar y por sus átomos de H):

$$H_{sale} = F_2\Big[0.45(8)+0.20(6)+0.06(6)+0.01(4)+0.03(4)+0.25(2)\Big]$$

Calculando el corchete término a término: $0.45(8)=3.6$; $0.20(6)=1.2$; $0.06(6)=0.36$; $0.01(4)=0.04$; $0.03(4)=0.12$; $0.25(2)=0.5$. Sumando: $3.6+1.2+0.36+0.04+0.12+0.5=5.82$.

$$H_{sale} = 5.82\,F_2$$

**Igualando** ($H_{entra}=H_{sale}$, porque el H no puede irse a ningún otro lado — el carbono depositado no lo contiene):

$$465.6 = 5.82\,F_2 \qquad\Rightarrow\qquad \boxed{F_2 = \dfrac{465.6}{5.82} = 80\ \text{kmol/día}}$$

### 3.6 Paso 3 — Balance de Carbono

**Átomos de C por mol:** C₃H₈ tiene 3 C; C₃H₆ tiene 3 C; C₂H₆ tiene 2 C; C₂H₄ tiene 2 C; CH₄ tiene 1 C.

**C que entra:**

$$C_{entra} = 58.2(3) = 174.6\ \text{kmol C}$$

**C que sale por la corriente de gases (2)**, con $F_2=80$ kmol/día ya conocido:

$$C_{sale(2)} = 80\Big[0.45(3)+0.20(3)+0.06(2)+0.01(2)+0.03(1)\Big]$$

Calculando el corchete: $0.45(3)=1.35$; $0.20(3)=0.60$; $0.06(2)=0.12$; $0.01(2)=0.02$; $0.03(1)=0.03$. Sumando: $1.35+0.60+0.12+0.02+0.03=2.12$.

$$C_{sale(2)} = 80(2.12) = 169.6\ \text{kmol C}$$

**El carbono restante debe ser el que se depositó** (todo el C que entró y no salió en la corriente de gases tiene que estar en el depósito sólido):

$$\boxed{C_{sale(3)} = C_{entra}-C_{sale(2)} = 174.6-169.6 = 5\ \text{kmol/día}}$$

### 3.7 Por qué este ejemplo es tan importante pedagógicamente

Ilustra exactamente cuándo usar balance por elementos en vez de por componente: siempre que la red de reacciones sea demasiado compleja o desconocida, o involucre subproductos indeseados (como este depósito de carbono, un fenómeno de "coquización" muy común en reactores catalíticos industriales, que reduce la actividad del catalizador con el tiempo) para los que no existe una ecuación estequiométrica única.

---

## 4. Ejercicio (CP10) — Combustión de propano con mezclador y horno

### 4.1 Enunciado completo

Hay un mezclador que enriquece el combustible antes de entrar al horno: la corriente (1), con 72.7 % C₃H₈ / 27.3 % N₂, se mezcla con C₃H₈ puro (corriente 2, 85 kmol/h) para dar la corriente (3), con 89.3 % C₃H₈ / 10.7 % N₂. Esta corriente (3) entra al horno junto con aire húmedo (25 % de exceso, 50 °C, $\%Y_R=75\%$), donde ocurren:

$$\text{C}_3\text{H}_8+5\text{O}_2=3\text{CO}_2+4\text{H}_2\text{O}\qquad(\text{I, combustión completa})$$

$$\text{C}_3\text{H}_8+\tfrac{7}{2}\text{O}_2=3\text{CO}+4\text{H}_2\text{O}\qquad(\text{II, combustión incompleta})$$

Con 100 % de conversión y 90 % de completamiento, calcular: a) el aire teórico; b) la composición molar de los gases de combustión; c) la temperatura de rocío de esos gases.

$$\text{(1) } \{72.7\%\text{C}_3\text{H}_8,\ 27.3\%\text{N}_2\} \to \underbrace{\bullet}_{\text{Mezclador}} \xrightarrow{(3)\ \{89.3\%,10.7\%\}} \boxed{\text{Horno}} \xrightarrow{(5)} \text{Gases de combustión}$$

con (2) $\text{C}_3\text{H}_8$ puro (85 kmol/h) entrando al mezclador, y (4) aire húmedo (25 % exceso) entrando al horno. **BC = 1 h.**

### 4.2 Parte (a), Paso 1 — Resolver el mezclador

**Grados de libertad:** incógnitas $F_1, F_3$ (2); ecuaciones: 2 EPB (C₃H₈, N₂). $V=2-2=0$.

**Balance total:**

$$F_1+F_2=F_3$$

**Balance de N₂** (inerte en el mezclador, no reacciona ahí — la reacción ocurre en el horno):

$$0.273\,F_1 = 0.107\,F_3 \qquad\Rightarrow\qquad F_1 = \dfrac{0.107}{0.273}\,F_3 = 0.392\,F_3$$

**Sustituyendo en el balance total** ($F_2=85$ kmol/h, dato):

$$0.392\,F_3+85=F_3 \qquad\Rightarrow\qquad 85 = F_3(1-0.392) = 0.608\,F_3$$

$$\boxed{F_3 = \dfrac{85}{0.608} = 139.8\ \text{kmol/h}}$$

**Flujo de C₃H₈ en la corriente 3** (dato: composición 89.3 %):

$$\text{C}_3\text{H}_{8(3)} = 139.8(0.893) = 124.8\ \text{kmol/h}$$

### 4.3 Parte (a), Paso 2 — Aire teórico

Con 100 % de conversión, **todo** el C₃H₈ alimentado al horno reacciona. El **aire teórico** se define como el necesario para la combustión **completa** (reacción I, la referencia estándar del término "teórico"), sin importar cuánto realmente se complete o no en la práctica:

$$O_{2\ teórico} = 124.8\ \text{kmol C}_3\text{H}_8\left(\dfrac{5\ \text{O}_2}{1\ \text{C}_3\text{H}_8}\right) = 624\ \text{kmol}$$

$$\boxed{\text{aire teórico} = \dfrac{O_{2\ teórico}}{0.21} = \dfrac{624}{0.21} = 2971.4\ \text{kmol/h}}$$

(se divide entre 0.21 porque el aire es 21 % O₂ en base molar — un dato estándar asumido en todo el curso).

### 4.4 Parte (b), Paso 1 — Cuánto O₂ entra realmente (con el 25 % de exceso)

$$O_{2\ entra} = O_{2\ teórico}\times(1+0.25) = 624(1.25) = 780\ \text{kmol/h}$$

### 4.5 Parte (b), Paso 2 — Repartir la conversión entre las dos reacciones (90 % completamiento)

Del C₃H₈ que reacciona (124.8 kmol, el 100 % de lo alimentado), el 90 % va por la reacción I (combustión completa, produce CO₂) y el 10 % restante va por la reacción II (incompleta, produce CO):

$$\text{C}_3\text{H}_{8\ \text{vía I}} = 124.8(0.90) = 112.32\ \text{kmol}\,,\qquad \text{C}_3\text{H}_{8\ \text{vía II}} = 124.8(0.10) = 12.48\ \text{kmol}$$

**CO₂ formado** (3 mol CO₂ por mol de C₃H₈, según la reacción I):

$$\text{CO}_{2\ forma} = 112.32(3) = 336.96 \approx 337.0\ \text{kmol}$$

**CO formado** (3 mol CO por mol de C₃H₈, según la reacción II):

$$\text{CO}_{forma} = 12.48(3) = 37.44 \approx 37.4\ \text{kmol}$$

**H₂O formada** (4 mol de agua por mol de C₃H₈, **igual en ambas reacciones**, así que se puede calcular directamente sobre el total reaccionado, 124.8 kmol, sin necesidad de separar por vía):

$$\text{H}_2\text{O}_{forma} = 124.8(4) = 499.2\ \text{kmol}$$

**O₂ consumido**, sumando lo que consume cada vía por separado (5 mol O₂/mol C₃H₈ en la reacción I; 3.5 mol O₂/mol C₃H₈ en la reacción II):

$$O_{2\ reacc} = 112.32(5)+12.48(3.5) = 561.6+43.68 = 605.28 \approx 605.3\ \text{kmol}$$

$$O_{2\ sale} = O_{2\ entra}-O_{2\ reacc} = 780-605.3 = 174.7\ \text{kmol}$$

### 4.6 Parte (b), Paso 3 — Nitrógeno (elemento de correlación) y agua del aire húmedo

**N₂ que entra**, sumando el que trae el aire (con razón 79:21 respecto al O₂) y el que ya traía la corriente de combustible (3), con 10.7 % de N₂:

$$N_{2\ entra} = O_{2\ entra}\left(\dfrac{79}{21}\right)+F_3(0.107) = 780(3.7619)+139.8(0.107) = 2934.3+15.0 = 2949.2\ \text{kmol}$$

Como el N₂ **no reacciona** (es inerte), $N_{2\ sale}=N_{2\ entra}=2949.2$ kmol.

**Agua que entra con el aire húmedo.** Con $Y_{50°C,\%Y_R=75\%}=0.063$ kg H₂O/kg aire (leído de la carta sicrométrica) y el factor 29/18 para pasar de base másica a molar:

$$H_2O_{entra} = 0.063\,\dfrac{\text{kg H}_2\text{O}}{\text{kg aire}}\times\dfrac{29\ \text{kmol aire}^{-1}\cdot\text{kg}}{18\ \text{kg H}_2\text{O/kmol}}\times\dfrac{780\ \text{kmol O}_2}{0.21}$$

Más claramente, en tres pasos: primero, moles de aire = $780/0.21=3714.3$ kmol; segundo, $0.063\times(29/18)=0.063\times 1.6111=0.10150$ kmol H₂O/kmol aire; tercero, multiplicar:

$$H_2O_{entra} = 0.10150\times 3714.3 = 377.0\ \text{kmol}$$

$$H_2O_{sale} = H_2O_{entra}+H_2O_{forma} = 377.0+499.2 = 876.2\ \text{kmol}$$

> **Nota de verificación de erratas:** el material fuente imprime, en dos lugares distintos, valores inconsistentes con estos cálculos: el N₂ de la tabla resumen aparece como "2949,7" (debería ser **2949.2**, el mismo valor calculado arriba — N₂ es inerte, entra = sale, y solo con 2949.2 cuadra el total de la corriente 5, verificado en la sección 4.8), y la ecuación de $H_2O_{sale}$ imprime "$337+499.2=876.2$" (con 337 en vez de 377 — un dígito trocado, porque $337+499.2=836.2\neq 876.2$, mientras que $377+499.2=876.2$ sí es exacto). Ambos se corrigen aquí a los valores consistentes: **N₂ = 2949.2 kmol** y **H₂O que entra con el aire = 377.0 kmol**.

### 4.7 Tabla de balance completa (kmol/h)

| Compuesto | Entra | Reacciona | Forma | Sale |
|---|---|---|---|---|
| C₃H₈ | 124.8 | 124.8 | – | – |
| O₂ | 780 | 605.3 | – | 174.7 |
| N₂ | 2949.2 | – | – | 2949.2 |
| H₂O | 377.0 | – | 499.2 | 876.2 |
| CO₂ | – | – | 337.0 | 337.0 |
| CO | – | – | 37.4 | 37.4 |

### 4.8 Composición final de la corriente 5 (gases de combustión)

Sumando todas las salidas: $174.7+2949.2+876.2+337.0+37.4 = 4374.5$ kmol.

| | kmol | % molar |
|---|---|---|
| O₂ | 174.7 | $174.7/4374.5=3.99\%$ |
| N₂ | 2949.2 | $2949.2/4374.5=67.42\%$ |
| H₂O | 876.2 | $876.2/4374.5=20.03\%$ |
| CO₂ | 337.0 | $337.0/4374.5=7.70\%$ |
| CO | 37.4 | $37.4/4374.5=0.86\%$ |
| **Total** | **4374.5** | **100 %** |

$$\boxed{\text{aire teórico}=2971.4\ \text{kmol/h}\,;\quad y_{O_2}=3.99\%,\ y_{N_2}=67.42\%,\ y_{H_2O}=20.03\%,\ y_{CO_2}=7.70\%,\ y_{CO}=0.86\%}$$

### 4.9 Parte (c) — Temperatura de rocío de los gases de combustión

**Paso 1 — Presión parcial actual del agua en la mezcla** (ley de Dalton: presión parcial = fracción molar × presión total):

$$\bar{P}_{H_2O} = P_{total}\times y_{H_2O} = 101.3\ \text{kPa}\times 0.2003 = 20.29\ \text{kPa}$$

**Paso 2 — Convertir a mmHg** (para poder usar las tablas de vapor de agua en esa unidad, convención habitual):

$$\bar{P}_{H_2O} = 20.29\ \text{kPa}\times\dfrac{1\ \text{atm}}{101.3\ \text{kPa}}\times\dfrac{760\ \text{mmHg}}{1\ \text{atm}} = 152.2\ \text{mmHg}$$

**Paso 3 — Buscar en las tablas de vapor de agua (Perry) la temperatura de saturación correspondiente a esta presión** — es decir, la temperatura a la que $P_s=152.2$ mmHg:

$$\boxed{T_{rocío} = 60.5\ °C}$$

**Por qué esto es exactamente "el punto de rocío":** el punto de rocío es la temperatura a la cual, si se enfría la mezcla a presión (y composición) constante, el vapor de agua presente comienza a condensar — porque a esa temperatura, la presión de saturación del agua $P_s(T)$ se iguala exactamente a la presión parcial actual del vapor, $\bar{P}_{H_2O}=20.29$ kPa. Por encima de 60.5 °C, el agua se mantiene completamente como vapor; si la temperatura baja de ese punto, empieza a condensar.

**Aplicación práctica:** este dato es crítico para el diseño de ductos y equipos de recuperación de calor aguas abajo del horno — si la temperatura de las paredes o de los gases baja de 60.5 °C en algún punto, comenzará a condensar agua (potencialmente ácida, si el combustible contiene azufre), lo que puede causar corrosión.

---

## 5. Ejercicio (CP11-12) — Planta de producción de NH₃ con reciclo y purga

### 5.1 Por qué este es el ejercicio de cierre de todo el Tema 3

Combina mezclador, reactor catalítico, separador y una corriente de **purga** (aplicando el mismo esquema de desvío/reciclo del Tema 3, ahora sobre un reciclo real), y exige distinguir con toda claridad entre la **conversión de un solo paso por el reactor** y la **conversión global de todo el proceso**. Es, con diferencia, el ejercicio con más pasos de todo el bloque de balance de masa.

### 5.2 Enunciado

Una alimentación fresca (100 kmol, BC) de 74 % H₂, 24.5 % N₂, 1.2 % CH₄ y 0.3 % Ar (% molares) reacciona catalíticamente: $\text{N}_2(g)+3\text{H}_2(g)=2\text{NH}_3(g)$. La corriente de salida del reactor se recircula. Para evitar que el CH₄ y el Ar (inertes) se acumulen indefinidamente en el lazo de reciclo, se purga parte del gas reciclado. Datos de diseño:

- La alimentación **combinada** al reactor (fresca + reciclo) contiene **18 % de CH₄**.
- En el reactor se convierte el **65 % del N₂** (en un solo paso).
- El N₂ en la purga es el **1.51 %** del N₂ alimentado al proceso (corriente fresca).
- El producto NH₃ puro que sale del separador es **47.81 kmol**.

$$\text{(1) Alimentación fresca}\ 100\ \text{kmol} \to \underbrace{\bullet}_{\text{M (mezclador)}} \xrightarrow{(2)} \boxed{\text{Reactor catalítico}} \xrightarrow{(3)} \boxed{\text{Separador}} \to \begin{cases}\text{(4) NH}_3=47.81\ \text{kmol}\\ \text{(5)} \to \underbrace{\bullet}_{\text{D (divisor)}} \to \begin{cases}\text{(6) Purga}\\ \text{(7) Reciclo} \to \text{regresa a M}\end{cases}\end{cases}$$

### 5.3 Por qué hay que tabular los grados de libertad de TODOS los sistemas antes de empezar

En cada posible subsistema hay corrientes con inertes (CH₄, Ar) de composición o flujo desconocidos; las ecuaciones restrictivas especiales que provienen de sus balances (p. ej., "el CH₄ solo entra por (1) y solo sale por la purga (6), sin cambiar") son indispensables para cerrar el sistema, y no hay una fórmula mecánica que las genere — hay que identificarlas caso por caso, examinando cada corriente. Por eso conviene, **antes de calcular nada**, construir una tabla con los grados de libertad de cada frontera posible:

| | Mezclador | Reactor | Separador | Proceso completo |
|---|---|---|---|---|
| # Incógnitas | 11 | 11 | 12 | 7 |
| # EPB | 5 | 3 | 5 | 5 |
| # ERC | 2 | 2 | 2 | 1 |
| # ERE | 0 | 0 | 0 | 1 |
| **V** | **−4** | **−6** | **−5** | **0** |

**Solo el "Proceso completo" tiene $V=0$**: es el único punto de partida posible.

### 5.4 Paso 1 — Balance en el proceso completo

**Restrictivas de composición de los inertes** (CH₄ y Ar entran solo por (1) y salen solo por la purga (6); ni el mezclador ni el reactor ni el separador los eliminan ni los transforman, así que su cantidad total se conserva entre la entrada fresca y la purga):

$$\text{CH}_{4(1)} = \text{CH}_{4(6)} = 0.012(100) = 1.2\ \text{kmol}$$

$$A_{(1)} = A_{(6)} = 0.003(100) = 0.3\ \text{kmol}$$

**Restrictiva especial del N₂ en la purga** (dato de diseño):

$$N_{2(6)} = 0.0151(24.5) = 0.37\ \text{kmol}$$

**Paso 1a — Identificar el reactivo limitante.** Para 24.5 kmol de N₂ se necesitarían, según la estequiometría (1:3), $24.5\times 3=73.5$ kmol de H₂; hay 74 kmol disponibles, apenas por encima. Como $24.5 < 74/3=24.67$ (equivalentemente, hace falta comparar $24.5/1$ contra $74/3=24.67$): **el N₂ es el reactivo limitante**, el H₂ está en un exceso muy pequeño.

**Paso 1b — Construir la tabla de balance del proceso completo.**

$$N_{2\ reacc} = N_{2\ entra}-N_{2\ sale} = 24.5-0.37 = 24.13\ \text{kmol}$$

$$H_{2\ reacc} = N_{2\ reacc}\left(\dfrac{3\ \text{H}_2}{1\ \text{N}_2}\right) = 24.13(3) = 72.39\ \text{kmol}$$

$$NH_{3\ forma} = N_{2\ reacc}\left(\dfrac{2\ \text{NH}_3}{1\ \text{N}_2}\right) = 24.13(2) = 48.26\ \text{kmol}$$

$$H_{2\ sale} = 74-72.39 = 1.61\ \text{kmol}$$

**Paso 1c — Repartir el NH₃ formado entre el producto (4) y lo que arrastra la purga.** El NH₃ formado en total (48.26 kmol) se reparte entre lo que sale purificado por (4) —dato: 47.81 kmol— y lo que se pierde en la purga:

$$NH_{3\ sale(6)} = NH_{3\ forma}-NH_{3\ sale(4)} = 48.26-47.81 = 0.45\ \text{kmol}$$

**Composición de la corriente de purga (6):**

| | kmol | % |
|---|---|---|
| H₂ | 1.61 | $1.61/3.93=40.97\%$ |
| N₂ | 0.37 | $0.37/3.93=9.41\%$ |
| NH₃ | 0.45 | $0.45/3.93=11.45\%$ |
| Ar | 0.30 | $0.30/3.93=7.63\%$ |
| CH₄ | 1.20 | $1.20/3.93=30.54\%$ |
| **Total F₆** | **3.93** | **100 %** |

**Conversión global del proceso** (tomando como frontera todo el proceso, del N₂ fresco al N₂ que sale por la purga — la única "salida" de N₂ sin reaccionar):

$$\%\text{Conversión}_{proceso} = \dfrac{N_{2\ reacc}}{N_{2\ entra}}\times 100 = \dfrac{24.13}{24.5}\times 100 = 98.49\%$$

**Por qué las corrientes (5), (6) y (7) comparten la misma composición:** el punto de división D es solo un desvío mecánico (Conferencia 5, sección 6.1) — divide un mismo flujo en dos partes sin cambiar su composición, exactamente igual que el punto de desvío del Ejercicio 2 de la sección 3 del documento de CP5-6-7.

### 5.5 Paso 2 — Balance en el mezclador

Con las composiciones de (6)=(7) ya conocidas, se reanaliza la tabla de grados de libertad: ahora el **Mezclador** da $V=0$ (Reactor sigue negativo, Separador también).

**Balance de CH₄** (el único componente cuya composición de entrada al reactor, 18 %, se conoce como dato de diseño):

$$F_1\,x_{CH_4(1)}+F_7\,x_{CH_4(7)} = F_2\,x_{CH_4(2)}$$

$$100(0.012)+F_7(0.3054) = F_2(0.18)$$

$$0.3054\,F_7 = 0.18\,F_2-1.2\qquad(1)$$

**Balance total:**

$$F_1+F_7=F_2 \qquad\Rightarrow\qquad F_7=F_2-100\qquad(2)$$

**Sustituyendo (2) en (1):**

$$0.3054(F_2-100) = 0.18\,F_2-1.2$$

$$0.3054\,F_2-30.54 = 0.18\,F_2-1.2$$

$$0.3054\,F_2-0.18\,F_2 = 30.54-1.2$$

$$0.1254\,F_2 = 29.34 \qquad\Rightarrow\qquad \boxed{F_2 = \dfrac{29.34}{0.1254} = 234\ \text{kmol}}$$

$$F_7 = 234-100 = 134\ \text{kmol}$$

**Composición de la corriente 2**, balanceando cada especie (ejemplo con H₂; el mismo patrón se repite para N₂, NH₃ y Ar):

$$x_{H_2(2)} = \dfrac{F_1\,x_{H_2(1)}+F_7\,x_{H_2(7)}}{F_2} = \dfrac{100(0.74)+134(0.4097)}{234} = \dfrac{74+54.90}{234} = \dfrac{128.90}{234} = 0.5509$$

$$x_{N_2(2)} = \dfrac{100(0.245)+134(0.0941)}{234} = \dfrac{24.5+12.61}{234} = 0.1586$$

$$x_{NH_3(2)} = \dfrac{134(0.1145)}{234} = \dfrac{15.34}{234} = 0.0656\qquad(\text{no entra NH}_3\text{ por (1), la alimentación fresca})$$

$$x_{A(2)} = \dfrac{100(0.003)+134(0.0763)}{234} = \dfrac{0.3+10.22}{234} = 0.0449$$

| Corriente 2 | % |
|---|---|
| H₂ | 55.09 |
| N₂ | 15.86 |
| NH₃ | 6.56 |
| Ar | 4.49 |
| CH₄ | 18.00 |
| **F₂ = 234 kmol** | |

**Balance total en el divisor D**, ahora que $F_7$ ya se conoce:

$$F_5 = F_6+F_7 = 3.93+134 = 137.93\ \text{kmol}\qquad(\text{misma composición que (6) y (7)})$$

### 5.6 Paso 3 — Balance en el separador

Con (2) resuelto, se reanaliza otra vez la tabla: ahora el **Separador** da $V=0$. Es una separación pura, sin reacción química (mismo tipo de balance de la Conferencia 5).

**Balance total:**

$$F_3 = F_4+F_5 = 47.81+137.93 = 185.74\ \text{kmol}$$

**Composición de la corriente 3**, balanceando cada especie (para el H₂, N₂, Ar, la corriente 4 no aporta nada porque es NH₃ puro; para el NH₃, sí hay que sumar el aporte de (4)):

$$x_{H_2(3)} = \dfrac{F_5\,x_{H_2(5)}}{F_3} = \dfrac{137.93(0.4097)}{185.74} = \dfrac{56.51}{185.74} = 0.3042$$

$$x_{N_2(3)} = \dfrac{137.93(0.0941)}{185.74} = \dfrac{12.98}{185.74} = 0.0699$$

$$x_{NH_3(3)} = \dfrac{F_5\,x_{NH_3(5)}+F_4}{F_3} = \dfrac{137.93(0.1145)+47.81}{185.74} = \dfrac{15.79+47.81}{185.74} = \dfrac{63.60}{185.74} = 0.3424$$

$$x_{CH_4(3)} = \dfrac{137.93(0.3054)}{185.74} = \dfrac{42.13}{185.74} = 0.2268$$

$$x_{A(3)} = \dfrac{137.93(0.0763)}{185.74} = \dfrac{10.53}{185.74} = 0.0567$$

| Corriente 3 | % |
|---|---|
| H₂ | 30.42 |
| N₂ | 6.99 |
| NH₃ | 34.24 |
| Ar | 5.67 |
| CH₄ | 22.68 |
| **F₃ = 185.74 kmol** | |

### 5.7 Paso 4 — Cerrar el reactor por diferencia, y verificar la conversión de un solo paso

Con (2) y (3) ya completamente conocidos, el reactor se cierra **por diferencia**, sin plantear ningún sistema de ecuaciones nuevo:

$$H_{2(2)} = F_2\,x_{H_2(2)} = 234(0.5509) = 128.91\ \text{kmol}\,,\qquad H_{2(3)} = F_3\,x_{H_2(3)} = 185.74(0.3042) = 56.5\ \text{kmol}$$

$$N_{2(2)} = 234(0.1586) = 37.11\ \text{kmol}\,,\qquad N_{2(3)} = 185.74(0.0699) = 12.98\ \text{kmol}$$

$$NH_{3(2)} = 234(0.0656) = 15.35\ \text{kmol}\,,\qquad NH_{3(3)} = 185.74(0.3424) = 63.6\ \text{kmol}$$

**Tabla de balance del reactor (kmol):**

| Compuesto | Entra (2) | Reacciona | Forma | Sale (3) |
|---|---|---|---|---|
| H₂ | 128.91 | $128.91-56.5=72.41$ | – | 56.5 |
| N₂ | 37.11 | $37.11-12.98=24.13$ | – | 12.98 |
| NH₃ | 15.35 | – | $63.6-15.35=48.25$ | 63.6 |
| CH₄ | 42.12 | – | – | 42.12 |
| Ar | 10.51 | – | – | 10.51 |

**Conversión de un solo paso por el reactor:**

$$\%\text{Conversión}_{\text{un paso}} = \dfrac{N_{2\ reacc}}{N_{2\ entra(2)}}\times 100 = \dfrac{24.13}{37.11}\times 100 = 65.0\%$$

**¡Este valor coincide exactamente con el 65 % dado en el enunciado!** Y es una coincidencia que vale la pena remarcar: el 65 % de conversión por paso **no se usó en ningún momento como ecuación** durante toda la solución (el sistema se cerró usando solo las restricciones de composición de CH₄, Ar y N₂-en-la-purga). Que se recupere exactamente al final, de forma completamente independiente, es la **comprobación numérica** (paso e del programa de análisis) de que toda la cadena de cálculo — mezclador, separador, y el cierre del reactor por diferencia — es internamente consistente.

### 5.8 Paso 5 — % de exceso de H₂

$$H_{2\ teórico} = N_{2(2)}\left(\dfrac{3\ \text{H}_2}{1\ \text{N}_2}\right) = 37.11(3) = 111.33\ \text{kmol}$$

$$\%\text{Exceso} = \dfrac{H_{2\ entra}-H_{2\ teórico}}{H_{2\ teórico}}\times 100 = \dfrac{128.91-111.33}{111.33}\times 100 = \dfrac{17.58}{111.33}\times 100$$

$$\boxed{\%\text{Exceso de H}_2 = 15.8\%}$$

### 5.9 La distinción central del ejercicio: conversión de un paso vs. conversión global

$$\%\text{Conversión (un solo paso por el reactor)} = 65.0\% \qquad\text{vs.}\qquad \%\text{Conversión (proceso completo, con reciclo)} = 98.49\%$$

**Por qué son tan distintas:** en cada paso por el reactor, solo el 65 % del N₂ que entra reacciona; el 35 % restante sale sin reaccionar. Pero gracias al **reciclo**, ese N₂ no reaccionado **no se pierde** — vuelve al mezclador y tiene una nueva oportunidad de reaccionar en el siguiente paso por el reactor, y así sucesivamente. Solo una pequeña fracción (fijada por diseño en 1.51 % del N₂ fresco) se pierde definitivamente por la purga, necesaria para evitar que el CH₄ y el Ar —que nunca reaccionan— se acumulen indefinidamente en el lazo cerrado. El resultado neto es que, aunque cada paso individual por el reactor sea poco eficiente (65 %), el proceso completo aprovecha casi todo el N₂ fresco alimentado (98.49 %).

**Relevancia industrial:** esta es exactamente la lógica que hace viables económicamente los procesos reales de síntesis de amoníaco (proceso Haber-Bosch), donde la conversión de equilibrio por paso —limitada por la termodinámica de la reacción a las condiciones de operación— ronda apenas el 15-20 %, y es precisamente el reciclo con purga el que permite alcanzar conversiones globales cercanas al 98-99 %, como en este ejercicio.

### 5.10 Trabajo independiente propuesto por la clase práctica

**"Comprobar que la composición de la corriente (3) se puede evaluar también resolviendo primero el balance en el punto divisor y después en el separador."** Esto es exactamente lo que ya se hizo, en ese mismo orden, en las secciones 5.5 (balance en el divisor D, para obtener $F_5$) y 5.6 (balance en el separador, para obtener la composición de (3)) — así que esta comprobación ya está incorporada en la secuencia de cálculo presentada.

**"Verificar el balance total en unidades másicas en el reactor."** Se deja indicado el método: multiplicar cada flujo molar de la tabla de la sección 5.7 por la masa molar correspondiente ($MM_{H_2}=2$, $MM_{N_2}=28$, $MM_{NH_3}=17$, $MM_{CH_4}=16$, $MM_{Ar}=40$ g/mol) y comprobar que la masa total que entra en (2) es igual a la masa total que sale en (3) — a diferencia de los moles totales (que sí cambian, porque $1$ mol de N₂ + $3$ moles de H₂ dan solo $2$ moles de NH₃), la **masa** total se conserva siempre en una reacción química, como se estableció en la Conferencia 6, sección 2.

---

## 6. Conclusiones de este bloque de clases prácticas

1. **El balance por elementos es indispensable cuando la red de reacciones no se conoce completamente** (Ejercicio 2 de la CP9): basta con elegir el elemento cuyo balance "elimina" alguna corriente desconocida (aquí, empezar por H porque el carbono depositado no contiene H) para simplificar enormemente la solución.
2. **En combustión, el % de exceso casi siempre se da en términos de aire**, y el % de completamiento es un concepto distinto de la conversión: mide qué fracción del combustible que sí reaccionó llegó hasta CO₂ en vez de quedarse en CO.
3. **El punto de rocío de los gases de combustión** es un dato de diseño crítico (corrosión por condensados) y se calcula exactamente igual que en el Tema 2: buscando la temperatura de saturación correspondiente a la presión parcial actual del vapor de agua.
4. **La distinción entre conversión de un solo paso y conversión global de un proceso con reciclo** (sección 5.9) es, posiblemente, la lección más importante de todo el Tema 3: un reactor con baja conversión por paso puede lograr una conversión global casi total gracias al reciclo, y esta es la base económica de buena parte de la industria química de síntesis.
5. **Tabular los grados de libertad de todos los sistemas posibles antes de empezar a calcular** (secciones 5.3, y repetido después de cada paso en las secciones 5.5-5.6) es la única forma sistemática de saber por dónde empezar en un proceso con muchos equipos interconectados — exactamente el mismo patrón usado en el Ejercicio 4 (café instantáneo) del documento de las Clases Prácticas 5, 6 y 7.

---

## Referencias / fuentes usadas en este documento

- [PIQ1 Clase practica 9 Reactor secador Reactor catalitico.pdf](PIQ1%20Clase%20practica%209%20Reactor%20secador%20Reactor%20catalitico.pdf) — Ejercicios 1 y 2 (secciones 2 y 3).
- [PIQ1 Clase practica 10 Reacciones de combustion Mezclador horno.pdf](PIQ1%20Clase%20practica%2010%20Reacciones%20de%20combustion%20Mezclador%20horno.pdf) — Ejercicio de la sección 4.
- [PIQ1 Clases practicas 11 y 12 Planta de produccion de amoniaco.pdf](PIQ1%20Clases%20practicas%2011%20y%2012%20Planta%20de%20produccion%20de%20amoniaco.pdf) — Ejercicio integrador de la sección 5.
- [Conferencia 6 - Balance de Masa con Reaccion Quimica.md](Conferencia%206%20-%20Balance%20de%20Masa%20con%20Reaccion%20Quimica.md) — teoría y demostraciones de las fórmulas usadas aquí.
- [../TEMA 2/Conferencia 4 - Mediciones Termometricas, Carta Sicrometrica y Procesos.md](../TEMA%202/Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md) — carta sicrométrica y punto de rocío, usados en las secciones 2 y 4.
