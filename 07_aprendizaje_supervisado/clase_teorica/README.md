# Unidad 7: Data Science - Aprendizaje Supervisado

## Tabla de Contenidos
1. [Introducción](#introducción)
2. [Modelo Analítico](#modelo-analítico)
3. [Inteligencia Artificial y Machine Learning](#inteligencia-artificial-y-machine-learning)
4. [Tipos de Aprendizaje Automático](#tipos-de-aprendizaje-automático)
5. [Aprendizaje Supervisado](#aprendizaje-supervisado)
6. [Algoritmos de Clasificación](#algoritmos-de-clasificación)
7. [Implementación de Modelos](#implementación-de-modelos)
8. [Referencias](#referencias)

---

## Introducción

Esta unidad teórica se enfoca en los fundamentos del **Data Science** y el **Aprendizaje Supervisado**, abordando desde la definición de modelos analíticos hasta la implementación de algoritmos de clasificación y regresión.

---

## Modelo Analítico

Un **modelo analítico** es un proceso que combina datos heterogéneos de múltiples fuentes para facilitar su análisis conjunto.

### Etapas del Modelo Analítico

| Fase | Descripción |
|------|-------------|
| Entendimiento del problema | Comprensión del contexto y descomposición del problema |
| Extracción de datos | Obtención de datos estructurados y no estructurados |
| Limpieza de datos | Manejo de duplicados, nulos y valores atípicos |
| Análisis exploratorio | Visualización y transformación de datos para identificar patrones |
| Selección de variables | Identificación de características más relevantes |
| Modelamiento | Aplicación de algoritmos de machine learning |
| Validación | Evaluación del rendimiento del modelo |
| Despliegue | Implementación en entorno productivo |

---

## Inteligencia Artificial y Machine Learning

### Definiciones Clave

- **Inteligencia Artificial (IA)**: Capacidad de una máquina de realizar tareas que requieren inteligencia similar a la humana.
- **Machine Learning (ML)**: Rama de la IA que automatiza la construcción de modelos analíticos mediante el aprendizaje a partir de datos.

### Componentes de la IA

| Componente | Ejemplos |
|------------|----------|
| Sistemas Cognitivos | Redes Neuronales, Planificación |
| Conocimiento | Robótica |
| Percepción | Procesamiento de Lenguaje Natural, Machine Learning |

---

## Tipos de Aprendizaje Automático

| Tipo | Descripción | Ejemplos |
|------|-------------|----------|
| Supervisado | Utiliza datos etiquetados para entrenar modelos | Regresión, Clasificación |
| No Supervisado | Encuentra patrones en datos sin etiquetar | Clustering, Asociación |
| Por Refuerzo | Aprende mediante sistema de recompensas | Agentes que interactúan con entornos |

---

## Aprendizaje Supervisado

### Características Principales
- Utiliza conjuntos de datos etiquetados
- Se divide en problemas de **regresión** y **clasificación**
- Permite predecir resultados basados en datos históricos

### Tipos de Problemas

| Tipo | Descripción | Ejemplos |
|------|-------------|----------|
| Regresión | Predice valores continuos | Precio de viviendas, demanda de productos |
| Clasificación Binaria | Dos clases posibles | Spam/No spam, Fraude/No fraude |
| Clasificación Multiclase | Tres o más clases | Categorización de productos, Clasificación de documentos |

---

## Algoritmos de Clasificación

### Algoritmos Populares

| Algoritmo | Abreviatura | Aplicaciones Típicas |
|-----------|-------------|---------------------|
| Árboles de Decisión | DT | Clasificación binaria y multiclase |
| K-Vecinos Más Cercanos | KNN | Reconocimiento de patrones, recomendaciones |
| Regresión Logística | LR | Clasificación binaria, detección de spam |
| Random Forest | RF | Clasificación robusta, selección de características |
| Máquinas de Vectores de Soporte | SVM | Clasificación de texto, reconocimiento de imágenes |

### Comparación de Algoritmos

| Algoritmo | Ventajas | Desventajas |
|-----------|----------|-------------|
| Árboles de Decisión | Fácil interpretación, maneja datos numéricos y categóricos | Propenso a overfitting, sensible a outliers |
| KNN | Simple, no requiere entrenamiento | Computacionalmente costoso, sensible a escala |
| Regresión Logística | Probabilístico, rápido entrenamiento | Límites de decisión lineales |

---

## Implementación de Modelos

### Ejemplo: Primer Modelo de Regresión Lineal

#### Paso 1: Preparación del Entorno
```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
import matplotlib.pyplot as plt
```

#### Paso 2: Carga y Exploración de Datos
```python
# Cargar dataset
data = pd.read_csv('dataset.csv')

# Exploración inicial
print(data.head())
print(data.info())
print(data.describe())
```

#### Paso 3: Preprocesamiento
```python
# Manejo de valores nulos
data = data.dropna()

# Selección de características
X = data[['feature1', 'feature2', 'feature3']]
y = data['target']

# División train-test
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

#### Paso 4: Entrenamiento del Modelo
```python
# Crear y entrenar modelo
model = LinearRegression()
model.fit(X_train, y_train)

# Coeficientes del modelo
print("Coeficientes:", model.coef_)
print("Intercepto:", model.intercept_)
```

#### Paso 5: Evaluación
```python
# Predicciones
y_pred = model.predict(X_test)

# Métricas de evaluación
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f"Error Cuadrático Medio: {mse:.2f}")
print(f"R² Score: {r2:.2f}")
```

#### Paso 6: Visualización
```python
# Gráfico de resultados
plt.scatter(y_test, y_pred)
plt.xlabel("Valores Reales")
plt.ylabel("Predicciones")
plt.title("Regresión Lineal: Reales vs Predicciones")
plt.plot([y_test.min(), y_test.max()], [y_test.min(), y_test.max()], 'k--', lw=2)
plt.show()
```

### Consideraciones Importantes
- **Calidad de datos**: Limpieza y preprocesamiento son cruciales
- **Feature engineering**: Selección y transformación de variables
- **Validación**: Uso de técnicas como cross-validation
- **Interpretabilidad**: Balance entre complejidad y explicabilidad

---

## Referencias

### Material Adicional
- History of Artificial Intelligence: https://www.javatpoint.com/history-of-artificial-intelligence
- Stenhouse K et al. (2021). Algoritmos de clasificación populares
- Nguyen D. et al. (2016). Joint Network Coding and Machine Learning for Error-prone Wireless Broadcast

