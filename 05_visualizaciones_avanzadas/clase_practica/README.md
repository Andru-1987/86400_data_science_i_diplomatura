# Visualización y Accesibilidad de Colores

## Daltonismo y diseño inclusivo

No todas las personas perciben los colores de la misma forma.
Cuando diseñamos visualizaciones, debemos **asegurarnos de que la información sea accesible** también para quienes tienen algún tipo de **daltonismo (deficiencia en la percepción del color)**.

**Lectura recomendada:**
[Daltonismo: cómo usar los colores teniendo en cuenta que no todos vemos igual](https://theconversation.com/daltonismo-como-usar-los-colores-teniendo-en-cuenta-que-no-todos-vemos-igual-215163#:~:text=Con%20los%20simuladores%20de%20daltonismo,daltonismo%20que%20tenga%20una%20persona)

 En el artículo encontrarás ejemplos de cómo elegir paletas efectivas y herramientas para **simular diferentes tipos de daltonismo**, lo cual resulta muy útil al momento de diseñar dashboards o gráficos para público general.

---

## Gráfico radial o radar chart

En esta clase veremos cómo construir un **gráfico radial (o radar chart)** para comparar múltiples variables de forma simultánea.
Exploraremos tanto la lógica geométrica detrás del gráfico como las diferentes formas de implementarlo.

**Notebook práctico:**
[00_radian.ipynb](./00_radian.ipynb)

Allí encontrarás ejemplos con:

* Cálculo de ángulos y normalización de datos
* Construcción del gráfico paso a paso
* Personalización de estilo y colores
* Opciones de hover e interactividad

---

##  Alternativas y visualización interactiva

Además de las librerías tradicionales de visualización como **Matplotlib** o **Seaborn**, exploraremos opciones más interactivas.

**Recurso recomendado:**
[Bokeh (visualización interactiva en Python)](https://bokeh.org/)

Con Bokeh es posible crear gráficos dinámicos que permiten:

* Interacción con el mouse (hover, zoom, selección)
* Exportación y guardado directo desde el navegador
* Integración con dashboards o notebooks Jupyter
