# Bitácora de prompts
Laboratorio 06: Fundamentos de Ingeniería de Prompts. 
Herramienta de IA usada: ChatGPT (o Gemini / Claude / Copilot)

## Ejercicio 2: Tokens y ventana de contexto

### Tabla de Conteo de Tokens

| Texto | Caracteres | Tokens |
| :--- | :---: | :---: |
| Los estudiantes programan en Java. | 35 | 7 |
| The students program in Java. | 30 | 6 |
| desafortunadamente | 18 | 5 |

### Observaciones de la Ventana de Contexto (Pasos 4 y 5)
* **En el mismo chat:** El asistente respondió correctamente que la aplicación se llamaba *TiendaTec* y utilizaba *Java Swing*. Esto ocurre porque los mensajes previos se mantienen almacenados y activos dentro de la **ventana de contexto** de la sesión actual.
* **En un chat nuevo:** El modelo no pudo dar la respuesta y solicitó mayores detalles. Esto demuestra que un chat nuevo inicializa la ventana de contexto completamente vacía, por lo que carece de memoria sobre interacciones previas realizadas en pestañas independientes.

---

## Ejercicio 3: Temperatura

### Tabla de Resultados del Simulador

| Temperatura | % de BiblioTec | Nombres en los 5 intentos |
| :---: | :---: | :--- |
| **0** | 100.0% | BiblioTec, BiblioTec, BiblioTec, BiblioTec, BiblioTec |
| **0.5** | 71.8% | BiblioTec, LibroYa, BiblioTec, BiblioTec, PrestaLibro |
| **1** | 47.2% | BiblioTec, PrestaLibro, LectoGo, LibroYa, BiblioTec |
| **1.8** | 24.5% | LectoGo, NubeDeTinta, PaginaLibre, LibroYa, BiblioTec |

### Análisis de la Temperatura
Al incrementar el valor de la temperatura, la distribución de probabilidad matemática se aplana (se vuelve más homogénea) entre las opciones. Esto reduce el dominio de la opción más probable y le otorga oportunidades de selección a palabras de baja frecuencia, incrementando la creatividad o variabilidad de la salida. 
El simulador **nunca inventará un nombre nuevo** ajeno a la lista porque la temperatura no añade información ni expande el conocimiento base del sistema; únicamente modifica el criterio probabilístico de muestreo sobre los tokens ya existentes internamente.

---

## Ejercicio 4: Prompt vago vs estructurado

### Tabla Comparativa de Atributos

| Criterio | Prompt vago | Prompt estructurado |
| :--- | :---: | :---: |
| ¿Menciona el objetivo del sistema? | Sí | Sí |
| ¿Menciona a los usuarios principales? | No | Sí |
| ¿Tiene exactamente 3 funcionalidades? | No (dio 5) | Sí |
| ¿Está estructurado en 3 párrafos? | No (dio 1 largo) | Sí |
| ¿Lo usaría en un informe real? | No | Sí |

---

## Ejercicio 5: Anatomía de un prompt, paso a paso

### Identificación de Componentes en el Prompt Final

| Componente | Texto de mi prompt |
| :--- | :--- |
| **Rol** | Actúa como desarrollador Java experto. |
| **Instrucción** | Crea un programa estructurado para gestionar el inventario de un negocio. |
| **Contexto** | El sistema es para controlar productos de una tienda usando una clase llamada Producto con los atributos codigo, nombre, precio y stock. |
| **Ejemplo** | Usa estrictamente este estilo para los métodos: getPrecio(), setPrecio(double precio). |
| **Formato** | Explica primero brevemente la arquitectura de la clase y luego presenta el bloque de código limpio en Java dentro de un bloque markdown. |

### Progresión de Respuestas por Nivel
* **Nivel 1:** Generó una plantilla genérica e inconexa de consola (un hola mundo estructurado).
* **Nivel 2 (+Rol):** Añadió mejores prácticas de ordenamiento técnico y comentarios propios de un programador senior.
* **Nivel 3 (+Contexto):** Dirigió el código específicamente al manejo de inventario comercial con atributos genéricos de productos.
* **Nivel 4 (+Instrucción):** El código se limitó exactamente a los atributos explícitos `codigo`, `nombre`, `precio` y `stock` requeridos.
* **Nivel 5 (+Formato):** Se ordenó la respuesta de manera limpia, colocando el marco explicativo antes de abrir el bloque de código.
* **Nivel final (+Ejemplo):** Los métodos encapsuladores respetaron fielmente la nomenclatura sintáctica dada en la plantilla del ejemplo.

---

## Ejercicio 6: Del prompt básico al profesional (e iterar)

### Evaluación del Prompt Profesional Inicial

| Qué revisar | Cumple (Sí / No) |
| :--- | :---: |
| ¿Está escrito en Java y usa Swing? | Sí |
| ¿Pide correo y contraseña? | Sí |
| ¿Explica el funcionamiento antes o después del código? | Sí |
| ¿El código está organizado en clases? | Sí |
| ¿Valida los datos que ingresa el usuario? | No (aceptaba cualquier entrada vacía) |

### Registro de Prompts e Iteración (Bloque de Código)
```text
PROMPT PROFESIONAL INICIAL:
Actua como desarrollador Java. Crea un ejemplo de login para una aplicacion de escritorio utilizando Swing. El usuario debe ingresar correo y contrasena. Explica brevemente el funcionamiento y presenta el codigo organizado por clases.

PROMPT DE MEJORA (ITERACIÓN):
Mejora el codigo anterior con estas restricciones: no uses librerias externas, valida que el correo contenga @ y que la contrasena tenga al menos 8 caracteres, y muestra los mensajes con JOptionPane.
```
