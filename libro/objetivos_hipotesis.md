---
title: Objetivos e hipótesis
label: objetivos-hipotesis
---

# Objetivos e hipótesis

Los objetivos definen **qué debe responder el estudio**. Deben derivarse de la pregunta de investigación y conectar directamente con las [variables](variables.md), el [análisis estadístico](pruebas_estadisticas.md) y el [cálculo del tamaño de muestra](calculo_tamano_muestra.md). Un objetivo bien formulado especifica con claridad qué se estimará, comparará o relacionará. [@farrugia2010_objectives; @browner2022_dcr]

:::{important} Regla básica
Cada objetivo debe poder traducirse en:

1. variables observables;
2. una medida, comparación o parámetro concreto;
3. un análisis capaz de responderlo.

Si no puede hacerse esa traducción, el objetivo es demasiado ambiguo.
:::

## El problema define el objetivo

La pregunta y el objetivo expresan la misma intención de investigación en formas distintas.

| Pregunta | Objetivo |
|---|---|
| ¿Cuál es la prevalencia de anemia en esta población? | **Estimar** la prevalencia de anemia en la población estudiada. |
| ¿El tratamiento A reduce más el puntaje que el tratamiento B? | **Comparar** el cambio en el puntaje entre los grupos A y B. |
| ¿La exposición X se asocia con el desenlace Y? | **Evaluar la asociación** entre la exposición X y el desenlace Y. |
| ¿Qué tan bien discrimina una prueba entre sujetos con y sin la condición? | **Evaluar la capacidad discriminativa** de la prueba mediante el AUC. |

Los objetivos deben indicar la población, exposición o intervención, comparador y desenlace cuando estos elementos sean relevantes. En estudios observacionales, STROBE recomienda declarar objetivos específicos e hipótesis preespecificadas cuando existan. [@vandenbroucke2007_strobe]

## Objetivo general

El objetivo general expresa la **respuesta principal que busca el estudio**.

Una estructura útil es:

```text
[verbo analítico] + [desenlace o parámetro] + [exposición/intervención o comparación] + [población] + [momento, si es necesario]
```

Ejemplo:

> Comparar el cambio en el puntaje de síntomas entre los pacientes que reciben el tratamiento A y los que reciben el tratamiento B después de 12 semanas.

El objetivo identifica:

- qué se comparará: cambio en el puntaje;
- entre quiénes: tratamiento A frente a B;
- cuándo: después de 12 semanas.

## Objetivos específicos

Los objetivos específicos descomponen el objetivo general en preguntas necesarias para responderlo.

Por ejemplo, para un estudio cuyo objetivo general es evaluar la relación entre una exposición y un desenlace:

1. **Describir** las características de la población estudiada.
2. **Estimar** la frecuencia del desenlace.
3. **Comparar** la frecuencia del desenlace entre expuestos y no expuestos.
4. **Estimar** la asociación entre la exposición y el desenlace mediante una medida apropiada.

No es necesario convertir cada procedimiento del protocolo en un objetivo.

:::{caution} Los procedimientos no son objetivos
No deben formularse como objetivos:

- aplicar un cuestionario;
- revisar expedientes;
- recolectar muestras;
- construir una base de datos;
- realizar una prueba estadística.

Son actividades del método. El objetivo debe expresar **qué se pretende obtener de los datos**.
:::

La formulación de los objetivos debe revisarse junto con la [tabla de variables](variables.md). Si un objetivo menciona un desenlace, una exposición, una intervención o un predictor, estos elementos deben estar definidos y operacionalizados.

## Objetivo primario y objetivos secundarios

El **objetivo general** describe el propósito central del estudio. El **objetivo primario** establece la pregunta analítica principal. Con frecuencia coinciden, pero no son necesariamente sinónimos.

Cuando existen varios objetivos analíticos, conviene identificar cuál es el primario. Este determina normalmente:

- el desenlace principal;
- el análisis principal;
- la estimación o contraste principal;
- el [tamaño de muestra](calculo_tamano_muestra.md).

