---
title: Cálculo del tamaño de muestra
label: calculo-tamano-muestra
---

# Cálculo del tamaño de muestra

El tamaño de muestra se elige a partir de la **pregunta principal**, la **hipótesis** y el **análisis que se utilizará para probar $H_0$**. No es necesario memorizar las fórmulas. Lo importante es identificar qué fórmula corresponde al diseño y reunir los parámetros que exige.

:::{important} Cómo usar esta página
1. Formula la hipótesis principal.
2. Escribe $H_0$.
3. Identifica la prueba estadística con la que intentarás rechazar $H_0$.
4. Selecciona la fórmula de tamaño de muestra correspondiente.
5. Sustituye los parámetros con valores justificados.
6. Redondea hacia arriba y ajusta por pérdidas.
:::

## De la hipótesis a la fórmula

En estudios analíticos, el cálculo parte de una hipótesis nula. Por ejemplo:

$$
H_0:\mu_1=\mu_2
$$

$$
H_1:\mu_1\neq\mu_2
$$

Si el desenlace es continuo y los grupos son independientes, $H_0$ se probará mediante una prueba para dos medias independientes. El tamaño de muestra debe calcularse para esa misma comparación.

En estudios cuyo objetivo principal es **estimar** un parámetro, como una prevalencia, una media, una sensibilidad o un AUC, no se necesita una $H_0$. En ese caso, el tamaño de muestra se determina por la **precisión deseada del intervalo de confianza**.

Referencia general: [@garcia2013; @chow2008; @wang2020].

```{mermaid}
flowchart TD
    A["Pregunta principal"] --> B{"Objetivo"}
    B -->|Estimar| C["Elegir precisión"]
    B -->|Contrastar| D["Definir H0 y prueba"]
```

## Parámetros que aparecen con frecuencia

| Símbolo | Significado |
|---|---|
| $n$ | Tamaño de muestra. Puede ser total, por grupo o por pares. |
| $N$ | Tamaño de una población finita. |
| $\alpha$ | Error tipo I. |
| $\beta$ | Error tipo II. La potencia es $1-\beta$. |
| $Z_{1-\alpha/2}$ | Cuantil normal asociado con una prueba bilateral. |
| $Z_{1-\beta}$ | Cuantil normal asociado con la potencia. |
| $d$ | Precisión absoluta deseada, usualmente la semiamplitud del IC. |
| $\Delta$ | Diferencia mínima que se desea detectar. |
| $L$ | Proporción esperada de pérdidas. |

Con $\alpha=0.05$ bilateral, $Z_{1-\alpha/2}=1.96$. Con potencia de 80%, $Z_{1-\beta}=0.842$.

## Guía rápida de selección

| Pregunta principal | $H_0$ o criterio | Método |
|---|---|---|
| Estimar una proporción | Precisión $d$ | Proporción |
| Estimar una media | Precisión $d$ | Media |
| Comparar dos proporciones independientes | $p_1=p_2$ | Dos proporciones |
| Comparar dos proporciones pareadas | $p_{01}=p_{10}$ | McNemar |
| Comparar una proporción con una referencia | $p=p_0$ | Una proporción |
| Comparar dos medias pareadas | $\mu_D=0$ | Media de diferencias |
| Comparar dos medias independientes | $\mu_1=\mu_2$ | Student o Welch |
| Detectar una correlación | $\rho=\rho_0$ | Fisher $z$ |
| Evaluar concordancia entre métodos | Tasa de discordancia y tolerancia | Liao |
| Comparar supervivencia entre dos grupos | $HR=1$ | Log-rank / riesgos proporcionales |
| Comparar supervivencia de un grupo con una referencia | $\varepsilon\leq0$ | Kaplan-Meier transformado |
| Estimar AUC | Precisión $d$ | Varianza del AUC |
| Estimar sensibilidad | Precisión $d$ | Sensibilidad |
| Estimar especificidad | Precisión $d$ | Especificidad |

# Fórmulas

## Estimar una proporción

**Úsala cuando:** el objetivo sea estimar una prevalencia, frecuencia o proporción con una precisión determinada.

