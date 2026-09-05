# Interpretación de pruebas estadísticas

## Introducción
Las pruebas de hipótesis evalúan si una diferencia o asociación observada es compatible con la hipótesis nula. El valor p indica evidencia estadística; **no indica por sí solo la magnitud ni la importancia clínica del resultado**. Para interpretar magnitud, consulte [Tamaños del efecto](tamanos_efecto.md). @wasserstein2016_pvalues @wasserstein2019_beyond

| Resultado | ¿Qué responde? |
|---|---|
| **Estimación** | ¿Cuánto difieren o se asocian las variables? |
| **IC95%** | ¿Con qué precisión se estimó? |
| **Valor p** | ¿Qué tan compatibles son los datos con H0? |
| **Tamaño del efecto** | ¿Qué tan grande es la diferencia o asociación? |

```{warning}
**p > 0.05 no demuestra igualdad.** Puede reflejar ausencia de efecto, un efecto pequeño o una estimación imprecisa. @altman1995_absence
```

## Pruebas de normalidad

Las pruebas de normalidad evalúan si la distribución observada **difiere estadísticamente de una distribución normal**.

- **H0:** los datos proceden de una distribución normal.
- **H1:** los datos no proceden de una distribución normal.

| Prueba | Idea principal |
|---|---|
| **Shapiro-Wilk** | Compara los valores ordenados con los esperados bajo normalidad. |
| **Kolmogorov-Smirnov** | Compara la distribución acumulada observada con una distribución teórica. |
| **Anderson-Darling** | Similar a una prueba de bondad de ajuste, con mayor peso en las colas. |

**Interpretación general:**

- `p < 0.05`: existe evidencia contra la normalidad.
- `p ≥ 0.05`: no existe evidencia suficiente para rechazarla; **no demuestra normalidad**.

Shapiro-Wilk es una prueba específicamente diseñada para normalidad. @shapiro1965_normality  
En Kolmogorov-Smirnov, si la media y la desviación estándar de la normal se estiman con los mismos datos, se utiliza una corrección como la de Lilliefors. @lilliefors1967_ks  
Anderson-Darling da mayor peso a discrepancias en las colas. @anderson1952_ad

```{important}
**No utilice estas pruebas para decidir automáticamente entre una prueba paramétrica y una no paramétrica.**

Reglas como `Shapiro p > 0.05 → t de Student` y `Shapiro p < 0.05 → Mann-Whitney` no son una buena estrategia. Las pruebas de normalidad tienen poca potencia en muestras pequeñas y detectan desviaciones triviales en muestras grandes; además, usar un pretest para seleccionar el análisis posterior puede alterar sus propiedades inferenciales. @rochon2012_normality @kero2026_normality

Valore la distribución **observada o razonablemente asumida**, el tipo de variable y la pregunta de investigación. Revise la forma de los datos con [histograma](galeria_graficos.ipynb#histograma), [densidad](galeria_graficos.ipynb#densidad-kde) y [gráfico Q-Q](galeria_graficos.ipynb#Q-Q-plot). En t, ANOVA y regresión, cuando corresponda, la normalidad relevante es la de los **errores o residuos**.
```

---

## Dos grupos independientes

### t de Student / t de Welch

**Pregunta:** ¿difieren las medias de dos grupos independientes?

Ejemplo:

- Media A = 18.2
- Media B = 14.0
- Diferencia = 4.2 puntos
- IC95% 1.1 a 7.3
- p = 0.009
- Hedges g = 0.55

**Interpretación:**

> El grupo A presentó en promedio 4.2 puntos más que el grupo B (IC95% 1.1 a 7.3; p = 0.009), con un tamaño del efecto estandarizado moderado (g = 0.55).

La **t de Welch** responde la misma pregunta y suele preferirse cuando no se asume igualdad de varianzas. @altman1991_practical

---

### Mann-Whitney U

**Pregunta:** ¿los valores de un grupo tienden a ocupar posiciones mayores o menores que los del otro?

Ejemplo:

- Mediana A = 14, RIC 10 a 18
- Mediana B = 10, RIC 7 a 13
- U = 614
- p = 0.018
- Correlación biserial por rangos = 0.34

**Interpretación:**

