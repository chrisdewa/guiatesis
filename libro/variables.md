# Variables

Una variable es una característica que se registra para cada unidad de observación y que puede tomar distintos valores. En un estudio clínico puede ser una edad, un diagnóstico, una exposición, una concentración, un puntaje o un desenlace.

Definir bien las variables conecta la **pregunta de investigación** con la **recolección de datos** y con el **análisis estadístico**. Una variable mal definida no se corrige después con una prueba estadística más sofisticada. @altman1991_practical

:::{important} Regla básica
Antes de construir la tabla de variables, cada objetivo debe poder traducirse en variables concretas que realmente puedan observarse o medirse.
:::

## Variable, medición y resultado del análisis

No todo lo que aparece en los resultados de una tesis es una variable.

**Son variables:**

- diagnóstico final;
- grupo de tratamiento;
- concentración de hemoglobina;
- edad;
- puntaje de una escala;
- presencia o ausencia de un evento.

**No son necesariamente variables:**

- sensibilidad;
- especificidad;
- concordancia;
- correlación;
- odds ratio;
- AUC;
- valor p.

Estas últimas suelen ser **medidas calculadas durante el análisis** a partir de una o más variables.

Por ejemplo, en un estudio de exactitud diagnóstica pueden registrarse como variables el resultado de la prueba índice y el diagnóstico establecido por el estándar de referencia. La sensibilidad, la especificidad y la AUC se calculan después a partir de esos datos.

:::{warning} Error frecuente
Es incorrecto llamar «variable dependiente» a una métrica únicamente porque es el resultado principal del análisis. La concordancia, una AUC o un coeficiente de correlación son estimadores, no características medidas directamente en cada participante.
:::

## Papel de cada variable

El papel de una variable depende de la **pregunta de investigación**. La misma variable puede funcionar como desenlace en un estudio y como predictor en otro.

| Papel | ¿Qué representa? | Ejemplo |
|---|---|---|
| **Desenlace** o dependiente | Lo que se desea explicar, comparar o predecir | Hospitalización |
| **Exposición** | Factor cuya asociación con el desenlace interesa estudiar | Exposición prenatal a tabaco |
| **Intervención** | Tratamiento o estrategia asignada | Fármaco A vs. placebo |
| **Predictor** | Variable utilizada para estimar un desenlace | Puntaje de una prueba de tamizaje |
| **Covariable** | Variable incluida para describir o ajustar el análisis | Edad |
| **Confusora** | Variable que puede distorsionar la asociación entre exposición y desenlace | Edad al estudiar actividad física y mortalidad |
| **Modificadora del efecto** | Variable para la cual el efecto puede ser diferente entre grupos o niveles | Efecto del tratamiento según gravedad basal |

En muchos formatos institucionales se solicita clasificar las variables como **independientes** y **dependientes**. Puede utilizarse esa nomenclatura cuando sea requerida, pero debe conservarse el papel real de cada variable en la pregunta de investigación.

:::{note} No toda covariable es confusora
Una variable no se convierte en confusora porque tenga `p < 0.05`, porque difiera entre grupos o porque esté disponible en la base. La decisión debe sustentarse en el conocimiento del problema y en la relación causal que se pretende estimar.
:::

## Tipo de variable

Para organizar y analizar los datos es más útil comenzar distinguiendo variables **categóricas** y **cuantitativas**. @altman1991_practical @agresti2018_categorical

### Variables categóricas

Representan categorías, no cantidades numéricas.

| Tipo | Característica | Ejemplo |
|---|---|---|
| **Dicotómica o binaria** | Dos categorías | Sí / No |
| **Nominal** | Tres o más categorías sin orden inherente | Grupo sanguíneo |
| **Ordinal** | Categorías con un orden definido | Leve / moderado / grave |

Asignar números a las categorías no convierte una variable en cuantitativa.

Por ejemplo:

```text
0 = masculino
1 = femenino
```

sigue representando una variable categórica nominal.

### Variables cuantitativas

Representan cantidades numéricas sobre las que tiene sentido calcular diferencias.

| Tipo | Característica | Ejemplo |
|---|---|---|
| **Discreta** | Valores contables | Número de crisis en un mes |
| **Continua** | Puede tomar valores dentro de un intervalo | Peso, talla, concentración sérica |

