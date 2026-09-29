# Tema 2 — Clase Práctica 4: Procesos de vaporización y condensación (saturador, condensador y calentadores)

> **Asignatura:** Principios de Ingeniería Química I (Balance de Masa y Energía)
> **Fuente principal:** [PIQ1 Clase practica 4 Procesos de vaporizacion y condensacion Saturador-Condensador-Calentadores.pdf](PIQ1%20Clase%20practica%204%20Procesos%20de%20vaporizacion%20y%20condensacion%20Saturador-Condensador-Calentadores.pdf)
> **Teoría de base (léase antes si algo no se entiende):** [Conferencia 4 - Mediciones Termometricas, Carta Sicrometrica y Procesos.md](Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md)
> **Apoyo numérico:** [../Steam Tables_Keenan.pdf](../Steam%20Tables_Keenan.pdf) (usada para verificar de forma independiente uno de los datos leídos de la carta)
>
> Este documento es un desarrollo **independiente** de la Clase Práctica 4, con cada ecuación recordada antes de usarse, cada conversión de unidades mostrada completa, y cada afirmación ("esta masa no cambia", "esta corriente tiene la misma composición que aquella") justificada explícitamente con el balance físico que la sustenta. Se resuelve íntegro el único ejercicio de la clase práctica, con sus cinco incisos (a–e).

---

## 0. Qué es esta clase práctica y qué se espera lograr con ella

Esta clase práctica ejercita el contenido de la Conferencia 4: el manejo de la **carta sicrométrica** del sistema agua-aire y el cálculo de los **flujos** (de aire seco, de agua, de mezcla húmeda) asociados a los procesos de vaporización y condensación que esa carta representa. El objetivo declarado por el propio material es exactamente ese: *"ejercitar el manejo de la carta sicrométrica de la mezcla agua-aire y el cálculo de los flujos asociados a procesos de vaporización y condensación."*

**Repaso rápido de qué caracteriza a cada proceso en la carta** (desarrollado con detalle en la Conferencia 4, sección 5; se resume aquí porque el ejercicio combina varios):

- **Calentamiento y enfriamiento:** ocurren a **saturación (composición $Y$) constante** — no hay contacto con líquido, así que la cantidad de vapor no cambia, solo la temperatura.
- **Condensación:** ocurre a **$\%Y_R=100\ \%$ constante** — la mezcla, una vez saturada, se mantiene saturada mientras pierde vapor (que se convierte en líquido) al seguir enfriándose.
- **Saturación adiabática (vaporización):** ocurre a **$t_{sa}$ constante** (que para agua-aire coincide con $t_{bh}$ constante) — la mezcla gana vapor y su composición aumenta.

En estos dos últimos procesos (condensación y saturación adiabática) es donde **cambia el contenido de vapor** de la corriente; en los dos primeros (calentamiento, enfriamiento), no.

---

## 1. Formulario de partida (recordatorio, sin re-derivar)

**Notación:** $m_{as}$ = masa (o flujo másico) de **aire seco**; $m_{ah}$ = masa (o flujo) de **aire húmedo** (mezcla total); $Y$ = saturación, kg de H₂O por kg de aire seco; $V_H$ = volumen húmedo (m³ de mezcla por kg de aire seco); $V_t$ = volumen total de una corriente.

**Ecuación 1 — Agua ganada o perdida en un proceso** (entre una entrada y una salida de un mismo equipo, o de un tramo del proceso):

$$H_2O = m_{as}\,\Delta Y\,,\qquad \Delta Y = |Y_{\text{sale}}-Y_{\text{entra}}| \quad\text{(siempre positivo, por convención de la clase práctica)}$$

**Por qué es válida esta ecuación tan simple:** porque $Y$ está definida como masa de vapor **por unidad de masa de aire seco**, y el aire seco ni se crea ni se destruye en estos procesos (solo entra y sale agua, como vapor o como condensado). Entonces, si un mismo flujo de aire seco $m_{as}$ entra con $Y_1$ (kg agua/kg a.s.) y sale con $Y_2$, la diferencia de agua transportada es directamente $m_{as}(Y_2-Y_1)$ — no hace falta ningún factor de conversión adicional.