> Los valores del grupo A tendieron a ser mayores que los del grupo B (U = 614; p = 0.018; r_rb = 0.34).

```{warning}
**Mann-Whitney no es, por definición, una prueba de medianas.**

Un resultado significativo indica que las observaciones de un grupo tienden a ocupar rangos distintos de las del otro. Sólo cuando las distribuciones tienen una forma similar puede interpretarse de manera sencilla como un desplazamiento de localización, que suele resumirse mediante medianas. @fay2010_wmw
```

Para cuantificar la magnitud puede utilizarse la **correlación biserial por rangos** o la **r de Rosenthal**. Consulte [Tamaños del efecto](tamanos_efecto.md). @fritz2012_effectsize

---

## Dos mediciones pareadas

### t de Student pareada

**Pregunta:** ¿la diferencia media dentro de los mismos sujetos es distinta de cero?

Ejemplo:

- Cambio medio = -3.8 puntos
- IC95% -5.1 a -2.5
- p < 0.001
- d pareada = -0.60

**Interpretación:**

> El puntaje disminuyó en promedio 3.8 puntos (IC95% 2.5 a 5.1 puntos de reducción; p < 0.001), con un efecto estandarizado moderado.

La unidad de análisis es la **diferencia dentro de cada sujeto**.

---

### Wilcoxon de rangos con signo

**Pregunta:** ¿las diferencias pareadas tienden sistemáticamente a ser positivas o negativas?

Ejemplo:

- Mediana antes = 18
- Mediana después = 13
- p = 0.004
- Correlación biserial por rangos pareados = -0.46

**Interpretación:**

> Las mediciones posteriores tendieron a ser menores que las iniciales (p = 0.004; r_rb = -0.46).

El estadístico puede aparecer como **W, V o T**, según el programa utilizado. Para la magnitud del efecto puede reportarse correlación biserial por rangos pareados o r de Rosenthal. @fritz2012_effectsize

---

## Variables categóricas

### Chi-cuadrada de bondad de ajuste

**Pregunta:** ¿las frecuencias observadas siguen una distribución esperada?

Ejemplo: comprobar si los grupos sanguíneos observados tienen las proporciones esperadas.

**Interpretación:**

> La distribución observada difirió de la esperada (χ² = 12.4; gl = 3; p = 0.006).

El valor p indica si existe evidencia de discrepancia; no indica por sí mismo qué categorías explican la diferencia.

---

### Chi-cuadrada de independencia

**Pregunta:** ¿dos variables categóricas están asociadas dentro de una misma población?

Ejemplo: sexo × respuesta al tratamiento.

**Interpretación:**

> Se encontró asociación entre sexo y respuesta al tratamiento (χ² = 5.79; gl = 1; p = 0.016).

Para cuantificar la magnitud puede reportarse **V de Cramér**. @agresti2018_categorical

---

### Chi-cuadrada de homogeneidad

**Pregunta:** ¿la distribución de una variable categórica es la misma en dos o más grupos?

Ejemplo: comparar la distribución de respuesta clínica entre tres tratamientos.

**Interpretación:**

> La distribución de respuestas no fue homogénea entre los grupos (χ² = 9.8; gl = 4; p = 0.044).

La matemática es la misma que en la prueba de independencia; cambia la **pregunta y el diseño**. @agresti2018_categorical

---

### Prueba exacta de Fisher

**Pregunta:** ¿existe asociación entre variables categóricas cuando la aproximación de chi-cuadrada no es adecuada?

La prueba clásica se aplica a tablas **2 × 2**, pero existen extensiones exactas para tablas **R × C**. @agresti2018_categorical @freeman1951_exact

Ejemplo 2 × 2:

- OR = 4.5
- IC95% 1.2 a 19.1
- Fisher p = 0.028

**Interpretación:**

> Se encontró asociación entre exposición y desenlace; las odds del desenlace fueron 4.5 veces mayores en los expuestos, aunque la estimación fue imprecisa.

Fisher proporciona el contraste; la magnitud debe expresarse con una medida apropiada como OR, RR o diferencia de riesgos.

---

### McNemar

**Pregunta:** ¿cambió una variable binaria medida dos veces en los mismos individuos?

Ejemplo: positivo/negativo antes y después.

**Interpretación:**