```{math}
:label: eq-proporcion
n_0 = \frac{Z_{1-\alpha/2}^{2}\,p(1-p)}{d^{2}}
```

| Parámetro | Qué necesitas |
|---|---|
| $p$ | Proporción esperada |
| $d$ | Precisión absoluta deseada |
| $Z_{1-\alpha/2}$ | Nivel de confianza |

Referencia: [@garcia2013; @wang2020].

**Ejemplo de uso:** estimar una prevalencia esperada de 30% con precisión de $\pm5\%$ e IC 95%.

$$
n_0=\frac{1.96^2(0.30)(0.70)}{0.05^2}=322.68
$$

Resultado: **323 sujetos**.

:::{note} Si no conoces la proporción esperada
Puede utilizarse $p=0.50$, que produce el tamaño más conservador dentro de esta aproximación.
:::

### Corrección por población finita

**Úsala cuando:** la población accesible es conocida y el tamaño calculado representa una fracción importante de ella.

```{math}
:label: eq-proporcion-finita
n = \frac{n_0}{1+\dfrac{n_0-1}{N}}
```

| Parámetro | Qué necesitas |
|---|---|
| $n_0$ | Tamaño calculado sin corrección |
| $N$ | Tamaño de la población accesible |

Referencia: [@garcia2013].

## Estimar una media

**Úsala cuando:** el objetivo sea estimar una media con una precisión absoluta determinada.

```{math}
:label: eq-media
n_0 = \frac{Z_{1-\alpha/2}^{2}\sigma^{2}}{d^{2}}
```

| Parámetro | Qué necesitas |
|---|---|
| $\sigma$ | Desviación estándar esperada |
| $d$ | Precisión absoluta deseada |
| $Z_{1-\alpha/2}$ | Nivel de confianza |

Referencia: [@garcia2013; @chow2008].

**Ejemplo de uso:** estimar una media con $\sigma=12$ y precisión de $\pm3$.

$$
n_0=\frac{1.96^2(12^2)}{3^2}=61.46
$$

Resultado: **62 sujetos**.

