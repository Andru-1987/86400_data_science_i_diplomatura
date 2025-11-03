# Clase 07 Pracica ML

[PRESENTACION](https://docs.google.com/presentation/d/1Q-D9XF9pfGWliz__2bFKoT7v8q3ey6Fp/edit?slide=id.p50#slide=id.p50)

### **Parte 1: Resumen y Estructura de la Clase**

**Objetivos de la Clase:**
- Comprender qué es un modelo analítico y su diferencia con los modelos numéricos.
- Introducir el concepto de Machine Learning (ML) y sus aplicaciones.
- Implementar y visualizar algoritmos de clasificación supervisada.
- Aplicar modelos de regresión en datos financieros.
- Experimentar con el algoritmo KNN y evaluar el impacto del parámetro \( k \).

#### **1.1. ¿Qué es un Modelo Analítico?**
- Un modelo es una **representación simplificada de una idea o proceso**.
- Siempre tiene un margen de error.
- En ciencia de datos, los modelos analíticos se construyen usando técnicas de ML.

**Tipos de Modelos:**
- **Analíticos:** Soluciones matemáticas en forma cerrada.
- **Numéricos:** Resuelven ecuaciones mediante métodos iterativos (ej: diferencias finitas).

---

#### **1.2. Machine Learning (ML)**
- Es una rama de la inteligencia artificial que permite a las máquinas **aprender de los datos** sin ser programadas explícitamente.

**Aplicaciones Comunes:**
- Vehículos autónomos.
- Sistemas de recomendación (Amazon, Netflix).
- Detección de fraudes.
- Procesamiento de lenguaje natural.

---

#### **1.3. Aprendizaje Supervisado**
- Se usa cuando tenemos datos **etiquetados**.
- Objetivo: Predecir una salida a partir de entradas conocidas.

**Algoritmos Comunes:**
- Árboles de Decisión.
- Regresión Logística.
- K-Nearest Neighbors (KNN).
- Support Vector Machines (SVM), Random Forest, etc.

---

#### **1.4. Tipos de Modelos Analíticos en Ciencia de Datos**
- Clasificación.
- Clustering.
- Pronósticos.
- Detección de anomalías.
- Series de tiempo.

---

### **Parte 2: Modelos de Machine Learning con Ejemplos**

---

#### **2.1. Árboles de Decisión**
**Breve Explicación:**
- Divide los datos en base a reglas jerárquicas.
- Fácil de interpretar y visualizar.

**Ejemplo con Dataset Iris:**
```python
from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.datasets import load_iris
import matplotlib.pyplot as plt

iris = load_iris()
X, y = iris.data, iris.target
clf = DecisionTreeClassifier(random_state=1234)
clf.fit(X, y)

plt.figure(figsize=(12,8))
plot_tree(clf, feature_names=iris.feature_names, class_names=iris.target_names, filled=True)
plt.show()
```

---

#### **2.2. Regresión Logística**
**Breve Explicación:**
- Usado para clasificación binaria.
- Output: probabilidad entre 0 y 1.

**Ejemplo con Dataset de Cáncer de Mama:**
```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import confusion_matrix, accuracy_score
import seaborn as sns

X, y = load_breast_cancer(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)

model = LogisticRegression(max_iter=10000)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
sns.heatmap(confusion_matrix(y_test, y_pred), annot=True, fmt='d')
plt.show()
```

---

#### **2.3. K-Nearest Neighbors (KNN)**
**Breve Explicación:**
- Clasifica en función de los \( k \) ejemplos más cercanos en el espacio de características.
- Sensible a la elección de \( k \) y a la escala de los datos.

**Ejemplo con Datos Sintéticos:**
```python
from sklearn.neighbors import KNeighborsClassifier
from mlxtend.plotting import plot_decision_regions

def knn_comparison(data, k):
    X = data[['X','Y']].values
    y = data['class'].astype(int).values
    clf = KNeighborsClassifier(n_neighbors=k)
    clf.fit(X, y)
    plot_decision_regions(X, y, clf=clf, legend=2)
    plt.title(f'KNN with k={k}')
    plt.show()

data = pd.read_csv('ushape.csv')
knn_comparison(data, k=5)
```

---

### **Parte 3: Tabla Comparativa de Algoritmos**

| Algoritmo          | Outliers | Missing Values | Skewness | Variables Categóricas | Rendimiento/Computo |
|---------------------|----------|----------------|----------|-----------------------|---------------------|
| **Árbol de Decisión** | Sensible | Robustos       | Robustos | Sí (one-hot)          | Rápido, bajo costo  |
| **Regresión Logística** | Sensible | Sensible       | Sensible | Sí (one-hot)          | Muy rápido          |
| **KNN**             | Sensible | Sensible       | Sensible | Sensible (escalar)    | Lento con muchos datos |

---

**Consideraciones Adicionales:**

- **Árboles de Decisión:**
  - Ventajas: No requieren escalado, manejan bien variables categóricas.
  - Desventajas: Propensos a overfitting si no se podan.

- **Regresión Logística:**
  - Ventajas: Rápidos, interpretables.
  - Desventajas: Asume relación lineal, sensible a outliers.

- **KNN:**
  - Ventajas: Simple, no asume distribución de datos.
  - Desventajas: Costoso computacionalmente, sensible a la escala.

---

**Conclusión:**
Cada algoritmo tiene sus fortalezas y debilidad. La elección debe basarse en la naturaleza de los datos, el contexto del problema y los recursos computacionales disponibles. Se recomienda experimentar con varios modelos y validar su desempeño mediante métricas adecuadas.