# Fundamentos de Python para Data Science

## Conceptos Fundamentales

### 1. ¿Qué es la Programación?

La programación es la forma de ejecutar algoritmos - secuencias de pasos que llevan a un resultado. Como una receta de cocina, si seguimos los pasos correctamente, obtenemos el resultado esperado.

**Ejemplo de algoritmo:**
```
1. Precalentar el horno a 180°C
2. Mezclar harina, huevos y azúcar
3. Hornear por 30 minutos
4. Resultado: Un pastel!
```

### 2. Python como Lenguaje para Data Science

Python es el lenguaje Open Source más solicitado en Data Science porque:
- Es interpretado (ejecuta código línea por línea)
- Tiene sintaxis clara y fácil de aprender
- Cuenta con librerías especializadas (Pandas, NumPy, Scikit-learn)
- Gran comunidad de apoyo

### 3. Componentes de Python

| Componente | Función | Ejemplo |
|------------|---------|---------|
| Intérprete | Traduce código a binario | Python 3.9 |
| IDE | Entorno de desarrollo | Jupyter Notebook |
| Paquetes | Funciones pre-armadas | Pandas, NumPy |

### 4. Variables y Tipos de Datos

**Variables:** Contenedores para almacenar información.

```python
# Ejemplos de variables
nombre = "Ana"           # str - texto
edad = 28                # int - número entero
altura = 1.65            # float - número decimal
es_estudiante = True     # bool - verdadero/falso
```

**Tipos de datos principales:**
- Simples: int, float, bool, str, NoneType
- Estructurados: list, tuple, dict, set

### 5. Operadores en Python

**Operadores aritméticos:**
```python
a + b    # Suma
a - b    # Resta  
a * b    # Multiplicación
a / b    # División
a // b   # División entera
a % b    # Módulo (resto)
a ** b   # Exponenciación
```

**Operadores de comparación:**
```python
a == b   # Igual a
a != b   # Distinto de
a < b    # Menor que
a > b    # Mayor que
a <= b   # Menor o igual que
a >= b   # Mayor o igual que
```

### 6. Estructuras de Control

**Condicional IF:**
```python
edad = 20
if edad >= 18:
    print("Es mayor de edad")
else:
    print("Es menor de edad")
```

**Bucle FOR:**
```python
# Imprimir números del 1 al 5
for i in range(1, 6):
    print(i)
```

**Bucle WHILE:**
```python
# Contador hasta 5
contador = 1
while contador <= 5:
    print(contador)
    contador += 1
```

### 7. Funciones

**Estructura básica:**
```python
def nombre_funcion(argumentos):
    # Código de la función
    return resultado
```

**Ejemplo práctico:**
```python
def calcular_iva(precio):
    iva = precio * 0.21
    total = precio + iva
    return total

# Usar la función
precio_final = calcular_iva(1000)
print(f"Precio final: ${precio_final}")
```

### 8. Entornos de Trabajo

**Jupyter Notebooks:** Ideal para Data Science porque:
- Permite ejecutar código en celdas independientes
- Combina código, texto y visualizaciones
- Fácil de compartir y colaborar

**Google Colab:** Versión cloud de Jupyter con:
- Acceso gratuito a GPUs
- No requiere instalación
- Almacenamiento en Google Drive