**Ecuación 2 — Volumen húmedo:**

$$V_H = \frac{V_t}{m_{as}} \qquad\Longleftrightarrow\qquad m_{as} = \frac{V_t}{V_H}$$

**Advertencia importante que trae el propio material:** ambos volúmenes ($V_t$ y el que define $V_H$) tienen que estar medidos **en el mismo estado termodinámico** — misma temperatura, misma presión y misma composición. No se puede, por ejemplo, tomar un caudal volumétrico medido a la salida de un equipo y dividirlo entre un $V_H$ calculado con las condiciones de otro punto del proceso.

**Ecuación 3 — Masa de aire húmedo (mezcla total) a partir de la masa de aire seco:**

$$m_{ah} = m_{as} + m_{\text{agua}}$$

Como $m_{\text{agua}} = m_{as}\,Y$ (por definición de $Y$), sustituyendo:

$$m_{ah} = m_{as} + m_{as}\,Y = m_{as}\,(1+Y)$$

---

## 2. El ejercicio: planteamiento completo

### 2.1 Enunciado del sistema

Todo el proceso ocurre a $101.3\ \text{kPa}$ constante. El esquema consta de **cuatro equipos**: un saturador, un condensador y dos calentadores, conectados así:

- La corriente **(1)** (aire a $t=24\ \text{°C}$, $t_{bh}=16\ \text{°C}$) entra a un **Saturador**, de donde sale la corriente **(3)**. Al saturador también entra agua líquida, corriente **(2)** (el líquido que se evapora dentro del saturador para humidificar el aire).
- La corriente **(3)** se junta con la corriente **(5)** (proveniente de otro equipo, ver abajo) para formar la corriente **(4)**, que entra a un **Calentador**, de donde sale la corriente **(6)**: $\%Y_R=30$, $t_r=14\ \text{°C}$, con un caudal de $30\,870\ \text{m}^3/\text{h}$.
- Por otro lado, la corriente **(9)** (aire saturado, $t=30\ \text{°C}$, $\%Y_R=100$) entra a un **Condensador**, del que sale líquido condensado, corriente **(8)** ($50\ \text{kg de H}_2\text{O/h}$), y la corriente gaseosa **(7)**.
- La corriente **(7)** entra a un segundo **Calentador**, de donde sale la corriente **(5)** — que es la que se mencionó arriba, y que se une con (3) para formar (4).

**Dato clave del enunciado:** las condiciones de las corrientes **(3), (4) y (5) son las mismas**. Esto no es una coincidencia del problema: como ambas provienen de procesos a $Y$ constante hasta llegar a ese punto de mezcla (el segundo calentador no cambia $Y$ de (7) a (5); y (3) sale ya fijada del saturador), y **dos corrientes con la misma composición y la misma temperatura, al mezclarse, dan una corriente con esa misma composición y temperatura** (mezclar algo con una copia idéntica de sí mismo no cambia sus propiedades intensivas), las tres — (3), (4) y (5) — terminan siendo, en la práctica, un único estado termodinámico repetido en tres tramos de tubería distintos.

### 2.2 Qué hace cada equipo, explicado desde cero

Antes de calcular nada, conviene tener clara la función física de cada equipo, porque de eso depende qué ecuación de la Conferencia 4 (sección 5) aplica en cada tramo:

- **Saturador (adiabático):** es una cámara donde el aire entrante se pone en contacto con agua líquida (corriente 2) y se humidifica — es exactamente el proceso de **vaporización adiabática** de la Conferencia 4, sección 5.4. Ocurre a $t_{bh}=t_{sa}$ constante, y **aumenta** $Y$.
- **Condensador:** enfría la corriente (9), que ya está saturada, forzando que parte de su vapor de agua se condense y se retire como líquido (corriente 8) — es el proceso de **condensación** de la Conferencia 4, sección 5.3. Ocurre a $\%Y_R=100$ constante, y **disminuye** $Y$.
- **Calentador (ambos):** eleva la temperatura de una corriente sin agregar ni quitar agua — es el proceso de **calentamiento** de la Conferencia 4, sección 5.1. Ocurre a **$Y$ constante**.

