# Clase Teórica – Manipulación de Datos con Pandas y Visualización

[Presentacion](https://docs.google.com/presentation/d/1wwQ64aeuK1jEK95uZXtsHYvTILAT4P15/edit?slide=id.g374242ea485_0_1163#slide=id.g374242ea485_0_1163)

## Objetivos 

* _Repaso_: Conocer estructuras de datos en Pandas: `Series` y `DataFrame`.
* Aggregacion: Aprender a seleccionar, agrupar y agregar datos.
* Trabajar con strings y fechas.
* Generar visualizaciones básicas en Python con **Matplotlib** y **Seaborn**.

---

## 1. Introducción a Pandas

### Pandas Series

Una **Serie** es un arreglo unidimensional con índice.

```python
import pandas as pd

numeros = range(50, 70, 2)
serie = pd.Series(numeros, name="Numeros pares")
print(serie.head())

print("Elemento en la posición 2:", serie[2])
```

Características principales: índice, valores y nombre.

---

### Pandas DataFrame

Un **DataFrame** es una tabla (2D) con filas y columnas.

```python
import numpy as np

ajedrez = np.arange(1, 65).reshape(8, 8)
df_ajedrez = pd.DataFrame(
    ajedrez,
    columns=range(1, 9),
    index=list("ABCDEFGH")
)
print(df_ajedrez)
```

Es una generalización de las Series.

---

## 2. Selección y Agregación de Datos

### Selección

```python
# Creamos un DataFrame simple
df = pd.DataFrame({
    "Nombre": ["Ana", "Luis", "Carla", "Pedro"],
    "Edad": [23, 35, 29, 40],
    "Ciudad": ["CABA", "Mendoza", "Córdoba", "CABA"]
})

print(df["Nombre"])         # Columna
print(df.loc[0])            # Fila por etiqueta
print(df.iloc[2])           # Fila por posición
```

---

### Agregaciones

```python
print("Edad promedio:", df["Edad"].mean())
print("Edad máxima:", df["Edad"].max())
```

---

### GroupBy

```python
agrupado = df.groupby("Ciudad")["Edad"].mean()
print(agrupado)
```

---

## 3. Operaciones con Strings y Fechas

### Strings

```python
presidentes = pd.Series(["George Washington", "John Adams", "Thomas Jefferson"])
print(presidentes.str.upper())
print(presidentes.str.len())
print(presidentes.str.split(" "))
```

---

### Fechas

```python
fechas = pd.to_datetime(["1789-04-30", "1797-03-04", "1801-03-04"])
serie_presidentes = pd.Series(presidentes.values, index=fechas)
print(serie_presidentes)
```

---

## 4. Visualizaciones con Matplotlib y Seaborn

### Gráfico de Líneas

```python
import matplotlib.pyplot as plt

ventas = [10, 15, 20, 25, 18, 30]
meses = ["Ene", "Feb", "Mar", "Abr", "May", "Jun"]

fig, ax = plt.subplots()
ax.plot(meses, ventas, marker="o")
ax.set_title("Ventas Mensuales")
ax.set_xlabel("Mes")
ax.set_ylabel("Ventas")
plt.show()
```

---

### Gráfico de Dispersión

```python
import numpy as np

np.random.seed(42)
x = np.random.randint(140, 200, 30)  # altura
y = np.random.randint(40, 90, 30)    # peso

fig, ax = plt.subplots()
ax.scatter(x, y, alpha=0.6)
ax.set_title("Relación Altura vs Peso")
ax.set_xlabel("Altura (cm)")
ax.set_ylabel("Peso (kg)")
plt.show()
```

---

### Histograma

```python
fig, ax = plt.subplots()
ax.hist(y, bins=8, color="skyblue", edgecolor="black")
ax.set_title("Distribución de Pesos")
ax.set_xlabel("Peso (kg)")
ax.set_ylabel("Frecuencia")
plt.show()
```

---

### Boxplot con Seaborn

```python
import seaborn as sns

sns.boxplot(x=df["Ciudad"], y=df["Edad"])
plt.title("Distribución de edades por ciudad")
plt.show()
```

---

## Cierre

* **Pandas** permite manipular grandes volúmenes de datos de forma sencilla.
* **Matplotlib y Seaborn** son esenciales para visualizar y comunicar resultados.

* El flujo clásico de trabajo:

  1. Leer dataset
  2. Limpiar/transformar
  3. Analizar
  4. Visualizar
