# Clase: Introducción a NumPy y Pandas

[Presentación](https://docs.google.com/presentation/d/135XQdDjAvsoXtqDWhASGQ8-YWBFS5bDgxyJjfycykYs/edit?slide=id.g2204e13b0d5_2_631#slide=id.g2204e13b0d5_2_631)

## Objetivos de la clase

* Comprender la importancia de usar bibliotecas optimizadas como **NumPy** y **Pandas** en proyectos de ciencia de datos.
* Manipular estructuras de datos con **NumPy**: arrays, operaciones vectorizadas, álgebra lineal.
* Explorar los componentes fundamentales de **Pandas**: Series y DataFrames.
* Aplicar técnicas de indexación, selección y transformación de datos reales.
* Leer archivos en distintos formatos (`.csv`, `.txt`, `.xlsx`, APIs y GitHub).

---

## Parte 1: NumPy

### Importación de la librería

```python
import numpy as np
```

### Ejercicio 1: Crear vectores

```python
# Crear un vector desde una lista
v = np.array([1, 2, 3, 4])
print(v)
```

### Ejercicio 2: Operaciones vectorizadas

```python
a = np.array([10, 20, 30])
b = np.array([1, 2, 3])

print(a + b)     # Suma elemento a elemento
print(a * 2)     # Multiplicación escalar
print(b ** 2)    # Potencia
```

### Ejercicio 3: Matrices y álgebra lineal

```python
A = np.array([[1, 2], [3, 4]])
print(A.T)              # Transpuesta
print(np.linalg.inv(A)) # Inversa

B = np.array([[5, 6], [7, 8]])
print(np.dot(A, B))     # Producto matricial
```

### Ejercicio 4: Tablero de ajedrez con reshape

```python
ajedrez = np.arange(1,65).reshape(8,8)
print(ajedrez)
```

---

## Parte 2: Pandas

### Importación

```python
import pandas as pd
```

### Ejercicio 1: Crear Series

```python
s = pd.Series([10, 20, 30], index=['a', 'b', 'c'])
print(s)
```

### Ejercicio 2: Crear DataFrames

```python
data = {
    'nombre': ['Ana', 'Luis', 'Juan'],
    'edad': [23, 35, 29],
    'ciudad': ['Córdoba', 'Buenos Aires', 'Rosario']
}

df = pd.DataFrame(data)
print(df)
```

### Ejercicio 3: Selección e indexación

```python
print(df['edad'])          # Seleccionar columna
print(df[df['edad'] > 30]) # Filtrar por condición
print(df.loc[1])           # Acceder por etiqueta
print(df.iloc[0])          # Acceder por posición
```

---

## Parte 3: Lectura de Archivos con Pandas

### Lectura CSV

```python
df = pd.read_csv('winequality-red.csv', sep=',')
print(df[['density','pH','sulphates','alcohol','quality']].head())
```

### Lectura TXT

```python
df = pd.read_csv('pokemon_data.txt', delimiter='\t')
print(df[['Name','Type 1','HP','Attack','Defense']].head())
```

### Lectura Excel

```python
df = pd.read_excel('defaultoutput.xlsx')
print(df[['ID','Year_Birth','Education','Income']].head())
```

### Lectura desde GitHub

```python
url = "https://raw.githubusercontent.com/JJTorresDS/stocks-ds-edu/main/stocks.csv"
df = pd.read_csv(url, index_col=0)
print(df[['AMZN','MCD','SBUX','GOOG','MSFT']].head())
```

---

## Actividad Práctica

### 1. NumPy: Manipulación de Arrays

```python
array_simple = np.array([1, 2, 3, 4, 5])
matriz_2d = np.array([[1, 2, 3], [4, 5, 6]])
zeros = np.zeros((3, 3))
ones = np.ones((2, 4))

print(array_simple, matriz_2d, zeros, ones)
```

### 2. Pandas: Operaciones básicas

```python
datos = {
    "Nombre": ["Juan", "María", "Pedro"],
    "Edad": [30, 25, 40],
    "Ciudad": ["Caracas", "Maracaibo", "Valencia"]
}
df = pd.DataFrame(datos)

# Filtrado
print(df[df["Edad"] > 30])

# Nueva columna
df["Edad_meses"] = df["Edad"] * 12
print(df)
```

### 3. Ejercicio final: Análisis de cotizaciones bursátiles

1. Cargar el dataset desde GitHub:

   ```
   https://raw.githubusercontent.com/JJTorresDS/stocks-ds-edu/main/stocks.csv
   ```
2. Calcular el rendimiento promedio mensual de cada acción.
3. Identificar la acción con mayor volatilidad.
4. Graficar la evolución de las 3 acciones con mejor rendimiento.

```python
import matplotlib.pyplot as plt

url = 'https://raw.githubusercontent.com/JJTorresDS/stocks-ds-edu/main/stocks.csv'
stocks_df = pd.read_csv(url)
stocks_df['formatted_date'] = pd.to_datetime(stocks_df['formatted_date'])
stocks_df = stocks_df.set_index('formatted_date')

print(stocks_df.head())
```

---

## Discusión Guiada

* ¿Cuáles son las ventajas prácticas de usar NumPy frente a listas?
* ¿Por qué Pandas es más útil que un diccionario de listas?
* ¿Qué errores comunes se cometen al manipular DataFrames?