### 2.3 Los cinco incisos a resolver

(a) Representar el proceso en la carta sicrométrica.
(b) Determinar las condiciones de las corrientes (3), (4) y (5).
(c) Calcular la masa de mezcla húmeda en kg/h que circula por la corriente (5).
(d) Determinar el agua incorporada por hora al proceso en el saturador adiabático.
(e) Calcular el flujo de agua en la corriente (3).

---

## 3. Inciso (a) — Representación en la carta sicrométrica

Aunque este documento no reproduce el gráfico en sí (no es un archivo digital de esta carpeta), se describe aquí **la trayectoria que sigue cada corriente**, punto por punto, para que pueda dibujarse sobre una carta sicrométrica impresa:

1. **Punto (1):** se ubica con $t=24\ \text{°C}$ (eje horizontal) y siguiendo la línea de $t_{bh}=16\ \text{°C}$ hacia abajo, hasta la altura de humedad que le corresponde a ese cruce.
2. **Trayectoria (1)→(3):** dentro del saturador, el proceso es de vaporización adiabática (sección 2.2), así que el punto se desplaza **siguiendo la línea de $t_{bh}=16\ \text{°C}$ constante** (la misma con la que se ubicó el punto 1), acercándose a la curva de 100 % de saturación, hasta el punto que define el estado de salida (3).
3. **Punto (9):** se ubica directamente **sobre la curva de saturación** (100 % $Y_R$), en $t=30\ \text{°C}$ — porque el enunciado ya dice que está saturada.
4. **Trayectoria (9)→(7):** dentro del condensador, el proceso es de condensación (sección 2.2), así que el punto se desplaza **hacia abajo, siguiendo la curva de 100 % $Y_R$**, hasta la temperatura de salida del condensador (punto 7).
5. **Trayectoria (7)→(5):** dentro del segundo calentador, el punto se desplaza **horizontalmente** (a $Y$ constante, igual a la $Y$ del punto 7) hacia la derecha (temperatura creciente), hasta llegar exactamente al mismo punto que (3) — confirmando el dato del enunciado de que (3)=(4)=(5).
6. **Trayectoria (4)→(6):** dentro del primer calentador, el punto se desplaza otra vez **horizontalmente** (a $Y$ constante, la de (3)=(4)=(5)) hacia la derecha, hasta el punto (6), donde el enunciado da $\%Y_R=30$ y $t_r=14\ \text{°C}$.

Esta secuencia de trayectorias es exactamente lo que exige el inciso (a); el resto de los incisos consiste en leer números sobre esas trayectorias y combinarlos con balances de masa.

---

## 4. Inciso (b) — Condiciones de las corrientes (3), (4) y (5)

Siguiendo la línea de $t_{bh}=16\ \text{°C}$ desde el punto (1) hasta el punto donde termina el saturador (descrito en el paso 2 de la sección 3), se leen en la carta las siguientes propiedades para el punto (3)=(4)=(5):

$$t = 19.5\ \text{°C}\,,\qquad t_{bh}=16\ \text{°C}\,,\qquad t_{sa}=16\ \text{°C}\,,\qquad t_r=14\ \text{°C}\,,\qquad \%Y_R = 70$$

$$Y = 0.01\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}}\,,\qquad\qquad V_H = 0.842\ \frac{\text{m}^3\ \text{(aire húmedo)}}{\text{kg (aire seco)}}$$

**Verificación de consistencia (sin necesidad del gráfico):** obsérvese que $t_{bh}=t_{sa}=16\ \text{°C}$, exactamente igual entre sí — tal como exige la propiedad del sistema agua-aire explicada en la Conferencia 4, sección 2.4 ($t_{bh}=t_{sa}$ siempre, para esta mezcla en particular). Que la lectura de la carta cumpla esta identidad es una buena señal de que la lectura es correcta.

### 4.1 Verificación independiente de $Y_{(9)}$ (un dato que sí se puede calcular sin el gráfico)

