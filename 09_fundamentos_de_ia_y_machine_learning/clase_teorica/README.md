


# Clase: Fundamentos de Evaluación de Modelos en Data Science

[Presentacion](https://docs.google.com/presentation/d/1NOfgow30Hh-h_eH2J-7zoAY_qYAZM4mo/edit?slide=id.g3641603263b_0_1001#slide=id.g3641603263b_0_1001)

## 1. Validación Cruzada (Cross-Validation)

**Objetivo:**
Evaluar el rendimiento de un modelo de manera robusta, evitando el sobreajuste y asegurando que los resultados sean generalizables a datos no vistos.

**¿Cómo funciona?**
- Se divide el dataset en k particiones (folds)
- Se entrena el modelo con k-1 particiones y se valida con la restante
- Se repite el proceso k veces, cambiando la partición de validación
- Finalmente, se promedian los resultados

**Ventajas:**
- Reduce la dependencia de una única división train/test
- Mejor estimación del rendimiento del modelo

---

## 2. Ingeniería de Características (Feature Engineering)

**Propósito:**
Mejorar la capacidad predictiva del modelo mediante la transformación, creación o selección de variables.

**Objetivos:**
- Capturar mejor la relación entre variables
- Reducir ruido y redundancia
- Facilitar el aprendizaje del modelo

**Ejemplos de técnicas:**
- Imputación de valores faltantes
- Codificación de variables categóricas
- Creación de características polinómicas o de interacción
- Normalización o estandarización

---

## 3. Detección de Overfitting y Underfitting

**Overfitting (Sobreajuste):**
- El modelo aprende demasiado los datos de entrenamiento, incluyendo el ruido
- Buen rendimiento en entrenamiento, malo en validación
- **Señales:** Alta varianza, baja generalización

**Underfitting (Subajuste):**
- El modelo es demasiado simple y no captura patrones esenciales
- Mal rendimiento tanto en entrenamiento como en validación
- **Señales:** Alto sesgo, baja complejidad

**Cómo prevenirlos:**
- Para overfitting: Regularización, más datos, validación cruzada
- Para underfitting: Modelos más complejos, más características, mejor feature engineering

---

## 4. Métricas de Evaluación

### A. Regresión

**R² (Coeficiente de Determinación):**
- Mide cuánta variabilidad de la variable objetivo es explicada por el modelo
- Rango: 0 a 1
- Fórmula: R² = 1 - (SS_res / SS_tot)

**RMSE (Raíz del Error Cuadrático Medio):**
- Penaliza más los errores grandes
- Fórmula: RMSE = √(1/n * Σ(y_i - ŷ_i)²)

**MAPE (Error Porcentual Absoluto Medio):**
- Error en términos porcentuales
- Fórmula: MAPE = (100%/n) * Σ|(y_i - ŷ_i)/y_i|

### B. Clasificación

**Matriz de Confusión:**
Tabla que muestra:
- Verdaderos Positivos (VP)
- Falsos Positivos (FP)
- Verdaderos Negativos (VN)
- Falsos Negativos (FN)

**Ejemplo:**
Supongamos un modelo que predice si un paciente tiene una enfermedad:

| Real / Predicho | Enfermo | Sano |
|-----------------|---------|------|
| Enfermo         | VP = 80 | FN = 10 |
| Sano            | FP = 5  | VN = 105 |

**Accuracy (Exactitud):**
- Proporción de predicciones correctas
- Fórmula: (VP + VN) / Total

**Precision (Precisión):**
- De los predichos como positivos, cuántos lo son
- Fórmula: VP / (VP + FP)

**Recall (Sensibilidad):**
- De los reales positivos, cuántos fueron detectados
- Fórmula: VP / (VP + FN)

**F1-Score:**
- Media armónica entre Precision y Recall
- Fórmula: F1 = 2 * (Precision * Recall) / (Precision + Recall)

---

## 5. Curva ROC y AUC

**ROC (Receiver Operating Characteristic):**
- Gráfica que muestra la tasa de verdaderos positivos (Recall) vs. la tasa de falsos positivos (1 - Especificidad) para distintos umbrales de clasificación

**AUC (Area Under the Curve):**
- Mide la capacidad del modelo para distinguir entre clases
- AUC = 1 → Clasificador perfecto
- AUC = 0.5 → Equivalente a adivinar al azar

**Interpretación:**
- Cuanto más cerca de 1, mejor es el modelo

---


# Métricas ideales para clasificación multiclase

## 1. Accuracy (Exactitud global)

- **Definición:** proporción total de predicciones correctas sobre el total de casos.
- **Fórmula:**

  ```
  Accuracy = Σ(VP_i) / N
  ```

  donde VP_i son los verdaderos positivos por clase y N el total de ejemplos.
- **Ventaja:** simple e intuitiva.
- **Limitación:** puede ser engañosa si hay **desbalance de clases**.

---

## 2. Precision, Recall y F1-Score por clase

En multiclase, se calculan **por cada clase** (considerando una clase como "positiva" y las demás como "negativas"), y luego se **promedian** según el tipo de promedio que elijas:

| Tipo de promedio | Descripción                                                               | Cuándo usarlo                                                                     |
|------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| **Macro**        | Promedia las métricas de cada clase **sin ponderar por su tamaño**.      | Si querés evaluar el rendimiento igualitario entre clases (incluso minoritarias).|
| **Weighted**     | Promedia ponderando por el número de ejemplos de cada clase.             | Si hay **desbalance de clases** y querés reflejar su impacto real.               |
| **Micro**        | Calcula métricas **globales** acumulando VP, FP y FN de todas las clases.| Si querés una medida general del desempeño.                                      |

**Ejemplo (para F1):**

```
F1_macro = (1/k) × Σ(F1_i)
```

---

## 3. Matriz de Confusión Multiclase

- Extiende la idea binaria a una matriz **k × k**, donde k es el número de clases.
- Muestra cuántas veces se predijo cada clase correctamente o se confundió con otra.
- Es ideal para identificar **patrones de confusión específicos** (por ejemplo, la clase "Gato" se confunde con "Tigre").

---

## 4. Cohen's Kappa

- Mide el grado de acuerdo entre las predicciones y las etiquetas verdaderas, **corrigiendo el acuerdo esperado por azar**.
- **Rango:** -1 a 1
  - 1 → acuerdo perfecto
  - 0 → acuerdo al azar
  - < 0 → peor que azar
- Muy útil para comparar modelos o medir consistencia en datasets desbalanceados.

---

## 5. AUC Multiclase (One-vs-Rest o One-vs-One)

- En multiclase, se calcula un **AUC por cada clase** comparándola contra las demás:
  - **One-vs-Rest (OvR):** cada clase vs el resto.
  - **One-vs-One (OvO):** promedio de todas las combinaciones de pares de clases.
- Se puede promediar usando **macro** o **weighted average**.

---

## 6. Log Loss (Cross-Entropy Loss)

- Evalúa la **probabilidad asignada** a las predicciones, penalizando más los errores de alta confianza.
- Útil si tu modelo produce **probabilidades** y no solo etiquetas.
- **Fórmula generalizada:**

  ```
  LogLoss = -(1/N) × Σ_i Σ_c [y_i,c × log(p̂_i,c)]
  ```

  donde y_i,c es 1 si el ejemplo pertenece a la clase c, y p̂_i,c la probabilidad predicha.

---

## Resumen por tipo de objetivo

| Objetivo                          | Métricas recomendadas                   |
|-----------------------------------|-----------------------------------------|
| **Evaluación general**            | Accuracy, F1-Weighted, Cohen's Kappa    |
| **Clases balanceadas**            | Macro Precision / Recall / F1           |
| **Clases desbalanceadas**         | Weighted Precision / Recall / F1, Kappa |
| **Probabilidades calibradas**     | Log Loss, AUC (OvR)                     |
| **Análisis detallado de errores** | Matriz de confusión multiclase          |

---

Los principales cambios que hice:

1. Eliminé los emojis
2. Convertí las fórmulas LaTeX a formato de código plano más legible en Markdown
3. Ajusté el espaciado en las tablas para mejor alineación
4. Usé guiones simples (-) en lugar de asteriscos (*) para las listas
5. Simplifiqué los símbolos matemáticos para que se vean bien sin renderizado LaTeX



## Resumen

- La validación cruzada y el feature engineering son esenciales para construir modelos generalizables
- Identificar overfitting/underfitting permite ajustar la complejidad del modelo
- Las métricas adecuadas dependen del problema: usar R², RMSE, MAPE para regresión; Accuracy, Precision, Recall, F1 y matriz de confusión para clasificación
- La curva ROC-AUC es clave para evaluar clasificadores binarios