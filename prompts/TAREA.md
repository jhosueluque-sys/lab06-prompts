# Tarea: Mi prompt profesional

## Funcionalidad elegida
Sistema de consola en Java para el cálculo del promedio ponderado de notas de un estudiante.

## Version 1: prompt basico
```text
Hazme un código para calcular notas en Java.
```
*   **Qué cambió y por qué:** Es la petición inicial y vaga. La IA asume cualquier fórmula matemática arbitraria, no realiza validaciones de datos y entrega una estructura de código genérica.

## Version 2
```text
Crea un programa en Java por consola para calcular el promedio ponderado de 4 notas con pesos de 30%, 40%, 15% y 15%.
```
*   **Qué cambió y por qué:** Se añadió el contexto del entorno (consola) y las instrucciones matemáticas específicas (4 notas con sus porcentajes). La IA mejoró la precisión del cálculo, pero el código sigue aceptando notas inválidas (como números negativos) y la estructura de la clase es impredecible.

## Version 3: prompt final
```text
Actúa como desarrollador Java Senior y crea un programa de consola que valide que 4 notas estén entre 0 y 20, calcule su promedio ponderado (Laboratorios 30%, Proyectos 40%, Parcial 15%, Final 15%) sin usar librerías externas, y presente el código estructurado en la clase "CalculadoraNotas" junto a una breve explicación.
```
*   **Qué cambió y por qué:** Se integraron los cinco componentes esenciales del laboratorio en una sola línea. Se asignó un rol profesional, restricciones estrictas de seguridad (validar rangos entre 0 y 20 sin dependencias externas) y un formato de salida definido. El resultado es un código robusto, ordenado y limpio.

## Componentes del prompt final

| Componente | Texto de mi prompt |
| :--- | :--- |
| **Rol** | Actúa como desarrollador Java Senior |
| **Instrucción** | crea un programa de consola que valide que 4 notas estén entre 0 y 20, calcule su promedio ponderado |
| **Contexto** | (Laboratorios 30%, Proyectos 40%, Parcial 15%, Final 15%) sin usar librerías externas |
| **Ejemplo** | *[En este prompt de una sola oración, el ejemplo queda implícito en la regla matemática de los porcentajes]* |
| **Formato** | y presente el código estructurado en la clase "CalculadoraNotas" junto a una breve explicación. |

## Evaluacion del resultado

| Qué revisar | Cumple (Sí / No) |
| :--- | :--- |
| ¿Está escrito en Java puro y se ejecuta por consola? | Sí |
| ¿Aplica con exactitud los porcentajes solicitados (30%, 40%, 15%, 15%)? | Sí |
| ¿Garantiza mediante validaciones que las notas estén entre 0 y 20? | Sí |
| ¿La clase generada se llama exactamente "CalculadoraNotas"? | Sí |

## Errores que evite

1.  **Ser demasiado general:** Lo evité pasando de la v1 (*"Hazme un código..."*) a la v3, donde delimité con exactitud las variables del negocio informándole a la IA qué datos procesar y bajo qué entorno.
2.  **Asumir información no proporcionada:** Al principio, la IA habría inventado criterios de aprobación o rangos de notas estándar (como de 0 a 100). Lo evité definiendo explícitamente el sistema de calificación peruano (de 0 a 20) y los pesos de Tecsup.