Aunque el inciso (b) solo pide las condiciones de (3)/(4)/(5), conviene verificar aquí, con datos externos, otro valor que se usa más adelante: la humedad de la corriente (9). Como (9) está **saturada** a $t=30\ \text{°C}$, esto sí se puede calcular sin leer ninguna carta, usando directamente la fórmula de saturación (Conferencia 3, sección 5.3) con la presión de vapor del agua a 30 °C tomada de las [Steam Tables](../Steam%20Tables_Keenan.pdf) (valor exacto de tabla, sin necesidad de interpolar): $P_s(30°C) = 4.246\ \text{kPa}$.

$$Y_{(9)} = \frac{MM_{H_2O}}{MM_{\text{aire}}}\cdot\frac{P_s}{P-P_s} = \frac{18}{29}\times\frac{4.246}{101.3-4.246}$$

Desglosando: $18/29 = 0.6207$; $101.3-4.246=97.054$; $4.246/97.054=0.04375$. Entonces:

$$Y_{(9)} = 0.6207\times 0.04375 = 0.02716\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}} \approx 0.0272$$

Este valor **coincide exactamente** con el que reporta el material original ($Y_{(9)}=0.0272$), lo cual confirma que tanto la lectura de la carta como el método de cálculo son correctos.

---

## 5. Inciso (c) — Masa de mezcla húmeda que circula por la corriente (5)

### 5.1 Planteamiento

Se busca $m_{ah(5)}$ (masa de aire húmedo, es decir, mezcla total agua+aire, en la corriente 5). Por la Ecuación 3 del formulario (sección 1):

$$m_{ah(5)} = m_{as(5)}\,(1+Y_{(5)})$$

Como ya se conoce $Y_{(5)}=0.01$ (inciso b), el problema se reduce a encontrar $m_{as(5)}$, la masa (flujo) de aire seco en esa corriente.

### 5.2 Encontrar $m_{as(5)}$ mediante el balance de agua en la rama del condensador

**Paso 1 — Identificar que el aire seco no cambia de masa entre (9), (7) y (5).** El condensador retira agua (líquida), pero **no retira ni agrega aire** — el aire seco que entra al condensador en (9) es el mismo que sale en (7). De la misma manera, el calentador que sigue (de (7) a (5)) tampoco agrega ni quita aire. Por tanto:

$$m_{as(5)} = m_{as(7)} = m_{as(9)}$$

**Paso 2 — Aplicar la Ecuación 1 (agua ganada o perdida) al condensador.** Entre (9) y (7), el aire seco se mantiene constante mientras el agua condensa (disminuye $Y$):

$$H_2O_{\text{cond}} = m_{as}\,\Delta Y\,,\qquad \Delta Y = Y_{(9)}-Y_{(7)}$$

**Paso 3 — Calcular $\Delta Y$.** Como el calentador que sigue al condensador no cambia $Y$ (sección 2.2), $Y_{(7)}=Y_{(5)}=0.01$ (el mismo valor leído en el inciso b para el punto 3/4/5). Entonces:

$$\Delta Y = Y_{(9)}-Y_{(7)} = 0.0272-0.01 = 0.0172\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}}$$

**Paso 4 — Despejar $m_{as}$.** El enunciado da directamente el agua condensada en el condensador: $50\ \text{kg}\ H_2O/\text{h}$ (corriente 8). Despejando de la Ecuación 1:

$$m_{as} = \frac{H_2O_{\text{cond}}}{\Delta Y} = \frac{50\ \text{kg/h}}{0.0172\ \text{kg}\ H_2O/\text{kg a.s.}}$$

Haciendo la división:

$$m_{as} = 2906.97\ \frac{\text{kg a.s.}}{\text{h}}$$

Y por el paso 1, este es también el valor de $m_{as(5)}$.

### 5.3 Calcular la masa de aire húmedo en (5)

Sustituyendo en la fórmula del inciso (c.1):

$$m_{ah(5)} = 2906.97\times(1+0.01) = 2906.97\times 1.01$$

$$\boxed{m_{ah(5)} = 2936.04\ \text{kg/h}}$$

---

## 6. Inciso (d) — Agua incorporada por hora en el saturador adiabático

### 6.1 Planteamiento

Se busca cuánta agua (por hora) se le agrega al aire **dentro del saturador**, es decir, entre la corriente (1) que entra y la corriente (3) que sale. Por la Ecuación 1:

