# NumPy & Pandas

[Diapositiva](https://docs.google.com/presentation/d/1pNHmH-25Cq3pHMAPVytUbR_YRvJJGmvz/edit?slide=id.g363e64b3470_0_47#slide=id.g363e64b3470_0_47)


### Objetivos de la Clase

1. Conocer las estructuras de datos en **Pandas**.
2. Comprender el uso de Pandas para la manipulación de grandes volúmenes de datos.
3. Conocer las estructuras de datos y su implementación en **Python**.
4. Entender el uso básico del paquete **NumPy** y sus operaciones vectorizadas.

---

## 1. Introducción

Python es ampliamente utilizado en ciencia de datos debido a librerías como **Pandas** y **NumPy**, que permiten:

* Manipular datos estructurados de forma eficiente.
* Realizar cálculos numéricos de manera rápida y segura.
* Preparar datos para análisis exploratorio y modelado predictivo.

---

## 2. Pandas: Manipulación de Datos

### 2.1 Estructuras Fundamentales

**Series (1D)**

```python
import pandas as pd

serie = pd.Series([10, 20, 30], index=['a', 'b', 'c'], name='MiSerie')
print(serie)
```

**DataFrames (2D)**

```python
data = {
    'Nombre': ['Ana', 'Luis', 'Emma'],
    'Edad': [28, 34, 22],
    'Ciudad': ['Buenos Aires', 'Córdoba', 'Rosario']
}
df = pd.DataFrame(data)
print(df)
```

---

### 2.2 Selección de Datos

```python
# Selección por columna
print(df['Nombre'])

# Selección por loc (etiquetas)
print(df.loc[0, 'Nombre'])

# Selección por iloc (posición)
print(df.iloc[1, 2])
```

---

### 2.3 Manejo de Datos Ausentes

```python
import numpy as np

df.loc[2, 'Edad'] = np.nan   # Insertar NaN
print(df.isnull())           # Detectar valores faltantes
print(df.fillna(30))         # Reemplazar valores faltantes
print(df.dropna())           # Eliminar filas con NaN
```

---

## 3. NumPy: Computación Numérica

### 3.1 Arrays y Estructuras de Datos

```python
import numpy as np

# Crear arrays
arr1 = np.array([1, 2, 3, 4])
arr2 = np.array([[1, 2], [3, 4]])

print(arr1.shape, arr1.ndim)  # Forma y dimensiones
print(arr2.shape, arr2.ndim)
```

---

### 3.2 Indexado y Slicing

```python
# Acceso a elementos
print(arr1[0], arr1[-1])
print(arr1[1:3])

# Acceso a columnas y filas
print(arr2[:, 1])    # Segunda columna
print(arr2[::-1, :]) # Filas en orden inverso
```

---

### 3.3 Operaciones Vectorizadas

```python
# Operaciones escalares
arr_sum = arr1 + 5
arr_mul = arr1 * 2

# Operaciones entre arrays
arr3 = np.array([5, 6, 7, 8])
print(arr1 + arr3)

# Producto matricial
print(np.matmul(arr2, np.array([[2, 0],[0,2]])))
```

---

### 3.4 Agregaciones y Estadísticas

```python
print(arr1.sum())
print(arr1.mean())
print(arr1.max(), arr1.min())
print(np.median(arr1))
print(np.std(arr1))
```

---

### 3.5 Concatenación y División de Arrays

```python
arr_cat = np.concatenate([arr1, arr3])
arr_vstack = np.vstack([arr1, arr3])
arr_hstack = np.hstack([arr1, arr3])

arr_split = np.split(arr_cat, [2,5])
```

---

## 4. Integración Pandas y NumPy

```python
# Crear columna usando operaciones vectorizadas de NumPy
df['Edad doble'] = np.array([28, 34, 30]) * 2
print(df)
```

---

## 5. Buenas Prácticas

* Inspecciona los datos antes de procesarlos: `df.head()`, `df.info()`, `df.describe()`.
* Maneja los valores faltantes antes de realizar cálculos estadísticos.
* Prefiere operaciones vectorizadas para mayor eficiencia.
* Mantén consistencia en los tipos de datos: `df.dtypes` o `arr.dtype`.

---

## 6. Ejercicios Propuestos

1. Cargar un dataset CSV de tu elección usando Pandas.
2. Detectar y manejar valores faltantes.
3. Calcular estadísticas básicas: suma, promedio, mediana y desviación estándar.
4. Crear nuevas columnas usando operaciones vectorizadas de NumPy.
5. Filtrar y seleccionar datos según condiciones específicas.