> La proporción de respuestas positivas cambió entre las dos mediciones (McNemar p = 0.012).

La prueba se basa en los **pares discordantes**.

---

## Tres o más grupos

### ANOVA de una vía

**Pregunta:** ¿existe evidencia de que al menos una media sea diferente?

Ejemplo:

- F(2,87) = 8.41
- p < 0.001
- η² = 0.16

**Interpretación:**

> Existieron diferencias entre las medias de los grupos (F(2,87) = 8.41; p < 0.001; η² = 0.16).

```{warning}
**Un ANOVA significativo no indica qué grupos difieren.**

Se requieren comparaciones post hoc o contrastes previamente definidos. @altman1996_anova @bland1995_multiple
```

Para la magnitud suelen utilizarse **η², η² parcial u ω²**, según el diseño. Consulte [Tamaños del efecto](tamanos_efecto.md).

---

### ANOVA de medidas repetidas

**Pregunta:** ¿cambia la media entre tres o más momentos o condiciones medidas en los mismos individuos?

**Interpretación:**

> Existió evidencia de cambio a lo largo del tiempo (F(2,78) = 9.2; p < 0.001).

El resultado global no indica entre qué momentos ocurre la diferencia. @schober2018_repeated

---

### Kruskal-Wallis

**Pregunta:** ¿los rangos difieren entre tres o más grupos independientes?

**Interpretación:**

> Se encontraron diferencias entre los grupos (H(2) = 11.3; p = 0.004).

No identifica qué grupos difieren; se requieren comparaciones posteriores. Como en Mann-Whitney, no debe interpretarse automáticamente como una prueba de medianas. @fay2010_wmw

---

### Friedman

**Pregunta:** ¿los rangos difieren entre tres o más mediciones pareadas?

**Interpretación:**

> Se encontraron diferencias entre las condiciones evaluadas (χ²(2) = 12.6; p = 0.002).

**Kendall W** puede utilizarse como medida de magnitud del efecto.

---

## Correlación

Los coeficientes de correlación describen **dirección y magnitud de asociación**. El propio coeficiente funciona como tamaño del efecto. Correlación no implica causalidad. @schober2018_correlation

| Coeficiente | ¿Qué describe? | Cuándo suele ser útil |
|---|---|---|
| **Pearson r** | Asociación lineal | Variables cuantitativas y relación aproximadamente lineal |
| **Spearman ρ** | Asociación monotónica basada en rangos | Datos ordinales, asimetría o relación monotónica no lineal |
| **Kendall τ-b** | Concordancia y discordancia entre pares | Muestras pequeñas, datos ordinales o presencia de empates |

### Pearson

$r$ varía entre -1 y 1.

- signo: dirección;
- $|r|$: magnitud;
- $r = 0$: ausencia de asociación **lineal**.

Ejemplo:

> Se observó una correlación lineal positiva moderada (r = 0.62; IC95% 0.45 a 0.75; p < 0.001).

En una relación lineal simple, $r^2$ representa la proporción de variabilidad compartida por ambas variables.

---

### Spearman

**Pregunta:** ¿al aumentar una variable la otra tiende a aumentar o disminuir de forma monotónica?

Ejemplo:

> Se observó una asociación monotónica negativa moderada (ρ = -0.54; p = 0.002).

Trabaja con rangos, por lo que no requiere una relación lineal. @schober2018_correlation

---

### Kendall tau

**Pregunta:** ¿con qué frecuencia los pares de observaciones son concordantes frente a discordantes?

$\tau$ varía entre -1 y 1. **Tau-b** ajusta por empates y suele ser una buena opción con muestras pequeñas o variables ordinales. @kendall1938_tau

Ejemplo:

> Se observó una asociación positiva moderada entre ambas variables (τ-b = 0.41; p = 0.006).

Los valores de τ suelen ser numéricamente menores que los de Spearman para una asociación similar; no deben compararse directamente como si fueran la misma escala.

---

## Regresión

La regresión estima la relación entre un **desenlace** y uno o más **predictores**.

### Regresión lineal

**Pregunta:** ¿cuánto cambia en promedio un desenlace continuo cuando cambia un predictor?

$$
\text{Puntaje} = \beta_0 + \beta_1(\text{edad})
$$