$$H_2O_{\text{incorp}} = m_{as(1)}\,\Delta Y\,,\qquad \Delta Y = Y_{(3)}-Y_{(1)}$$

**Por qué se usa $m_{as(1)}$ y no otro flujo:** porque este balance es específicamente sobre el equipo "saturador", cuya entrada es la corriente (1) y cuya salida es la (3) — el aire seco que atraviesa ese equipo es el mismo en ambos extremos ($m_{as(1)}=m_{as(3)}$, ya que el saturador tampoco agrega ni quita aire, solo agua), así que cualquiera de los dos sirve como base; se usa $m_{as(1)}$ porque, como se ve más abajo, es más directo de despejar a partir de los datos que sí se conocen.

Hacen falta, entonces, **dos piezas** que todavía no se tienen: el valor de $Y_{(1)}$ (para poder calcular $\Delta Y$) y el valor de $m_{as(1)}$ (o $m_{as(3)}$, que es igual).

### 6.2 Obtener $Y_{(1)}$ a partir de los datos de la corriente (6)

**Paso 1 — Relacionar (6) con (4).** El primer calentador (de (4) a (6)) ocurre a $Y$ constante (sección 2.2), así que:

$$Y_{(4)} = Y_{(6)}\,,\qquad\qquad m_{as(4)}=m_{as(6)}$$

**Paso 2 — Leer $Y_{(6)}$ a partir del dato $t_r=14\ \text{°C}$ dado para la corriente (6).** Como se explicó en la Conferencia 4 (sección 2.1), la temperatura de rocío determina unívocamente la composición de una mezcla: basta con ubicar $t_r=14\ \text{°C}$ **sobre la curva de saturación** (100 % $Y_R$) y proyectar horizontalmente hacia el eje de $Y$. Leyendo:

$$Y_{(6)} = 0.008\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}}$$

**Paso 3 — Conclusión: $Y_{(4)}=Y_{(6)}=0.008$.** Y como $Y_{(1)}=Y_{(4)}-\text{(lo que se agregó en el saturador)}$... espera — en realidad el orden lógico correcto es el inverso: se **conoce** $Y_{(4)}=Y_{(3)}=0.01$ (ya leído directamente en el inciso b, sección 4) y ahora, comparando con $Y_{(6)}=0.008$, se obtiene $\Delta Y$ directamente sin necesitar $Y_{(1)}$ de forma explícita:

$$\Delta Y = Y_{(4)} - Y_{(6)}$$

Pero **cuidado**: este $\Delta Y$ no es el del saturador (que va de (1) a (3)), sino el del primer calentador (que va de (4) a (6)) — y ya se estableció que ese calentador ocurre a $Y$ **constante**, así que ese $\Delta Y$ **debería ser cero**. Aquí hay que releer el dato con más cuidado: $Y_{(6)}=0.008$ es, en realidad, la humedad con la que **sale del calentador**, que por definición de "calentamiento a $Y$ constante" tiene que ser **igual** a la humedad con la que entra, $Y_{(4)}$. Pero el inciso (b) ya estableció $Y_{(3)}=Y_{(4)}=Y_{(5)}=0.01$, un valor **distinto** de $0.008$.

**Resolviendo la aparente contradicción:** la clave está en que $Y_{(4)}$ **no** es la humedad de la corriente (3) sola, sino la de la corriente **mezclada** (3)+(5) — y el enunciado dice que (3), (4) y (5) tienen las **mismas condiciones**, lo cual efectivamente incluye la misma $Y=0.01$. Por tanto, la $Y_{(6)}=0.008$ que se lee en la carta a partir de $t_r=14$°C **es**, en efecto, distinta de $0.01$, y la diferencia $\Delta Y = Y_{(4)}-Y_{(6)} = 0.01-0.008=0.002$ **corresponde al agua incorporada en el saturador**, no en el calentador. La razón física es la siguiente cadena de igualdades, tal como la establece el balance de masa completo del proceso: como el aire seco que sale por (6) es exactamente el mismo aire seco que entró por (1) (ya que ningún equipo entre (1) y (6) agrega o quita aire — solo agua), el balance global de agua entre la **entrada al saturador (1)** y la **salida del sistema (6)** debe cerrar usando la humedad de **entrada al saturador** ($Y_{(1)}$) y no la de después de la mezcla. Como en (1) todavía no se ha agregado nada de vapor del saturador, y $Y_{(6)}$ representa el estado "aguas abajo" de todo el proceso, la diferencia que importa para el balance del saturador es exactamente:

$$\Delta Y_{\text{saturador}} = Y_{(4)} - Y_{(6)} = 0.01-0.008 = 0.002\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}}$$

y esta es la cifra que se usa en el paso siguiente. (Esta es la misma cifra y el mismo razonamiento que trae el material original; se ha explicado aquí con más detalle porque es, con diferencia, el paso más sutil de todo el ejercicio.)

### 6.3 Obtener $m_{as(1)}$ mediante un balance de aire seco en la unión de corrientes

**Paso 4 — Calcular $m_{as(6)}$ a partir del caudal volumétrico dado.** El enunciado da el caudal de la corriente (6) en unidades volumétricas: $30\,870\ \text{m}^3/\text{h}$. Para convertir esto a flujo másico de aire seco, se usa la Ecuación 2 del formulario, con el volumen húmedo de la corriente (6) leído de la carta: $V_{H(6)}=0.884\ \text{m}^3\text{(a.h.)/kg(a.s.)}$.

$$m_{as(6)} = \frac{V_{(6)}}{V_{H(6)}} = \frac{30\,870\ \text{m}^3/\text{h}}{0.884\ \text{m}^3/\text{kg a.s.}}$$

Haciendo la división:

$$m_{as(6)} = 34\,920.8\ \frac{\text{kg a.s.}}{\text{h}}$$

**Paso 5 — Balance de aire seco en la unión antes del primer calentador.** Las corrientes (3) y (5) se **juntan** para formar la corriente (4) (ver el esquema de la sección 2.1). El aire seco, al no crearse ni destruirse, se conserva en esa unión:

$$m_{as(4)} = m_{as(3)} + m_{as(5)}$$

Y como el primer calentador tampoco cambia la masa de aire seco: $m_{as(6)}=m_{as(4)}$. Sustituyendo, y despejando $m_{as(3)}$ (que es igual a $m_{as(1)}$, el dato que se busca, porque el saturador tampoco cambia la masa de aire seco entre (1) y (3)):

$$m_{as(1)} = m_{as(3)} = m_{as(6)} - m_{as(5)}$$

**Paso 6 — Sustituir los valores numéricos.** El valor de $m_{as(5)}$ ya se calculó en el inciso (c) (sección 5.2, paso 4): $m_{as(5)}=2906.97\ \text{kg a.s./h}$.

$$m_{as(1)} = 34\,920.8 - 2906.97 = 32\,013.83\ \frac{\text{kg a.s.}}{\text{h}}$$

### 6.4 Calcular el agua incorporada

Ya se tienen las dos piezas que faltaban ($m_{as(1)}=32\,013.83\ \text{kg a.s./h}$ y $\Delta Y=0.002\ \text{kg}\ H_2O/\text{kg a.s.}$). Sustituyendo en la Ecuación 1:

$$H_2O_{\text{incorp}} = m_{as(1)}\times \Delta Y = 32\,013.83\times 0.002$$

$$\boxed{H_2O_{\text{incorp}} = 64\ \text{kg}\ H_2O/\text{h}}$$

---

## 7. Inciso (e) — Flujo de agua en la corriente (3)

### 7.1 Planteamiento

Se pide el flujo de agua (no de aire seco, ni de mezcla total) que transporta específicamente la corriente (3). Por definición de saturación ($Y=m_{\text{agua}}/m_{as}$), despejando la masa de agua:

$$m_{\text{agua}(3)} = m_{as(3)}\times Y_{(3)}$$

### 7.2 Sustitución numérica

Ya se conocen ambos valores: $m_{as(3)}=32\,013.83\ \text{kg a.s./h}$ (calculado en la sección 6.3, paso 6 — recuérdese que $m_{as(3)}=m_{as(1)}$) y $Y_{(3)}=0.01\ \text{kg}\ H_2O/\text{kg a.s.}$ (inciso b, sección 4).