La forma en que una variable se registra puede modificar su tipo. La edad exacta puede considerarse cuantitativa continua; la edad registrada solo en años cumplidos es discreta; y «menor de 5 / 5 a 9 / 10 o más» es categórica ordinal.

:::{caution} Evitar categorizar sin necesidad
Convertir una variable cuantitativa en categorías elimina información y puede reducir la capacidad del análisis para detectar asociaciones. Si se utilizará un punto de corte, debe definirse y justificarse.
:::

## Escala de medición

Algunas instituciones solicitan además la escala clásica de medición.

| Escala | Propiedad | Ejemplo |
|---|---|---|
| **Nominal** | Categorías sin orden | Tipo de tratamiento |
| **Ordinal** | Categorías ordenadas | Clase funcional I, II, III, IV |
| **Intervalo** | Distancias comparables, sin cero absoluto | Temperatura en °C |
| **Razón** | Distancias comparables y cero con significado | Peso en kg |

En la práctica, para construir la base y seleccionar el análisis suele ser más importante especificar claramente si la variable será categórica o cuantitativa y cómo será registrada.

## Definición conceptual y operacional

Una tabla de variables debe dejar claro **qué significa** cada variable y **cómo se obtendrá su valor**.

### Definición conceptual

Describe el fenómeno o constructo que representa la variable.

Ejemplo:

> **Edad:** tiempo transcurrido desde el nacimiento.

### Definición operacional

Explica exactamente cómo se determinará el valor en este estudio.

Ejemplo:

> **Edad:** meses cumplidos entre la fecha de nacimiento registrada en el expediente y la fecha de inclusión al estudio.

La definición operacional debe permitir que otra persona pueda obtener el mismo dato siguiendo el protocolo.

Siempre que corresponda debe especificar:

- fuente del dato;
- instrumento o método de medición;
- momento de medición;
- unidad;
- categorías o puntos de corte;
- reglas para valores derivados.

:::{important} «Se obtendrá del expediente» no basta
La fuente del dato forma parte de la definición operacional, pero no sustituye la definición. Debe indicarse qué dato se tomará, de dónde y bajo qué regla.
:::

## Ejemplo de operacionalización

Supóngase un estudio que evalúa si un puntaje de tamizaje predice un diagnóstico clínico.

| Variable | Papel | Definición conceptual | Definición operacional | Tipo / escala | Unidad o codificación |
|---|---|---|---|---|---|
| Diagnóstico | Desenlace | Presencia de la condición de interés | Diagnóstico establecido mediante el estándar clínico definido en el protocolo | Categórica dicotómica / nominal | 0 = ausente; 1 = presente |
| Puntaje de tamizaje | Predictor | Resultado cuantitativo del instrumento | Puntaje total obtenido al aplicar el instrumento en la visita basal | Cuantitativa discreta | Puntos |
| Edad | Covariable | Tiempo desde el nacimiento | Meses cumplidos entre nacimiento e inclusión | Cuantitativa discreta | Meses |
| Sexo | Covariable | Sexo registrado del participante | Dato consignado en la fuente especificada por el protocolo | Categórica dicotómica / nominal | Codificación predefinida |

La **AUC** no debe agregarse como una quinta variable. Se calculará posteriormente utilizando el puntaje y el diagnóstico.

## Variables derivadas

Una variable derivada se calcula a partir de otros datos registrados.

Ejemplos:

- índice de masa corporal a partir de peso y talla;
- cambio de puntaje = puntaje final menos puntaje basal;
- edad en meses a partir de fechas;
- respuesta clínica definida como reducción de al menos 50 %.

La regla debe quedar definida antes del análisis.

Ejemplo:

$$
IMC = \frac{Peso\;(kg)}{Talla\;(m)^2}
$$

En la tabla conviene indicar que se trata de una variable derivada y especificar la fórmula o criterio utilizado.

## Mediciones repetidas

Cuando una variable se mide en varios momentos, el tiempo forma parte de la estructura de los datos.

Por ejemplo:

- presión arterial basal;
- presión arterial a 4 semanas;
- presión arterial a 12 semanas.

