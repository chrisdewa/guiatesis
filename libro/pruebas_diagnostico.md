# Pruebas diagnósticas

Una prueba diagnóstica se evalúa comparando una **prueba índice** contra un **estándar de referencia**. En un estudio básico, los mismos participantes deben contar con ambos resultados. La muestra debe parecerse, en lo posible, a la población en la que se pretende utilizar la prueba; comparar únicamente casos muy evidentes contra controles completamente sanos puede sobreestimar su desempeño @bossuyt2015_stard.

## Tabla 2 × 2

El resultado de la prueba índice y del estándar de referencia se resume en una tabla 2 × 2:

| | Condición presente | Condición ausente |
|---|---:|---:|
| **Prueba positiva** | VP (a) | FP (b) |
| **Prueba negativa** | FN (c) | VN (d) |

- **VP:** verdadero positivo.
- **FP:** falso positivo.
- **FN:** falso negativo.
- **VN:** verdadero negativo.

Aunque algunas fórmulas utilizan `a`, `b`, `c` y `d`, suele ser más fácil trabajar con VP, FP, FN y VN.

## Sensibilidad y especificidad

Son las medidas básicas de desempeño diagnóstico @altman1994_sensibilidad.

### Sensibilidad

De todos los **enfermos**, ¿cuántos fueron detectados?

$$
Sensibilidad =
\frac{VP}{VP+FN}
=
\frac{VP}{Enfermos}
$$

Una sensibilidad de 90 % significa que la prueba detecta al 90 % de las personas que realmente presentan la condición.

**Mayor sensibilidad → menos falsos negativos.**

### Especificidad

De todos los **sanos**, ¿cuántos fueron correctamente clasificados como negativos?

$$
Especificidad =
\frac{VN}{VN+FP}
=
\frac{VN}{Sanos}
$$

Una especificidad de 90 % significa que la prueba clasifica correctamente como negativas al 90 % de las personas que no presentan la condición.

**Mayor especificidad → menos falsos positivos.**

## Valores predictivos

Los valores predictivos parten del **resultado de la prueba**, no del estado real del paciente @altman1994_predictivos.

### Valor predictivo positivo

De todas las **pruebas positivas**, ¿cuántas corresponden realmente a enfermos?

$$
VPP =
\frac{VP}{VP+FP}
=
\frac{VP}{Positivos}
$$

### Valor predictivo negativo

De todas las **pruebas negativas**, ¿cuántas corresponden realmente a sanos?

$$
VPN =
\frac{VN}{VN+FN}
=
\frac{VN}{Negativos}
$$

## ¿Por qué importa la prevalencia?

La sensibilidad y la especificidad se calculan dentro de enfermos y sanos. El VPP y el VPN, en cambio, dependen también de **qué tan frecuente sea la condición** en la población donde se aplica la prueba @altman1994_predictivos.

Por eso, si la proporción de enfermos de la muestra fue fijada por el diseño, los valores predictivos observados en esa muestra no deben trasladarse directamente a la población.

Si se dispone de una prevalencia esperada $P$, pueden calcularse valores predictivos para esa prevalencia:

$$
VPP =
\frac{Sensibilidad \times P}
{(Sensibilidad \times P) + [(1-Especificidad)(1-P)]}
$$

$$
VPN =
\frac{Especificidad \times (1-P)}
{[(1-Sensibilidad)P] + [Especificidad(1-P)]}
$$

Por ejemplo, con sensibilidad de 90 % y especificidad de 90 %:

| Prevalencia | VPP | VPN |
|---:|---:|---:|
| 50 % | 90 % | 90 % |
| 5 % | 32 % | 99 % |

La prueba es la misma; lo que cambió fue la población.

Este cálculo supone que la sensibilidad y la especificidad estimadas son razonablemente aplicables a la población de interés.

## Razones de verosimilitud

Las razones de verosimilitud (*likelihood ratios*, LR) resumen cuánto favorece un resultado la presencia o ausencia de la condición @deeks2004_lr.

### Resultado positivo

$$
LR+ =
\frac{Sensibilidad}
{1-Especificidad}
$$

- $LR+ = 1$: el resultado positivo no discrimina.
- Cuanto mayor sea el $LR+$, mayor evidencia aporta un resultado positivo a favor de la condición.

### Resultado negativo