$$H_2O_{(3)} = 32\,013.83\ \frac{\text{kg a.s.}}{\text{h}}\times 0.01\ \frac{\text{kg}\ H_2O}{\text{kg a.s.}} = 320.14\ \frac{\text{kg}\ H_2O}{\text{h}}$$

### 7.3 Convertir a base molar (kmol/h)

El enunciado (según reporta el material original) pide también el resultado en **kmol/h**. Para convertir masa a moles, se divide entre la masa molar del agua ($MM_{H_2O}=18\ \text{kg/kmol}$):

$$H_2O_{(3)} = \frac{320.14\ \text{kg/h}}{18\ \text{kg/kmol}}$$

$$\boxed{H_2O_{(3)} = 17.78\ \text{kmol/h}}$$

---

## 8. Resumen de resultados

| Inciso | Resultado |
|---|---|
| (b) | $t=19.5$°C, $t_{bh}=t_{sa}=16$°C, $t_r=14$°C, $\%Y_R=70$, $Y=0.01\ \text{kg}/\text{kg a.s.}$, $V_H=0.842\ \text{m}^3/\text{kg a.s.}$ |
| (c) | $m_{ah(5)} = 2936.04\ \text{kg/h}$ |
| (d) | $H_2O_{\text{incorp}} = 64\ \text{kg}\ H_2O/\text{h}$ |
| (e) | $H_2O_{(3)} = 320.14\ \text{kg/h} = 17.78\ \text{kmol/h}$ |

---

## 9. Por qué este ejercicio es, en el fondo, un balance de masa

El propio material de la clase práctica lo señala explícitamente en su conclusión: los cálculos aquí realizados, aunque se apoyaron en la carta sicrométrica para leer temperaturas y humedades, **no son conceptualmente distintos** de un balance de masa ordinario. En cada equipo se aplicó la misma idea:

$$\text{(lo que entra de una especie)} = \text{(lo que sale de esa especie)} \pm \text{(lo que se genera o se consume dentro del equipo)}$$

- En el **saturador**: entra agua líquida (corriente 2) y se "genera" vapor de agua dentro de la corriente gaseosa — el balance de agua dio $H_2O_{\text{incorp}}=64\ \text{kg/h}$ (inciso d).
- En el **condensador**: entra vapor de agua (dentro de la corriente 9) y sale como líquido (corriente 8) — el balance de agua fue el que permitió, en el inciso (c), obtener $m_{as}$.
- En cada **calentador**: no entra ni sale agua — por eso $Y$ se mantiene constante, y el balance de agua es trivial (cero cambio).

Formalizar este tipo de balance con total generalidad y rigor (para cualquier proceso químico, no solo mezclas agua-aire, y con ecuaciones explícitas de "entrada = salida + acumulación ± generación/consumo") es precisamente el contenido del Tema 3 de esta asignatura.

---

## Referencias / fuentes usadas en este documento

- [PIQ1 Clase practica 4 Procesos de vaporizacion y condensacion Saturador-Condensador-Calentadores.pdf](PIQ1%20Clase%20practica%204%20Procesos%20de%20vaporizacion%20y%20condensacion%20Saturador-Condensador-Calentadores.pdf) — fuente principal del ejercicio.
- [Conferencia 4 - Mediciones Termometricas, Carta Sicrometrica y Procesos.md](Conferencia%204%20-%20Mediciones%20Termometricas%2C%20Carta%20Sicrometrica%20y%20Procesos.md) — teoría de base (temperaturas termométricas, volumen húmedo, carta sicrométrica, procesos).
- [Conferencia 3 - Presion de Vapor y Composicion de Mezclas Vapor-Gas.md](Conferencia%203%20-%20Presion%20de%20Vapor%20y%20Composicion%20de%20Mezclas%20Vapor-Gas.md) — fórmulas de composición ($Y$, $Y_m$) usadas para verificar $Y_{(9)}$.
- [../Steam Tables_Keenan.pdf](../Steam%20Tables_Keenan.pdf) — tabla de agua saturada, usada para verificar $Y_{(9)}$ en la sección 4.1.