No debe escribirse simplemente «presión arterial» si el objetivo depende del momento de medición.

En una base en formato largo, estas mediciones pueden almacenarse mediante una variable para el valor y otra para el momento:

| id | semana | presion_sistolica |
|---|---:|---:|
| 001 | 0 | 118 |
| 001 | 4 | 114 |
| 001 | 12 | 110 |

## Tiempo hasta un evento

Los desenlaces de supervivencia requieren al menos dos elementos:

1. **tiempo de seguimiento**;
2. **indicador de evento**.

Por ejemplo, «supervivencia a 12 meses» no debe operacionalizarse únicamente como una fecha. Debe definirse cuál es el evento, desde qué momento comienza el seguimiento y cómo se manejarán los participantes sin evento al terminar la observación.

## De la tabla de variables a la base de datos

La tabla de variables debe funcionar como un pequeño **diccionario de datos**.

Para una base sencilla:

- cada columna representa una variable;
- cada fila representa una unidad de observación;
- cada celda contiene un solo valor.

En estudios con mediciones repetidas, una persona puede ocupar varias filas, una por cada momento de observación. La estructura debe corresponder con la unidad analítica.

Ejemplo adecuado:

| id | edad_meses | grupo | puntaje |
|---|---:|---|---:|
| 001 | 72 | intervención | 18 |
| 002 | 65 | control | 24 |

Ejemplo inadecuado:

| id | edad | resultados |
|---|---|---|
| 001 | 6 años | 18 basal, 14 final |

Guardar varios valores dentro de una misma celda dificulta el análisis y favorece errores.

## Codificación

La codificación debe definirse antes de comenzar la captura.

Ejemplo:

```text
diagnostico
0 = ausente
1 = presente
```

No deben mezclarse representaciones distintas de la misma categoría:

```text
Sí
si
SI
1
positivo
```

Todos esos valores podrían representar lo mismo, pero el software los interpretará como categorías diferentes.

### Valores perdidos

Un dato faltante no debe registrarse como `0` salvo que cero sea realmente el valor observado.

Es preferible utilizar un valor ausente reconocido por el programa, por ejemplo `NA`, y documentar su significado.

Si importa conocer la causa del dato faltante, puede registrarse en una variable adicional:

```text
motivo_faltante
1 = no acudió
2 = no se realizó la medición
3 = rechazo
4 = dato no disponible en expediente
```

## Nombres de variables

En la base de datos conviene utilizar nombres breves, inequívocos y consistentes.

Preferible:

```text
edad_meses
sexo
grupo
puntaje_basal
puntaje_12sem
diagnostico_final
```

Evitar:

```text
Edad del paciente en el momento de la valoración
Puntaje final!!!!
Variable 1
resultado
```

El nombre de la columna no sustituye la definición operacional. La explicación completa pertenece al diccionario o tabla de variables.

## Plantilla

Una tabla general puede construirse con las siguientes columnas:

| Variable | Papel en el estudio | Definición conceptual | Definición operacional | Tipo / escala | Unidad o codificación |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |
| | | | | | |

Si el formato institucional exige columnas adicionales, pueden agregarse sin perder esta lógica.

## Revisión rápida

Antes de cerrar la tabla de variables, comprobar que:

- cada objetivo tenga las variables necesarias para responderlo;
- el desenlace principal esté claramente identificado;
- cada variable tenga una definición operacional reproducible;
- estén definidos instrumento, fuente y momento de medición cuando correspondan;
- las unidades y categorías sean inequívocas;
- los puntos de corte estén preespecificados y justificados;
- las variables derivadas tengan una regla explícita;
- las métricas del análisis no se hayan confundido con variables;
- la codificación de la tabla coincida con la que se utilizará en la base.

## Para saber más

- [STROBE](https://www.strobe-statement.org/checklists/): para estudios observacionales, recomienda definir claramente desenlaces, exposiciones, predictores, posibles confusores y modificadores del efecto, además de describir cómo se midió cada variable.
- [Tidy Data](https://www.jstatsoft.org/v59/i10/): describe una estructura de datos en la que cada variable corresponde a una columna y cada observación a una fila.
