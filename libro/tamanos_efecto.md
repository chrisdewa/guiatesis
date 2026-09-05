# Tamaños del efecto

Una diferencia **estadísticamente significativa** indica evidencia de que la diferencia no es cero, pero no dice **qué tan grande** es. Para describir su magnitud se utiliza un **tamaño del efecto** [@sullivan2012; @fritz2012].

Lo mismo ocurre al estudiar asociaciones: además de indicar si existe evidencia de asociación, interesa describir **su dirección y magnitud**.

:::{important} Idea clave
Cuando se describe una diferencia o asociación, conviene reportar una medida de tamaño del efecto y, cuando esté disponible, su intervalo de confianza.
:::

## El software suele calcularlo

JASP, jamovi, SPSS y otros programas pueden producir muchas de estas medidas directamente, aunque con frecuencia hay que solicitarlas de forma explícita.

Antes de exportar un análisis, conviene revisar opciones como **Effect size**, **Estimates** o **Confidence intervals**.

| Análisis | Tamaño del efecto |
|---|---|
| Prueba $t$ | $d$ de Cohen o $g$ de Hedges |
| Mann-Whitney / Wilcoxon | Correlación rango-biserial |
| Prueba no paramétrica con $Z$ | $r$ de Rosenthal |
| Correlación de Pearson | $r$ |
| Correlación de Spearman | $\rho$ |
| $\chi^2$ | $V$ de Cramér |
| Tabla $2\times2$ | Odds ratio (OR) |
| Regresión lineal | $B$ o $\beta$ |
| Regresión logística | OR |

:::{note} No siempre hace falta otra medida
En una correlación, $r$ o $\rho$ ya son tamaños del efecto. En una regresión, los coeficientes del modelo también describen la magnitud de la asociación.
:::

---

## d de Cohen

La $d$ de Cohen expresa una diferencia entre dos medias en **unidades de desviación estándar** [@cohen1988].

$$
d=\frac{\bar{x}_1-\bar{x}_2}{s_p}
$$

donde $s_p$ es la desviación estándar combinada.

| $\|d\|$ | Referencia aproximada |
|---:|---|
| 0.20 | pequeña |
| 0.50 | moderada |
| 0.80 | grande |

**Ejemplo:** `d = 0.62`

La media de un grupo difiere de la del otro en 0.62 desviaciones estándar: una diferencia de magnitud moderada a grande.

:::{caution} Los puntos de corte son orientativos
Los valores 0.20, 0.50 y 0.80 son convenciones. La importancia de una diferencia depende del desenlace y del contexto [@cohen1988; @fritz2012].
:::

