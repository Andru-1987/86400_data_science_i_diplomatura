# NumPy y Pandas

### 1. Configuración Inicial

```python
# Importar librerías
import numpy as np
import pandas as pd

print("Todo listo para empezar!")
```

### 2. Trabajando con NumPy Arrays

**Creación de arrays:**
```python
# Array simple
array_1d = np.array([1, 2, 3, 4, 5])
print("Array 1D:", array_1d)

# Array de ceros
ceros = np.zeros(5)
print("Array de ceros:", ceros)

# Array con valores específicos
lleno = np.full(5, 7)
print("Array lleno de 7s:", lleno)

# Array con rango
rango = np.arange(1, 11)
print("Array con rango 1-10:", rango)
```

**Arrays multidimensionales:**
```python
# Matriz 2x3
matriz = np.array([[1, 2, 3], [4, 5, 6]])
print("Matriz 2x3:")
print(matriz)

# Reshape de arrays
array_original = np.arange(1, 13)
matriz_3x4 = array_original.reshape(3, 4)
print("Matriz 3x4 después de reshape:")
print(matriz_3x4)
```

### 3. Operaciones con NumPy

```python
# Operaciones matemáticas
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print("Suma:", a + b)
print("Resta:", a - b)
print("Multiplicación:", a * b)
print("División:", b / a)

# Funciones estadísticas
numeros = np.array([2, 4, 6, 8, 10])
print("Estadísticas:")
print("Suma total:", np.sum(numeros))
print("Promedio:", np.mean(numeros))
print("Valor máximo:", np.max(numeros))
print("Valor mínimo:", np.min(numeros))
```

### 4. Introducción a Pandas

**Creando Series:**
```python
# Series desde lista
precios = [100, 200, 150, 300]
productos = ['Laptop', 'Mouse', 'Teclado', 'Monitor']

serie_precios = pd.Series(precios, index=productos)
print("Series de precios:")
print(serie_precios)
```

**Creando DataFrames:**
```python
# DataFrame manual
data = {
    'Producto': ['Laptop', 'Mouse', 'Teclado', 'Monitor'],
    'Precio': [1000, 50, 120, 300],
    'Stock': [15, 100, 45, 30]
}

df_productos = pd.DataFrame(data)
print("DataFrame de productos:")
print(df_productos)
```

### 5. Lectura de Archivos

```python
# Desde CSV (ejemplo simulado)
# En la práctica usarías: pd.read_csv('archivo.csv')
datos_ejemplo = {
    'Nombre': ['Ana', 'Carlos', 'María', 'Juan'],
    'Edad': [28, 35, 42, 29],
    'Ciudad': ['Madrid', 'Barcelona', 'Valencia', 'Sevilla']
}

df_personas = pd.DataFrame(datos_ejemplo)
print("DataFrame desde datos simulados:")
print(df_personas)
```

### 6. Operaciones Básicas con DataFrames

```python
# Información básica
print("Información del DataFrame:")
print(df_productos.info())

print("Primeras 3 filas:")
print(df_productos.head(3))

print("Estadísticas descriptivas:")
print(df_productos.describe())

# Selección de datos
print("Precios mayores a 100:")
print(df_productos[df_productos['Precio'] > 100])

# Agregar nueva columna
df_productos['Valor_Total'] = df_productos['Precio'] * df_productos['Stock']
print("DataFrame con valor total:")
print(df_productos)
```

### 7. Ejercicio Integrador

```python
# Crear dataset de estudiantes
estudiantes_data = {
    'Nombre': ['Ana García', 'Carlos López', 'María Rodríguez', 'Juan Pérez', 'Laura Martínez'],
    'Edad': [20, 22, 21, 23, 19],
    'Carrera': ['Ingeniería', 'Medicina', 'Derecho', 'Administración', 'Psicología'],
    'Calificación': [8.5, 9.2, 7.8, 8.9, 9.5]
}

df_estudiantes = pd.DataFrame(estudiantes_data)

print("Dataset de estudiantes:")
print(df_estudiantes)

# Análisis básico
print(f"Cantidad de estudiantes: {len(df_estudiantes)}")
print(f"Calificación promedio: {df_estudiantes['Calificación'].mean():.2f}")
print(f"Calificación más alta: {df_estudiantes['Calificación'].max()}")
print(f"Calificación más baja: {df_estudiantes['Calificación'].min()}")

# Filtrar estudiantes con calificación > 9
excelentes = df_estudiantes[df_estudiantes['Calificación'] > 9]
print("Estudiantes excelentes:")
print(excelentes)
```

### 8. Desafío Final

```python
# Tu turno: Crear tu propio dataset
"""
Crea un DataFrame con información de 5 productos que te gusten:
- Nombre del producto
- Precio
- Categoría
- Rating (1-5)

Luego:
1. Calcula el precio promedio
2. Filtra los productos con rating mayor a 4
3. Agrega una columna con el precio con IVA (21%)
"""
```

---
## Conceptos para check hasta acá:

### Conceptos Teóricos:
- [ ] Programación como ejecución de algoritmos
- [ ] Variables y tipos de datos
- [ ] Operadores y estructuras de control
- [ ] Funciones y modularización

### Herramientas Prácticas:
- [ ] NumPy para operaciones numéricas
- [ ] Pandas para manipulación de datos
- [ ] Creación de Series y DataFrames
- [ ] Operaciones básicas de análisis

---

## Recursos Adicionales

- Documentación oficial de Python: https://docs.python.org/3/
- Tutorial de NumPy: https://numpy.org/doc/stable/user/absolute_beginners.html
- Guía de Pandas: https://pandas.pydata.org/docs/getting_started/index.html
- Google Colab: https://colab.research.google.com/