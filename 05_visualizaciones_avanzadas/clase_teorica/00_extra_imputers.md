# Criterios para Tratamiento de Missing Values

## Tabla Comparativa por Ratio de Nullidad

| Ratio de Nullidad | Criterio Principal | Estrategias Recomendadas | Consideraciones Clave |
|-------------------|-------------------|--------------------------|----------------------|
| **< 5%** | **Eliminación Segura** | - Eliminar filas/columnas<br>- Imputación simple (media, mediana, moda) | - Impacto mínimo en el tamaño de la muestra<br>- Bajo riesgo de sesgo |
| **5% - 10%** | **Imputación Simple** | - Mediana para numéricas (robusta a outliers)<br>- Moda para categóricas<br>- KNN básico | - Validar distribución de datos<br>- Considerar creación de flag de imputación |
| **10% - 20%** | **Imputación Avanzada** | - MICE (Multiple Imputation by Chained Equations)<br>- Random Forest imputation<br>- Modelos predictivos | - Analizar patrón (MCAR/MAR/MNAR)<br>- Incluir variables predictoras relevantes |
| **20% - 50%** | **Análisis de Patrón + Imputación** | - Determinar MCAR/MAR/MNAR<br>- Imputación múltiple<br>- Modelos mixtos | - Alto riesgo de sesgo<br>- Requiere validación cruzada<br>- Considerar análisis de sensibilidad |
| **> 50%** | **Evaluación Crítica** | - Eliminar la variable<br>- Tratamiento como variable categórica especial<br>- Modelos de selección | - Pérdida significativa de información<br>- Posible introducción de sesgo severo<br>- Considerar exclusión del análisis |

##  Criterio por Tipo de Patrón (MCAR/MAR/MNAR)

### **MCAR (Missing Completely At Random)**
- **Criterio**: Los valores faltantes son completamente aleatorios
- **Acción**: Imputación simple aceptable
- **Riesgo**: Bajo sesgo de imputación

### **MAR (Missing At Random)**
- **Criterio**: Los faltantes dependen de otras variables observadas
- **Acción**: Imputación usando variables predictoras
- **Riesgo**: Sesgo moderado si no se incluyen predictores correctos

### **MNAR (Missing Not At Random)**
- **Criterio**: Los faltantes dependen de valores no observados
- **Acción**: Métodos avanzados (Heckman, pattern mixture models)
- **Riesgo**: Alto sesgo potencial

---
_Un detalle importante a tener en cuenta cuando hacemos imputaciones, tenemos que tener en cuenta la correlacion con otras columnas_