Ejemplo:

- β = -0.82
- IC95% -1.20 a -0.44
- p < 0.001

**Interpretación:**

> Por cada año adicional de edad, el puntaje disminuyó en promedio 0.82 puntos.

Un β no estandarizado se interpreta en las unidades originales. Un β estandarizado expresa cambios en desviaciones estándar. @schober2021_linear

---

### Regresión lineal múltiple

Ejemplo:

- β tratamiento = -4.1
- IC95% -6.3 a -1.9
- p < 0.001

**Interpretación:**

> Manteniendo constantes las demás variables del modelo, el grupo de tratamiento presentó en promedio 4.1 puntos menos que el grupo de referencia.

```{important}
**Ajustado** significa condicionado a las variables incluidas en el modelo. No significa que todo posible confusor haya sido controlado.
```

$R^2$ representa la proporción de variabilidad del desenlace explicada por el modelo; con varios predictores suele reportarse también $R^2$ ajustado.

---

### Regresión logística

**Pregunta:** ¿cómo cambian las odds de un desenlace binario según uno o más predictores?

Ejemplo:

- OR = 2.4
- IC95% 1.4 a 4.1
- p = 0.002

**Interpretación:**

> Las odds del desenlace fueron 2.4 veces mayores entre los expuestos que entre los no expuestos.

En un modelo múltiple:

> Manteniendo constantes las demás variables incluidas, las odds del desenlace fueron aproximadamente dos veces mayores entre los expuestos.

```{warning}
**OR no es lo mismo que RR.** Cuando el desenlace es frecuente, pueden diferir de forma importante.
```

@schober2021_logistic @agresti2018_categorical

---

## Resumen rápido

| Prueba | Pregunta principal | Magnitud |
|---|---|---|
| Shapiro-Wilk | ¿Hay evidencia contra normalidad? | No es una medida de efecto |
| Kolmogorov-Smirnov | ¿La distribución difiere de una distribución teórica? | No es una medida de efecto |
| Anderson-Darling | ¿La distribución difiere, especialmente en las colas? | No es una medida de efecto |
| t independiente / Welch | ¿Difieren dos medias independientes? | Diferencia de medias, d o g |
| Mann-Whitney | ¿Un grupo tiende a ocupar rangos mayores que otro? | r biserial por rangos o r de Rosenthal |
| t pareada | ¿La diferencia media pareada es distinta de cero? | Diferencia media, d pareada |
| Wilcoxon | ¿Las diferencias pareadas tienen dirección sistemática? | r biserial pareada o r de Rosenthal |
| χ² bondad de ajuste | ¿Las frecuencias siguen una distribución esperada? | Según el problema |
| χ² independencia | ¿Dos variables categóricas están asociadas? | V de Cramér |
| χ² homogeneidad | ¿La distribución categórica es igual entre grupos? | V de Cramér |
| Fisher | ¿Existe asociación en una tabla con frecuencias pequeñas? | OR, RR u otra medida apropiada |
| McNemar | ¿Cambió una respuesta binaria pareada? | Diferencia pareada u OR de discordantes |
| ANOVA | ¿Al menos una media difiere? | η², η² parcial u ω² |
| Kruskal-Wallis | ¿Difieren los rangos de ≥3 grupos? | ε² u otra medida basada en rangos |
| Friedman | ¿Difieren los rangos de ≥3 mediciones pareadas? | Kendall W |
| Pearson | ¿Existe asociación lineal? | r |
| Spearman | ¿Existe asociación monotónica? | ρ |
| Kendall | ¿Existe concordancia ordinal? | τ-b |
| Regresión lineal | ¿Cuánto cambia un desenlace continuo? | β, R² |
| Regresión logística | ¿Cómo cambian las odds? | OR |

## Cómo interpretar cualquier resultado

1. ¿Qué pregunta responde la prueba?
2. ¿Cuál es la **estimación** o tamaño del efecto?
3. ¿Cuál es su **IC95%**?
4. ¿Qué aporta el **valor p**?
5. ¿La magnitud es relevante en términos clínicos o científicos?

No basta con escribir “fue estadísticamente significativo”. El resultado debe decir **qué cambió, cuánto cambió y con qué precisión se estimó**. @wasserstein2019_beyond
