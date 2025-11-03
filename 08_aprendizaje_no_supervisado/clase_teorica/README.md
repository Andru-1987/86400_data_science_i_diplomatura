### **Unidad 8: Data Science I - Clase Teórica para Principiantes**

**Objetivos de la Clase:**
*   Aplicar e interpretar modelos de regresión lineal simple y múltiple.
*   Analizar factores que influyen en fenómenos empresariales usando regresión.
*   Comprender y utilizar técnicas de codificación de variables categóricas.
*   Implementar algoritmos de clustering para identificar patrones en datos.
*   Evaluar la similitud entre activos financieros aplicando clustering.

---

### **1. Introducción a Machine Learning (Aprendizaje Automático) (10 min)**

**Teoría:**
Machine Learning (ML) es una rama de la inteligencia artificial que permite a los sistemas "aprender" de los datos sin ser programados explícitamente para cada tarea. Se puede clasificar en tres tipos principales:

*   **Aprendizaje Supervisado:** El modelo aprende a partir de datos históricos que ya contienen la respuesta correcta (etiqueta). El objetivo es predecir esa etiqueta para nuevos datos.
    *   **Ejemplo:** Tienes datos históricos de casas (tamaño, número de habitaciones) y sus precios de venta. Un modelo supervisado puede predecir el precio de una casa nueva.
*   **Aprendizaje No Supervisado:** El modelo encuentra patrones o estructuras en datos que no tienen etiquetas. No hay una "respuesta correcta" predefinida.
    *   **Ejemplo:** Tienes datos de clientes (edad, gastos, intereses) y quieres agruparlos en segmentos naturales sin saber de antemano cuáles son esos grupos.
*   **Aprendizaje por Refuerzo:** El modelo aprende mediante prueba y error, recibiendo recompensas o penalizaciones por sus acciones.
    *   **Ejemplo:** Un programa que aprende a jugar ajedrez jugando muchas partidas contra sí mismo.

**Dentro del Aprendizaje Supervisado, existen dos tipos de problemas principales:**
*   **Clasificación:** Predecir una categoría (etiqueta discreta). "¿Es este correo spam o no spam?".
*   **Regresión:** Predecir un valor numérico (etiqueta continua). "¿Cuál será el precio de esta acción mañana?".

---

### **2. Regresión Lineal: Prediciendo Valores Numéricos (20 min)**

**Teoría:**
La regresión lineal es un algoritmo de Aprendizaje Supervisado utilizado para predecir un valor numérico continuo. Su objetivo es encontrar una relación lineal entre una o más variables independientes (predictoras) y una variable dependiente (objetivo).

**a) Regresión Lineal Simple:**
*   Se usa una sola variable predictora (X) para predecir la variable objetivo (Y).
*   La fórmula del modelo es: `Y = a + b*X`
    *   `Y`: Variable que queremos predecir (ej: salario).
    *   `X`: Variable que usamos para predecir (ej: años de experiencia).
    *   `a`: Intercepto. El valor de Y cuando X es cero.
    *   `b`: Pendiente o coeficiente. Indica cuánto cambia Y por cada unidad que aumenta X.

**Ejemplo Simple:**
*   **Problema:** Predecir el salario de una persona basado en sus años de experiencia.
*   **Modelo:** `Salario = a + b * (Años de Experiencia)`
*   Si el modelo resulta ser `Salario = 30000 + 5000 * (Años de Experiencia)`, se interpreta como:
    *   Un salario base (intercepto) de 30,000 USD para alguien con 0 años de experiencia.
    *   Por cada año adicional de experiencia, el salario aumenta en promedio 5,000 USD (coeficiente).

**b) Regresión Lineal Múltiple:**
*   Extiende la regresión simple usando varias variables predictoras (X1, X2, ..., Xn).
*   La fórmula del modelo es: `Y = a + b1*X1 + b2*X2 + ... + bn*Xn`

**Ejemplo Simple:**
*   **Problema:** Predecir el salario usando años de experiencia y nivel de educación.
*   **Modelo:** `Salario = a + b1*(Experiencia) + b2*(Nivel de Educación)`
*   Esto permite aislar el efecto de cada variable. Por ejemplo, podríamos encontrar que, manteniendo constante el nivel de educación, por cada año de experiencia el salario aumenta 4,800 USD.