Los objetivos secundarios responden preguntas adicionales, pero no deben competir con el objetivo primario como si todos fueran igualmente centrales.

:::{important} Una tesis no necesita muchos objetivos
Agregar objetivos aumenta variables, análisis y resultados que deberán justificarse e interpretarse. Deben incluirse solo los necesarios para responder la pregunta de investigación.
:::

## Verbos útiles para redactar objetivos

El verbo debe anticipar **qué resultado producirá el estudio**. No existe un verbo mejor por sí mismo: debe corresponder con la pregunta, las variables y el análisis.

| Propósito del objetivo | Verbos recomendados | Ejemplo |
|---|---|---|
| **Describir una población o fenómeno** | describir, caracterizar | Describir las características clínicas de los pacientes con epilepsia farmacorresistente. |
| **Estimar una frecuencia o parámetro** | estimar, cuantificar | Estimar la prevalencia de anemia en niños menores de 5 años. |
| **Comparar grupos, momentos o condiciones** | comparar, contrastar | Comparar el cambio en el puntaje entre el grupo de intervención y el grupo control. |
| **Examinar una asociación** | evaluar, analizar | Evaluar la asociación entre exposición prenatal a tabaco y bajo peso al nacer. |
| **Estimar el efecto de una intervención o exposición** | estimar | Estimar el efecto del tratamiento sobre la presión arterial a las 12 semanas. |
| **Construir o evaluar una predicción** | desarrollar, predecir, evaluar | Desarrollar un modelo para predecir hospitalización a partir de variables clínicas. |
| **Evaluar desempeño diagnóstico o discriminativo** | estimar, evaluar, comparar | Estimar la sensibilidad y especificidad de una prueba para detectar la enfermedad. |
| **Evaluar propiedades de una medición o instrumento** | estimar, comparar, evaluar | Estimar la concordancia entre dos métodos de medición. |
| **Explorar relaciones no prespecificadas** | explorar, identificar | Explorar patrones clínicos asociados con la respuesta al tratamiento. |

:::{note} Preferir el verbo más específico
Si el resultado esperado puede expresarse como una cantidad, conviene usar un verbo que lo haga explícito.

- **Estimar** una prevalencia, una media, un riesgo, una sensibilidad o un efecto.
- **Comparar** grupos o momentos.
- **Evaluar una asociación** entre variables.
- **Predecir** un desenlace.
- **Describir** una población.

Verbos generales como **analizar** o **evaluar** son aceptables cuando el objeto del análisis queda claramente definido.
:::

### Verbos que suelen producir objetivos imprecisos

| Evitar como verbo principal | Problema | Preferir |
|---|---|---|
| **conocer** | No define un resultado observable | describir, estimar |
| **saber** | No especifica qué se medirá | estimar, comparar |
| **estudiar** | Puede significar prácticamente cualquier cosa | describir, comparar, evaluar |
| **investigar** | Describe la actividad general, no el objetivo | especificar la operación analítica |
| **demostrar** | Supone de antemano cuál será el resultado | comparar, estimar, evaluar |
| **comprobar** | Sugiere que se busca confirmar una conclusión previa | contrastar, evaluar |
| **determinar** | Puede ser demasiado general si no se especifica el parámetro | estimar, comparar, evaluar |

## Hipótesis

La hipótesis expresa una **respuesta anticipada a la pregunta de investigación**. Debe derivarse del problema y corresponder directamente con el objetivo principal. [@farrugia2010_objectives; @browner2022_dcr]

No toda investigación necesita una hipótesis. Los estudios cuyo propósito principal es **describir o estimar** un parámetro pueden formularse únicamente mediante una pregunta y objetivos.

:::{important} Una hipótesis principal
En una tesis suele definirse **una hipótesis principal**, correspondiente a la pregunta y al objetivo primario.

Los objetivos secundarios pueden generar análisis adicionales, pero no es necesario convertir cada uno en una nueva hipótesis dentro del protocolo.
:::

## De la hipótesis científica al análisis

Conviene distinguir tres niveles.

