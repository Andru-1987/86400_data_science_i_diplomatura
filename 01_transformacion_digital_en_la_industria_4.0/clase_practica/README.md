# Clases de Aprendizaje Automático: Supervisado vs No Supervisado

## Introducción

Hoy vamos a entender la diferencia fundamental entre dos tipos de aprendizaje automático que van a usar constantemente en el mundo de los datos.

## Aprendizaje Supervisado

**¿Cómo lo reconozco?**
- Los datos vienen con etiquetas (como etiquetas en la ropa)
- Algoritmo: "Esto es una manzana", "Esto es una naranja"
- Es como tener un profesor que te dice las respuestas

**¿Para qué sirve?**
- Predecir categorías (clasificación)
- Predecir valores numéricos (regresión)
- Ejemplo: predecir si un cliente se va o se queda

## Aprendizaje No Supervisado

**¿Cómo lo reconozco?**
- Los datos NO tienen etiquetas
- El algoritmo tiene que encontrar patrones por sí solo
- Es como darle un montón de fotos sin nombre y que encuentre grupos

**¿Para qué sirve?**
- Encontrar grupos naturales en los datos (clustering)
- Detectar anomalías o cosas raras
- Reducir dimensiones (simplificar datos complejos)

## Caso Práctico: La Heladería de Pedro

**Situación**: Pedro tiene una heladería y quiere optimizar su stock usando datos históricos.

**Reflexión**:
- Los datos pueden mostrar patrones estacionales (más helado en verano)
- Puede evitar quedarse sin stock o tener demasiado
- La empresa está empezando a usar datos sistemáticamente

**¿Qué tipo de aprendizaje usaría?**
- Para predecir ventas específicas: Supervisado (porque tiene datos históricos con fechas y cantidades)
- Para encontrar grupos de clientes: No Supervisado (clustering para segmentar clientes)

## Cómo Empezar: Consultas Básicas

Cuando trabajen con datos (como archivos CSV), van a hacer:

```sql
-- Consulta típica para entender los datos
SELECT * FROM tabla_heladeria LIMIT 10;

-- Ver ventas por mes
SELECT mes, SUM(ventas) as total_ventas
FROM ventas_heladeria
GROUP BY mes
ORDER BY total_ventas DESC;
```

## Consejo para Principiantes

- **Supervisado**: Cuando ya saben qué quieren predecir y tienen ejemplos etiquetados
- **No Supervisado**: Cuando quieren explorar los datos y encontrar patrones ocultos

Ambos approaches son complementarios y van a usar ambos según el problema que necesiten resolver.

