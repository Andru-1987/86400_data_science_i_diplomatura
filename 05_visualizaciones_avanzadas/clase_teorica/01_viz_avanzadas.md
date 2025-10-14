# Clase Teórica: Visualizaciones Avanzadas con Seaborn

## Objetivos de la Clase
- Conocer la relevancia de la visualización de datos
- Comprender análisis básico, relaciones entre elementos y distribución
- Conocer gráficos en más de dos dimensiones
- Aprender a graficar datos en Python con Seaborn
- Entender el uso básico de Matplotlib y Seaborn

## ¿Qué es Seaborn?
- Librería para hacer gráficos estadísticos en Python
- Fundamentada en matplotlib y pandas
- Realiza mapeo semántico y agregación estadística automáticamente

---

## Tipos de Funciones en Seaborn

`Funciones Axes-Level` vs `Figure-Level`

**Axes-Level**: Funciones que trabajan sobre ejes específicos

```python
# Ejemplo Axes-Level
sns.histplot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack")
```

**Figure-Level**: Funciones que crean figuras completas
```python
# Ejemplo Figure-Level
sns.displot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack")
```

- Funciones Axes-level (de nivel de ejes): Trabajan sobre un objeto Axes de Matplotlib específico y que ya debe existir. Dibujan en un solo "subplot" o conjunto de ejes. Piensa en ellas como "artistas" que pintan en un lienzo dado.

- Funciones Figure-level (de nivel de figura): Crean su propia figura completa (un objeto Figure de Matplotlib) con uno o más Axes (subplots) internamente. Piensa en ellas como "arquitectos" que diseñan y construyen toda la casa (figura) y sus habitaciones (ejes) de una vez.


---

## Ejemplos de Visualizaciones con Seaborn



## Consideraciones Importantes

### Mejores Prácticas
- Usar gráficos de líneas para series temporales
- Evitar gráficos de barras para datos temporales
- Considerar siempre la correlación vs causalidad
- Elegir el gráfico apropiado para el tipo de datos