:::{note} Herramienta para entender mejor
La visualización interactiva [Understanding Cohen's d](https://rpsychologist.com/cohend/) permite observar cómo cambia la separación entre dos distribuciones conforme aumenta el tamaño del efecto.
:::
---

## g de Hedges

La $g$ de Hedges es una diferencia estandarizada de medias similar a $d$, pero corrige parte de su sesgo en muestras pequeñas [@hedges1981].

Se interpreta prácticamente igual que la $d$ de Cohen.

**Ejemplo:** `g = -0.74`

La diferencia tiene una magnitud moderada a grande. El signo indica la dirección de la comparación.

:::{note} Cohen o Hedges
$d$ y $g$ responden a la misma pregunta. No representan dos efectos distintos. En muestras grandes suelen ser muy similares.
:::

---

## Correlación rango-biserial

La correlación rango-biserial ($r_{rb}$) es una medida de efecto útil para comparaciones basadas en rangos, como Mann-Whitney o Wilcoxon [@kerby2014].

Va de $-1$ a $1$:

- el **signo** indica la dirección;
- el **valor absoluto** indica la magnitud;
- valores cercanos a 0 indican poca separación.

Como orientación puede leerse de forma semejante a otros coeficientes tipo $r$: alrededor de 0.10 pequeño, 0.30 moderado y 0.50 grande [@cohen1988].

**Ejemplo:** `r_rb = 0.43`

La comparación muestra un efecto de magnitud moderada, dirigido hacia el grupo o condición definido como positivo por el programa.

:::{warning} Revisar la dirección
El signo depende del orden de los grupos o de cómo el programa define las diferencias. La categoría de referencia debe verificarse antes de interpretarlo.
:::

---

## r de Rosenthal

Cuando una prueba no paramétrica produce un estadístico $Z$, puede obtenerse un tamaño del efecto tipo $r$ [@fritz2012]:

$$
r=\frac{Z}{\sqrt{N}}
$$

donde $N$ es el número de observaciones utilizadas en la prueba.

| $|r|$ | Referencia aproximada |
|---:|---|
| 0.10 | pequeña |
| 0.30 | moderada |
| 0.50 | grande |

**Ejemplo:** `r = 0.36`

El efecto tiene una magnitud moderada.

:::{note} No es Pearson
Esta $r$ se deriva del estadístico $Z$. Comparte una escala similar, pero no es una correlación de Pearson.
:::

---

## Correlaciones: r y rho

Los coeficientes de Pearson ($r$) y Spearman ($\rho$) ya describen la **dirección y magnitud** de una asociación [@schober2018].

| Valor absoluto | Referencia aproximada |
|---:|---|
| 0.10 | pequeña |
| 0.30 | moderada |
| 0.50 | grande |

**Ejemplo:** `r = -0.58`

Existe una asociación negativa de magnitud grande: conforme aumenta una variable, la otra tiende a disminuir.

**Ejemplo:** `rho = 0.41`

Existe una asociación monotónica positiva de magnitud moderada.

:::{important} Correlación no implica causalidad
Una correlación grande describe una asociación fuerte. No demuestra que una variable cause cambios en la otra.
:::

---

## V de Cramér

La $V$ de Cramér describe la **magnitud de la asociación entre variables categóricas** y suele acompañar a una prueba de $\chi^2$ [@agresti2013].

Va de 0 a 1:

- 0 indica ausencia de asociación;
- valores mayores indican asociaciones más intensas;
- no tiene signo y, por tanto, no indica dirección.

**Ejemplo:** `V = 0.27`

Existe una asociación entre las variables, pero $V$ por sí sola no indica qué categorías explican esa asociación.

:::{caution} No usar cortes universales
Los puntos de referencia para $V$ dependen de las dimensiones de la tabla. Los valores 0.10, 0.30 y 0.50 solo son una orientación razonable en tablas $2\times2$ [@cohen1988].
:::

---

## Odds ratio

El **odds ratio (OR)** compara las *odds* de un desenlace entre dos grupos [@agresti2013].

Su valor nulo es **1**.

| OR | Lectura |
|---:|---|
| 1 | sin asociación |
| > 1 | odds mayores que en el grupo de referencia |
| < 1 | odds menores que en el grupo de referencia |

**Ejemplo:** tratamiento frente a control, con hospitalización como desenlace.

`OR = 0.60; IC 95%: 0.42 a 0.86`

Las *odds* de hospitalización fueron aproximadamente **40 % menores** en el grupo tratado que en el grupo control.

**Ejemplo:** `OR = 2.1`

Las *odds* del desenlace fueron aproximadamente **2.1 veces mayores** que en el grupo de referencia.

:::{warning} OR no es riesgo relativo
Un OR de 2 no significa necesariamente que el desenlace sea dos veces más probable. *Odds* y probabilidad no son equivalentes [@bland2000].
:::

:::{note} La dirección depende del desenlace
Un OR menor de 1 puede ser favorable si el desenlace es adverso, pero desfavorable si el desenlace es deseable. Siempre debe identificarse el desenlace y el grupo de referencia.
:::

---

## Coeficientes de regresión

Los coeficientes de regresión describen cuánto cambia el desenlace en relación con un predictor.

### B: coeficiente no estandarizado

Un coeficiente no estandarizado conserva las **unidades originales**.

**Ejemplo:** `B = -2.3`

Por cada unidad adicional del predictor, el desenlace disminuye en promedio 2.3 unidades, manteniendo constantes las demás variables del modelo.

Su magnitud depende de la escala utilizada. No existen puntos de corte universales para decidir si un $B$ es pequeño o grande.

### beta: coeficiente estandarizado

Un coeficiente estandarizado expresa el cambio en **desviaciones estándar**, no en las unidades originales [@bring1994].

**Ejemplo:** `beta = 0.38`

Por cada incremento de una desviación estándar en el predictor, el desenlace aumenta 0.38 desviaciones estándar.

La estandarización facilita comparar coeficientes expresados originalmente en escalas diferentes, pero no convierte a $\beta$ en una medida automática de importancia [@bring1994].

:::{important} B no siempre significa lo mismo que beta
Es frecuente utilizar $B$ para el coeficiente no estandarizado y $\beta$ para el estandarizado, pero la notación no es universal. Debe revisarse cómo los define el programa o artículo.
:::

### Regresión logística

En regresión logística, el coeficiente suele transformarse y presentarse como **odds ratio**.

**Ejemplo:** `OR ajustado = 1.72; IC 95%: 1.18 a 2.51`

Por cada unidad adicional del predictor, las *odds* del desenlace son 1.72 veces mayores, manteniendo constantes las demás variables del modelo.

---

## Atlas rápido

| Medida | ¿Qué describe? | Valor nulo | Lectura básica |
|---|---|---:|---|
| $d$ de Cohen | Diferencia de medias | 0 | desviaciones estándar de diferencia |
| $g$ de Hedges | Diferencia de medias | 0 | igual que $d$, con corrección de sesgo |
| $r_{rb}$ | Diferencia basada en rangos | 0 | dirección y magnitud |
| $r$ de Rosenthal | Efecto derivado de $Z$ | 0 | magnitud tipo $r$ |
| $r$ / $\rho$ | Correlación | 0 | dirección y magnitud |
| $V$ de Cramér | Asociación categórica | 0 | intensidad, sin dirección |
| OR | Asociación con un desenlace | 1 | cambio en las odds |
| $B$ | Regresión lineal | 0 | cambio en unidades originales |
| $\beta$ | Regresión estandarizada | 0 | cambio en desviaciones estándar |

:::{important} Para la discusión
No basta con escribir que una diferencia o asociación fue «estadísticamente significativa». El tamaño del efecto permite decir **qué tan grande fue**, **en qué dirección** y, junto con su intervalo de confianza, **con qué precisión se estimó** [@sullivan2012; @fritz2012].
:::