$$
LR- =
\frac{1-Sensibilidad}
{Especificidad}
$$

- $LR- = 1$: el resultado negativo no discrimina.
- Cuanto más cercano sea el $LR-$ a 0, mayor evidencia aporta un resultado negativo contra la presencia de la condición.

Los LR son útiles, pero no son indispensables en todos los trabajos de tesis.

## Puntos de corte

Muchas pruebas producen un valor continuo: una concentración, una puntuación o alguna otra medida numérica. Para convertirlo en un resultado positivo o negativo debe elegirse un **punto de corte**.

Si valores mayores indican mayor probabilidad de la condición:

- **bajar el punto de corte** → más resultados positivos → mayor sensibilidad y menor especificidad;
- **subir el punto de corte** → menos resultados positivos → menor sensibilidad y mayor especificidad.

Ejemplo:

| Punto de corte | Sensibilidad | Especificidad | $1-Especificidad$ |
|---:|---:|---:|---:|
| ≥ 5 | 0.95 | 0.40 | 0.60 |
| ≥ 10 | 0.85 | 0.70 | 0.30 |
| ≥ 15 | 0.70 | 0.90 | 0.10 |
| ≥ 20 | 0.45 | 0.97 | 0.03 |

No existe necesariamente un punto de corte universalmente mejor.

- Si importa especialmente **no perder casos**, se favorece sensibilidad.
- Si importa especialmente **evitar falsos positivos**, se favorece especificidad.

## Curva ROC

Cada punto de corte de la tabla anterior puede representarse como un punto en una curva ROC (*receiver operating characteristic*) @zweig1993_roc:

$$
x = 1-Especificidad
$$

$$
y = Sensibilidad
$$

Por tanto, la curva ROC muestra el intercambio entre sensibilidad y especificidad para todos los puntos de corte posibles.

El área bajo la curva, **AUC**, resume la capacidad de discriminación de la prueba:

$$
AUC = 0.5
$$

indica discriminación equivalente al azar, mientras que:

$$
AUC = 1
$$

indica discriminación perfecta.

La AUC describe la **discriminación global** de la prueba. No indica cuál punto de corte debe utilizarse. Ver [Curva ROC](./galeria_graficos.ipynb#curva-roc) en la galería de gráficos.

## Índice de Youden

Una forma simple de buscar un punto de corte que equilibre sensibilidad y especificidad es el índice de Youden @youden1950:

$$
J =
Sensibilidad + Especificidad - 1
$$

Aplicado al ejemplo anterior:

| Punto de corte | Sensibilidad | Especificidad | $J$ |
|---:|---:|---:|---:|
| ≥ 5 | 0.95 | 0.40 | 0.35 |
| ≥ 10 | 0.85 | 0.70 | 0.55 |
| ≥ 15 | 0.70 | 0.90 | **0.60** |
| ≥ 20 | 0.45 | 0.97 | 0.42 |

Aquí, el punto ≥15 maximiza $J$.

Youden identifica el mejor **compromiso matemático** cuando sensibilidad y especificidad reciben el mismo peso. No necesariamente identifica el mejor punto de corte clínico.

## Interpretación mínima

Un resultado puede reportarse de forma directa:

> Con un punto de corte ≥15, la prueba presentó una sensibilidad de 70 % y una especificidad de 90 %. Detectó al 70 % de quienes presentaban la condición y clasificó correctamente como negativos al 90 % de quienes no la presentaban.

Si se reportan VPP o VPN, debe quedar claro a qué prevalencia corresponden.

Las medidas principales deben acompañarse de sus **intervalos de confianza de 95 %** @bossuyt2015_stard.

## Para saber más

- [STARD 2015](https://www.equator-network.org/reporting-guidelines/stard/): lista de elementos que deben reportarse en estudios de exactitud diagnóstica @bossuyt2015_stard.
- [Sensitivity and specificity](https://www.bmj.com/content/308/6943/1552): nota breve de *BMJ* sobre sensibilidad y especificidad @altman1994_sensibilidad.
- [Predictive values](https://www.bmj.com/content/309/6947/102.1): nota breve de *BMJ* sobre valores predictivos y prevalencia @altman1994_predictivos.
- [Likelihood ratios](https://www.bmj.com/content/329/7458/168): introducción breve a LR @deeks2004_lr.