**Evaluación del Modelo: R-cuadrado (R²)**
*   Es una medida que indica qué porcentaje de la variación de la variable objetivo (Y) es explicada por el modelo.
*   Va de 0 a 1 (o 0% a 100%). Un R² de 0.75 significa que el 75% de la variación en Y se explica por las X.
*   **En el ejemplo de la brecha salarial:** Un R² de 0.319 (31.9%) es bajo, lo que indica que factores como la edad y el género explican solo una parte del salario; hay otras variables importantes (como el puesto de trabajo) que no se incluyeron en ese primer modelo.

---

### **3. Codificación de Variables Categóricas (10 min)**

**Teoría:**
Los modelos matemáticos trabajan con números, no con texto. Para usar variables categóricas (como "Género", "País", "Color") en un modelo, debemos convertirlas en números. Las dos técnicas principales son:

**a) One-Hot Encoding (OHE):**
*   Crea una nueva columna binaria (0 o 1) para cada categoría posible.
*   **Se usa cuando:** La variable no es ordinal (no tiene un orden inherente).
*   **Ejemplo Simple:** La variable "Color" con categorías [Rojo, Verde, Azul].
    *   Se convierte en tres columnas: `Color_Rojo`, `Color_Verde`, `Color_Azul`.
    *   Un objeto rojo se representa como [1, 0, 0].
    *   Un objeto verde se representa como [0, 1, 0].

**b) Label Encoding (LE):**
*   Asigna un número único a cada categoría (por ejemplo: Rojo=0, Verde=1, Azul=2).
*   **Se usa cuando:** La variable es ordinal (las categorías tienen un orden) o cuando hay muchas categorías y OHE generaría demasiadas columnas.
*   **Ejemplo Simple:** La variable "Tamaño" con categorías [Pequeño, Mediano, Grande].
    *   Tiene un orden claro, por lo que se puede codificar como Pequeño=0, Mediano=1, Grande=2.

---

### **4. Aprendizaje No Supervisado: Clustering (Agrupamiento) (20 min)**

**Teoría:**
El clustering tiene como objetivo encontrar grupos naturales (clústeres) en un conjunto de datos no etiquetados. Los elementos dentro de un mismo clúster son muy similares entre sí, y diferentes a los de otros clústeres.

**Tipos de Algoritmos de Clustering:**

**a) Clustering Jerárquico:**
*   Crea una estructura de árbol de clústeres (dendrograma).
*   **Enfoque Aglomerativo (de abajo hacia arriba):** Cada punto comienza en su propio clúster y se van uniendo los más similares.
*   **Ejemplo Simple:** Agrupar especies de plantas basándose en medidas de sus pétalos y sépalos. El dendrograma muestra cómo las plantas individuales se fusionan en grupos (especies).

**b) Clustering No Jerárquico (Particional):**
*   Divide los datos en un número predefinido 'k' de grupos.
*   **Algoritmo K-Means:** Es el más popular.
    *   **Pasos:**
        1.  Se eligen 'k' puntos aleatorios como centroides (el centro de cada clúster).
        2.  Se asigna cada punto al centroide más cercano.
        3.  Se recalculan los centroides como el promedio de todos los puntos del clúster.
        4.  Se repiten los pasos 2 y 3 hasta que los centroides ya no cambien.
*   **Ejemplo Simple:** Segmentación de clientes de un e-commerce en 3 grupos (k=3) basándose en su frecuencia de compra y monto gastado. El resultado podrían ser grupos como "Clientes ocasionales", "Clientes frecuentes" y "Whales" (clientes de muy alto valor).

**c) Clustering Basado en Densidad (DBSCAN):**
*   Encuentra clústeres como áreas densas de puntos, separadas por áreas vacías. Es robusto a los valores atípicos (outliers).
*   **Parámetros clave:**
    *   **eps:** La distancia máxima entre dos puntos para ser considerados vecinos.
    *   **minPts:** El número mínimo de puntos para formar un área densa (un clúster).
*   **Ejemplo Simple:** Identificar grupos de personas en una plaza. DBSCAN encontraría los grupos densos (como gente alrededor de un músico callejero) y dejaría como "ruido" a las personas que caminan solas y alejadas.

---

### **5. Resumen y Próximos Pasos (5 min)**

Hoy hemos visto los pilares fundamentales del Data Science práctico:

1.  **Regresión:** Para predecir valores numéricos (como un salario o un precio) y entender las relaciones entre variables.
2.  **Preprocesamiento:** Cómo preparar los datos, por ejemplo, codificando variables categóricas para que los modelos puedan entenderlas.
3.  **Clustering:** Para explorar datos sin etiquetas y descubrir grupos o segmentos ocultos, como clientes similares o acciones con comportamientos de precio parecidos.
