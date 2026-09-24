# Tarea: Mi prompt profesional

## Funcionalidad elegida
Una función que calcula el promedio final ponderado de un estudiante a partir de sus notas parciales y los pesos de cada evaluación.

## Version 1: prompt basico
```text
Hazme un programa que calcule el promedio de notas.
```
**Qué obtuve:** un script genérico que promedia una lista de números simples (promedio aritmético), sin considerar pesos ni contexto de un curso. No sabía en qué lenguaje lo quería ni qué formato de entrada usar.

## Version 2
```text
Crea una función en Python que calcule el promedio ponderado de notas
de un estudiante. Recibe un diccionario con el nombre de cada evaluación
y su nota, y otro diccionario con el peso (%) de cada evaluación.
Debe devolver el promedio final redondeado a dos decimales.
```
**Qué cambié:** agregué el lenguaje (Python), el formato exacto de los datos de entrada (dos diccionarios) y el formato de salida (redondeado a dos decimales).
**Por qué:** en la v1 el modelo tuvo que "adivinar" la estructura de datos, y adivinó mal.
**Qué mejoró:** ahora el código sí calculaba un promedio ponderado real y usaba los nombres de variables que yo esperaba, pero no manejaba errores (pesos que no suman 100%, evaluación sin nota) ni traía docstring ni ejemplo de uso.

## Version 3: prompt final
```text
Rol: Eres un desarrollador backend con experiencia en Python, encargado
de construir módulos para un sistema académico.

Instrucción: Escribe una función llamada calcular_promedio_final que
reciba las notas y los pesos de las evaluaciones de un estudiante y
devuelva su promedio final ponderado.

Contexto: La función formará parte de un sistema de gestión académica
de un instituto técnico. Cada curso tiene entre 3 y 6 evaluaciones,
cada una con un peso porcentual, y todos los pesos de un curso suman
100%.

Ejemplo de entrada:
notas = {"practica1": 14, "practica2": 16, "examen_final": 12}
pesos = {"practica1": 30, "practica2": 30, "examen_final": 40}

Ejemplo de salida esperada:
13.4

Formato: Devuelve solo el código Python, con type hints y un docstring
breve explicando parámetros y retorno. No incluyas explicaciones fuera
del código.

Restricción: No uses librerías externas, solo Python estándar.
```
**Qué cambié:** incorporé los cinco componentes completos (rol, instrucción, contexto, ejemplos y formato) y agregué una restricción explícita.
**Por qué:** quería que el modelo entendiera el propósito del código dentro de un sistema real (contexto), viera un caso concreto de entrada/salida (ejemplos) y supiera exactamente qué debía y no debía incluir en la respuesta (formato y restricción).
**Qué mejoró:** el resultado final incluyó validación de que los pesos sumen 100%, manejo del caso de pesos faltantes, docstring completo, type hints, y no trajo texto sobrante fuera del bloque de código — justo lo que pedí.

## Componentes del prompt final

| Componente | Fragmento del prompt |
|---|---|
| Rol | "Eres un desarrollador backend con experiencia en Python..." |
| Instrucción | "Escribe una función llamada calcular_promedio_final que reciba..." |
| Contexto | "La función formará parte de un sistema de gestión académica..." |
| Ejemplos | Bloque de entrada/salida con `notas`, `pesos` y resultado `13.4` |
| Formato | "Devuelve solo el código Python, con type hints y un docstring breve..." |

## Evaluacion del resultado

| Criterio | Cumplido |
|---|---|
| El código calcula correctamente el promedio ponderado | Sí |
| Incluye docstring y type hints | Sí |
| Maneja el caso de pesos que no suman 100% | Sí |
| No usa librerías externas | Sí |
| No incluye texto explicativo fuera del código | Sí |

## Errores que evite
1. **Ser demasiado general:** en la v1 el prompt no especificaba lenguaje ni estructura de datos, lo que generó una solución genérica e inútil. En la v3 detallé exactamente el nombre de la función, los parámetros y el tipo de dato esperado.
2. **No indicar el formato:** en la v2 no dije cómo debía verse la respuesta, y el modelo agregó explicaciones y comentarios extra que no necesitaba. En la v3 especifiqué "solo código, con type hints y docstring", eliminando ese ruido.