### Hipótesis epistemológica o sustantiva

Es la proposición científica acerca del fenómeno que se pretende estudiar. Surge del marco teórico y de los antecedentes, y expresa lo que se considera plausible sobre la realidad sin depender todavía de una prueba estadística específica.

> La intervención A produce una mayor mejoría clínica que la intervención B.

### Hipótesis de trabajo

Es la formulación concreta de la hipótesis principal para el estudio. Debe especificar la población, las variables, la comparación y, cuando corresponda, el momento de medición.

> En niños con la condición X, el tratamiento A producirá una mayor reducción del puntaje de síntomas a las 12 semanas que el tratamiento B.

En la práctica, esta es la hipótesis que suele declararse formalmente en la tesis.

Debe corresponder de manera directa con la pregunta y con el objetivo primario:

> **Pregunta:** ¿El tratamiento A reduce más el puntaje de síntomas que el tratamiento B después de 12 semanas?

> **Objetivo:** Comparar el cambio en el puntaje de síntomas entre los grupos A y B después de 12 semanas.

> **Hipótesis de trabajo:** El tratamiento A producirá una mayor reducción del puntaje de síntomas a las 12 semanas que el tratamiento B.

La pregunta, el objetivo y la hipótesis deben referirse al **mismo fenómeno, las mismas variables, la misma población y la misma comparación**.

### Hipótesis analíticas o estadísticas

Son las proposiciones que se contrastan durante el análisis estadístico.

Si $\Delta_A$ y $\Delta_B$ representan el cambio medio en los dos grupos:

$$
H_0:\Delta_A-\Delta_B=0
$$

$$
H_1:\Delta_A-\Delta_B\neq0
$$

Estas hipótesis no sustituyen a la hipótesis de trabajo. Son su **traducción al parámetro que será analizado**.

Un estudio puede requerir varias hipótesis estadísticas para análisis secundarios sin que por ello deba declarar múltiples hipótesis principales.

:::{note} La hipótesis no es el valor p
No debe formularse como:

> «Existe una diferencia estadísticamente significativa entre los grupos».

La significancia estadística es un resultado del análisis. La hipótesis debe expresar la diferencia, asociación o efecto que se espera encontrar.
:::

## Cuando no se necesita una hipótesis

Un objetivo de estimación no requiere necesariamente una hipótesis nula.

Por ejemplo:

> **Pregunta:** ¿Cuál es la prevalencia de anemia en esta población?

> **Objetivo:** Estimar la prevalencia de anemia y su intervalo de confianza del 95 %.

El propósito es estimar un parámetro, no probar que sea diferente de un valor arbitrario.

Lo mismo puede ocurrir al estimar:

- una media;
- una prevalencia;
- sensibilidad y especificidad;
- concordancia;
- un AUC;
- otros parámetros con sus intervalos de confianza.

En estos estudios, el [cálculo del tamaño de muestra](calculo_tamano_muestra.md) puede basarse en la precisión deseada de la estimación.

Para sensibilidad, especificidad, valores predictivos, razones de verosimilitud y AUC, consulte [Pruebas diagnósticas](pruebas_diagnostico.md).

## Hipótesis estadísticas frecuentes

La forma de $H_0$ depende del parámetro analizado.

| Análisis principal | Parámetro | Hipótesis nula |
|---|---|---|
| Comparación de medias | Diferencia de medias | $\mu_1-\mu_2=0$ |
| Comparación de proporciones | Diferencia de proporciones | $p_1-p_2=0$ |
| Correlación | Correlación poblacional | $\rho=0$ |
| Riesgo relativo | RR | $RR=1$ |
| Odds ratio | OR | $OR=1$ |
| Regresión lineal | Coeficiente | $\beta=0$ |
| Regresión logística | Coeficiente / OR | $\beta=0$ o $OR=1$ |
| Discriminación frente al azar | AUC | $AUC=0.5$ |