La corrección por población finita utiliza la misma expresión de [](#eq-proporcion-finita).

```{mermaid}
flowchart TD
    A["Desenlace binario"] --> B{"Relación entre datos"}
    B -->|Independientes| C["Dos proporciones"]
    B -->|Pareados| D["McNemar"]
```

## Comparar dos proporciones independientes

$$
H_0:p_1=p_2
$$

**Prueba prevista:** comparación de dos proporciones independientes.

**Úsala cuando:** el desenlace sea binario y existan dos grupos independientes con asignación 1:1.

```{math}
:label: eq-dos-proporciones
n = \frac{\left[Z_{1-\alpha/2}\sqrt{2\bar p(1-\bar p)} + Z_{1-\beta}\sqrt{p_1(1-p_1)+p_2(1-p_2)}\right]^2}{(p_1-p_2)^2},
\qquad \bar p=\frac{p_1+p_2}{2}
```

| Parámetro | Qué necesitas |
|---|---|
| $p_1,p_2$ | Proporciones esperadas en cada grupo |
| $\bar p$ | Promedio de $p_1$ y $p_2$ |
| $\alpha$ | Error tipo I |
| $1-\beta$ | Potencia |

$n$ es el número requerido **por grupo**.

Referencia: [@chow2008].

**Ejemplo de uso:** detectar una diferencia entre 40% y 25%, con $\alpha=0.05$ y potencia de 80%.

Resultado: **152 sujetos por grupo**.

## Comparar dos proporciones pareadas

$$
H_0:p_{01}=p_{10}
$$

**Prueba prevista:** McNemar.

**Úsala cuando:** el desenlace sea binario y las observaciones estén pareadas, por ejemplo antes y después en los mismos sujetos.

```{math}
:label: eq-proporciones-pareadas
n = \frac{\left[Z_{1-\alpha/2}\sqrt{p_{01}+p_{10}} + Z_{1-\beta}\sqrt{p_{01}+p_{10}-(p_{01}-p_{10})^2}\right]^2}{(p_{01}-p_{10})^2}
```

| Parámetro | Qué necesitas |
|---|---|
| $p_{01}$ | Proporción que cambia de 0 a 1 |
| $p_{10}$ | Proporción que cambia de 1 a 0 |
| $\alpha$ | Error tipo I |
| $1-\beta$ | Potencia |

$n$ es el número de **pares completos**.

Referencia: [@chow2008].

**Ejemplo de uso:** $p_{10}=0.20$, $p_{01}=0.08$, $\alpha=0.05$, potencia 80%.

Resultado: **151 pares**.

## Comparar una proporción con un valor de referencia

$$
H_0:p=p_0
$$

**Úsala cuando:** quieras determinar si una proporción difiere de un valor conocido o de referencia.

```{math}
:label: eq-una-proporcion-prueba
n = \frac{\left[Z_{1-\alpha/2}\sqrt{p_0(1-p_0)} + Z_{1-\beta}\sqrt{p_1(1-p_1)}\right]^2}{(p_1-p_0)^2}
```

| Parámetro | Qué necesitas |
|---|---|
| $p_0$ | Proporción bajo $H_0$ |
| $p_1$ | Proporción que se espera detectar |
| $\alpha$ | Error tipo I |
| $1-\beta$ | Potencia |

Referencia: [@chow2008].

**Ejemplo de uso:** contrastar 30% contra una referencia de 20%.

Resultado: **137 sujetos**.

```{mermaid}
flowchart TD
    A["Desenlace continuo"] --> B{"Relación entre datos"}
    B -->|Pareados| C["t pareada"]
    B -->|Independientes| D["Student o Welch"]
```

## Comparar dos medias pareadas

$$
H_0:\mu_D=0
$$

**Prueba prevista:** prueba $t$ pareada.

**Úsala cuando:** el mismo sujeto tenga dos mediciones o existan pares emparejados.

```{math}
:label: eq-medias-pareadas
n = \frac{(Z_{1-\alpha/2}+Z_{1-\beta})^2\sigma_D^2}{\Delta^2}
```

| Parámetro | Qué necesitas |
|---|---|
| $\sigma_D$ | DE de las diferencias individuales |
| $\Delta$ | Diferencia media mínima de interés |
| $\alpha$ | Error tipo I |
| $1-\beta$ | Potencia |

$n$ es el número de **pares completos**.

Referencia: [@garcia2013; @chow2008].

**Ejemplo de uso:** detectar un cambio de 5 unidades con $\sigma_D=10$.

Resultado: **32 pares**.

```{mermaid}
flowchart TD
    A["Dos grupos independientes"] --> B{"Varianza común asumible"}
    B -->|Sí| C["Student"]
    B -->|No| D["Welch"]
```

## Comparar dos medias independientes con varianzas iguales

$$
H_0:\mu_1=\mu_2
$$

**Prueba prevista:** prueba $t$ de Student para grupos independientes.

**Úsala cuando:** haya dos grupos independientes, un desenlace continuo y sea razonable asumir una varianza común.

```{math}
:label: eq-medias-independientes-iguales
n = \frac{2\sigma^2(Z_{1-\alpha/2}+Z_{1-\beta})^2}{\Delta^2}
```

| Parámetro | Qué necesitas |
|---|---|
| $\sigma$ | DE común esperada |
| $\Delta=|\mu_1-\mu_2|$ | Diferencia mínima de interés |
| $\alpha$ | Error tipo I |
| $1-\beta$ | Potencia |

$n$ es el número requerido **por grupo**.

Referencia: [@garcia2013; @chow2008].

**Ejemplo de uso:** detectar una diferencia de 8 unidades con $\sigma=12$.

Resultado: **36 sujetos por grupo**.

## Comparar dos medias independientes sin asumir varianzas iguales

$$
H_0:\mu_1=\mu_2
$$

**Prueba prevista:** prueba $t$ de Welch.

**Úsala cuando:** haya dos grupos independientes y no se desee asumir la misma varianza en ambos. La expresión siguiente es una aproximación normal para planificación; con muestras pequeñas, el cálculo debe verificarse con los grados de libertad de Welch-Satterthwaite.

```{math}
:label: eq-medias-independientes-desiguales
n_1 = \frac{(Z_{1-\alpha/2}+Z_{1-\beta})^2\left(\sigma_1^2+\dfrac{\sigma_2^2}{r}\right)}{\Delta^2},
\qquad n_2=r\,n_1
```

| Parámetro | Qué necesitas |
|---|---|
| $\sigma_1,\sigma_2$ | DE esperada en cada grupo |
| $r=n_2/n_1$ | Razón de tamaños planeada |
| $\Delta$ | Diferencia mínima de interés |
| $\alpha$ | Error tipo I |
| $1-\beta$ | Potencia |

Referencia: [@chow2008].

**Ejemplo de uso:** detectar una diferencia de 8 unidades con DE de 10 y 16 y $r=1$.

Resultado aproximado: **44 sujetos por grupo**.

:::{note} Aproximación de Welch
Para muestras pequeñas conviene verificar el resultado con un método basado en la distribución $t$ no central.
:::

## Comparar dos medias mediante una diferencia estandarizada

$$
H_0:\mu_1=\mu_2
$$

**Úsala cuando:** el efecto esperado esté expresado como $d$ de Cohen y no en las unidades originales de la variable.

```{math}
:label: eq-medias-cohen
n = \frac{2(Z_{1-\alpha/2}+Z_{1-\beta})^2}{d_s^2},
\qquad d_s=\frac{|\mu_1-\mu_2|}{\sigma}
```

| Parámetro | Qué necesitas |
|---|---|
| $d_s$ | Diferencia estandarizada esperada |
| $\alpha$ | Error tipo I |
| $1-\beta$ | Potencia |

$n$ es el número requerido **por grupo**.

Referencia: [@cohen1988; @chow2008].

**Ejemplo de uso:** detectar $d_s=0.60$.

Resultado aproximado: **44 sujetos por grupo**.

## Detectar una correlación

$$
H_0:\rho=\rho_0
$$

**Prueba prevista:** contraste de una correlación mediante transformación $z$ de Fisher.

**Úsala cuando:** quieras detectar una correlación $\rho_1$ distinta de una correlación nula o de referencia $\rho_0$.

```{math}
:label: eq-correlacion
n = \left[\frac{Z_{1-\alpha/2}+Z_{1-\beta}}{\operatorname{atanh}(\rho_1)-\operatorname{atanh}(\rho_0)}\right]^2+3,
\qquad \operatorname{atanh}(\rho)=\frac{1}{2}\ln\left(\frac{1+\rho}{1-\rho}\right)
```

| Parámetro | Qué necesitas |
|---|---|
| $\rho_0$ | Correlación bajo $H_0$ |
| $\rho_1$ | Correlación mínima de interés |
| $\alpha$ | Error tipo I |
| $1-\beta$ | Potencia |

Referencia: [@cohen1988].

**Ejemplo de uso:** detectar $\rho=0.30$ frente a $\rho_0=0$.

Resultado: **85 sujetos**.


# Estudios de concordancia

## Concordancia entre dos métodos mediante un intervalo aceptable

**Criterio previsto:** definir antes del análisis qué diferencia entre dos mediciones se considera aceptable.

**Úsala cuando:** se comparen dos métodos de medición y la concordancia se defina por un intervalo clínicamente aceptable, en lugar de por una correlación.

Liao propone planear el estudio a partir de una tasa máxima de discordancia $a$, una probabilidad de tolerancia $b$ y un número máximo permitido de pares discordantes $k$ [@liao2010].

Si no se permite ningún par discordante, $k=0$:

```{math}
:label: eq-concordancia-k0
n \geq \frac{\ln(1-b)}{\ln(1-a)}
```

| Parámetro | Qué necesitas |
|---|---|
| $a$ | Tasa máxima de discordancia compatible con concordancia |
| $b$ | Probabilidad de tolerancia deseada |
| $k$ | Número máximo de pares discordantes permitido |
| $n$ | Número de pares completos |

Si se permiten $k\geq1$ discordancias, se elige el menor $n$ que cumpla:

```{math}
:label: eq-concordancia-k
1-\sum_{i=0}^{k}\binom{n}{i}(1-a)^{n-i}a^i \geq b
```

Referencia: [@liao2010].

**Ejemplo de uso:** con $a=0.05$, $b=0.80$ y $k=0$:

$$
n \geq \frac{\ln(0.20)}{\ln(0.95)}=31.38
$$

Resultado: **32 pares**.

:::{note} Concordancia no es correlación
Una correlación alta no implica que dos métodos concuerden. Este cálculo parte de una diferencia aceptable entre mediciones y de cuántas discordancias se tolerarán.
:::

## Comparar dos curvas de supervivencia

$$
H_0:HR=1
$$

**Prueba prevista:** log-rank bajo el supuesto de riesgos proporcionales.

**Úsala cuando:** el desenlace sea tiempo hasta un evento y se comparen dos grupos.

Primero se calcula el número de eventos:

```{math}
:label: eq-supervivencia-eventos
D = \frac{(Z_{1-\alpha/2}+Z_{1-\beta})^2}{q_1q_2[\ln(HR)]^2}
```

Después se convierte a número de sujetos:

```{math}
:label: eq-supervivencia-total
N = \frac{D}{P(E)}
```

| Parámetro | Qué necesitas |
|---|---|
| $HR$ | Hazard ratio mínimo de interés |
| $q_1,q_2$ | Proporción asignada a cada grupo |
| $P(E)$ | Proporción esperada con el evento |
| $\alpha$ | Error tipo I |
| $1-\beta$ | Potencia |

Referencia: [@chow2008; @wang2020].

**Ejemplo de uso:** $HR=0.70$, asignación 1:1, $\alpha=0.05$, potencia 80% y $P(E)=0.70$.

Resultado: **247 eventos**, equivalentes a aproximadamente **353 participantes**.

:::{warning} Riesgos proporcionales
La fórmula de Schoenfeld no es apropiada si el supuesto de riesgos proporcionales no es razonable.
:::


## Supervivencia de un solo grupo frente a una referencia

$$
H_0:\varepsilon\leq0
$$

$$
H_1:\varepsilon>0
$$

**Prueba prevista:** contraste de la probabilidad de supervivencia de Kaplan-Meier en un tiempo $t$ frente a una referencia histórica, después de aplicar una transformación $g$.

**Úsala cuando:** exista un solo grupo y el objetivo sea determinar si $S(t)$ supera un valor de referencia $S_0(t)$.

```{math}
:label: eq-supervivencia-una-muestra
n =
\left[
\frac{\tau_1\left(Z_{1-\alpha}+Z_{1-\beta}\right)}
{\varepsilon}
\right]^2,
\qquad
\varepsilon=g\{S_1(t)\}-g\{S_0(t)\}
```

| Parámetro | Qué necesitas |
|---|---|
| $S_0(t)$ | Supervivencia en el tiempo $t$ bajo $H_0$ |
| $S_1(t)$ | Supervivencia esperada bajo $H_1$ |
| $g$ | Transformación de la función de supervivencia |
| $\tau_1$ | DE asintótica de la estimación transformada bajo $H_1$ |
| $\alpha$ | Error tipo I unilateral |
| $1-\beta$ | Potencia |

Referencia: [@nagashima2021].

**Ejemplo de uso:** comparar una supervivencia a 12 meses esperada de 75% con una referencia de 60%. Sin censura y usando la transformación arcoseno-raíz cuadrada, $\tau_1=0.5$:

$$
\varepsilon=
\arcsin\sqrt{0.75}-\arcsin\sqrt{0.60}=0.1611
$$

$$
n=
\left[
\frac{0.5(1.645+0.842)}{0.1611}
\right]^2
=59.54
$$

Resultado: **60 sujetos**.

:::{warning} Censura y transformación
El ejemplo supone ausencia de censura. En estudios reales, $\tau_1$ depende del patrón de censura. Nagashima et al. muestran mejor comportamiento en muestras pequeñas con las transformaciones arcoseno-raíz cuadrada y log-minus-log que con la aproximación logarítmica convencional.
:::


# Estudios de exactitud diagnóstica

## Estimar el AUC

**Úsala cuando:** el objetivo principal sea estimar el área bajo la curva ROC con una precisión determinada.

Para igual número de sujetos con y sin la condición:

```{math}
:label: eq-auc-n
n_D=n_{\bar D}=\frac{Z_{1-\alpha/2}^2V(\widehat{\mathrm{AUC}})}{d^2}
```

```{math}
:label: eq-auc-var
V(\widehat{\mathrm{AUC}})=0.0099\exp\left(-\frac{a^2}{2}\right)(6a^2+16),
\qquad a=\sqrt{2}\,\Phi^{-1}(\widehat{\mathrm{AUC}})
```

| Parámetro | Qué necesitas |
|---|---|
| $\widehat{\mathrm{AUC}}$ | AUC esperada |
| $d$ | Precisión absoluta deseada |
| $Z_{1-\alpha/2}$ | Nivel de confianza |

$n_D$ y $n_{\bar D}$ corresponden a sujetos con y sin la condición.

Referencia: [@hajiantilaki2014].

**Ejemplo de uso:** AUC esperada de 0.80 e IC 95% con semiamplitud de 0.15.

Resultado: **21 sujetos con la condición y 21 sin ella**.

## Estimar sensibilidad

**Úsala cuando:** el objetivo principal sea estimar sensibilidad con una precisión determinada en una muestra procedente de una población con prevalencia esperada conocida.

```{math}
:label: eq-sensibilidad
n_{Se}=\frac{Z_{1-\alpha/2}^2\widehat{Se}(1-\widehat{Se})}{d^2\,Prev}
```

| Parámetro | Qué necesitas |
|---|---|
| $\widehat{Se}$ | Sensibilidad esperada |
| $d$ | Precisión deseada |
| $Prev$ | Prevalencia esperada |

Referencia: [@hajiantilaki2014].

**Ejemplo de uso:** $Se=0.80$, $Prev=0.30$, $d=0.10$, IC 95%.

Resultado: **205 participantes**.

## Estimar especificidad

**Úsala cuando:** el objetivo principal sea estimar especificidad con una precisión determinada.

```{math}
:label: eq-especificidad
n_{Sp}=\frac{Z_{1-\alpha/2}^2\widehat{Sp}(1-\widehat{Sp})}{d^2(1-Prev)}
```

| Parámetro | Qué necesitas |
|---|---|
| $\widehat{Sp}$ | Especificidad esperada |
| $d$ | Precisión deseada |
| $Prev$ | Prevalencia esperada |

Referencia: [@hajiantilaki2014].

**Ejemplo de uso:** $Sp=0.85$, $Prev=0.30$, $d=0.07$, IC 95%.

Resultado: **143 participantes**.

:::{warning} Casos y controles
Las fórmulas de sensibilidad y especificidad anteriores suponen muestreo de una población con prevalencia $Prev$. Si el número de sujetos con y sin la condición se fija por diseño, calcula cada estrato por separado.
:::

# Ajustes finales

## Pérdidas o datos no analizables

El ajuste se realiza después del cálculo principal:

```{math}
:label: eq-perdidas
n_{reclutar}=\frac{n_{analizable}}{1-L}
```

| Parámetro | Qué necesitas |
|---|---|
| $n_{analizable}$ | Tamaño que debe completar el análisis |
| $L$ | Proporción esperada de pérdidas |

Referencia: [@garcia2013; @chow2008].

**Ejemplo de uso:** si se necesitan 152 sujetos analizables y se esperan 10% de pérdidas:

$$
n_{reclutar}=\frac{152}{1-0.10}=168.89
$$

Resultado: **169 sujetos**.

:::{important} Regla final
Si un estudio requiere varios cálculos de tamaño de muestra, utiliza el mayor que sea compatible con el diseño. Redondea siempre hacia arriba.
:::

# Qué escribir en el protocolo

El protocolo debe indicar, de forma reproducible:

1. objetivo o hipótesis principal;
2. $H_0$, cuando corresponda;
3. prueba estadística prevista;
4. fórmula, método o programa utilizado;
5. valores introducidos y fuente de cada supuesto;
6. $\alpha$ y si la prueba es unilateral o bilateral;
7. potencia;
8. si $n$ es total, por grupo, por pares o por eventos;
9. ajuste por pérdidas y otros ajustes de diseño.

:::{bibliography}
:::