Estas hipótesis pertenecen principalmente al **plan de análisis**. La prueba correspondiente y su interpretación se describen en [Interpretación de pruebas estadísticas](pruebas_estadisticas.md). Para interpretar la magnitud de diferencias y asociaciones, consulte [Tamaños del efecto](tamanos_efecto.md).

## Dirección de la hipótesis

La hipótesis de trabajo puede expresar una dirección cuando existe una justificación previa:

> El tratamiento A producirá una reducción mayor que el tratamiento B.

Esto no obliga automáticamente a utilizar una prueba estadística unilateral. La decisión entre un contraste unilateral y bilateral es una decisión analítica que debe definirse **antes de observar los resultados** y estar metodológicamente justificada. [@browner2022_dcr]

## Correspondencia entre pregunta, objetivo, hipótesis y análisis

Antes de cerrar el protocolo, conviene comprobar la cadena completa:

| Elemento | Pregunta que debe responder |
|---|---|
| **Pregunta de investigación** | ¿Qué se quiere conocer o resolver? |
| **Objetivo primario** | ¿Qué se quiere estimar, comparar o relacionar? |
| **Hipótesis de trabajo** | ¿Qué respuesta se anticipa para esa pregunta? |
| **Variables** | ¿Qué datos permiten responderla? |
| **Parámetro** | ¿Qué medida resume la respuesta? |
| **Hipótesis estadística** | ¿Existe un valor nulo que se pretende contrastar? |
| **Análisis** | ¿Qué método estima o contrasta ese parámetro? |
| **Tamaño de muestra** | ¿Se calculó para ese objetivo primario? |

Ejemplo:

| Elemento | Definición |
|---|---|
| Pregunta | ¿El tratamiento A reduce más el puntaje que el tratamiento B? |
| Objetivo primario | Comparar el cambio medio de puntaje entre A y B |
| Hipótesis de trabajo | El tratamiento A producirá una mayor reducción del puntaje que B |
| Desenlace | Cambio de puntaje |
| Parámetro | $\mu_A-\mu_B$ |
| $H_0$ | $\mu_A-\mu_B=0$ |
| $H_1$ | $\mu_A-\mu_B\neq0$ |
| Análisis | Comparación de dos medias independientes |
| Tamaño de muestra | Calculado para detectar una diferencia $\Delta$ |

Esta correspondencia evita un problema frecuente: plantear una pregunta, formular una hipótesis distinta, calcular el tamaño de muestra para otra comparación y terminar analizando una tercera.

## Errores frecuentes

| Error | Corrección |
|---|---|
| «Determinar si existe una diferencia significativa...» | Definir **qué variable** se comparará y entre **qué grupos**. |
| «Demostrar que el tratamiento funciona.» | **Comparar** un desenlace predefinido entre los grupos. |
| «Aplicar la escala X.» | La aplicación de la escala pertenece al método. |
| Formular $H_0$ y $H_1$ para una prevalencia que solo se desea estimar | Reportar la estimación y su intervalo de confianza. |
| Objetivo principal sin desenlace claramente definido | Definir y operacionalizar el desenlace en [Variables](variables.md). |
| Hipótesis de trabajo que no corresponde con el objetivo primario | Reformularla para que responda exactamente a la misma pregunta. |
| Hipótesis estadística que no corresponde al análisis | Expresarla en términos del parámetro realmente evaluado. |
| Varios objetivos primarios sin jerarquía | Identificar un objetivo principal y separar los secundarios. |

## Revisión final

Antes de considerar terminada esta sección del protocolo:

- el objetivo general responde directamente a la pregunta de investigación;
- el objetivo primario identifica claramente el desenlace o parámetro principal;
- los objetivos específicos no son una lista de procedimientos;
- cada objetivo puede traducirse a variables observables;
- la hipótesis principal, cuando existe, corresponde con la pregunta y el objetivo primario;
- la hipótesis de trabajo está separada de las hipótesis estadísticas;
- los estudios puramente descriptivos o de estimación no fuerzan una hipótesis innecesaria;
- el análisis estadístico responde al mismo objetivo;
- el cálculo del tamaño de muestra corresponde al objetivo primario.
