# Bitácora de técnicas avanzadas
Laboratorio 07: Técnicas Avanzadas de Prompting.
Herramienta de IA usada: Gemini

## Ejercicio 2: Zero-shot, one-shot y few-shot
| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Sí/No) |
|------|-----------------|-------------------------|------------------------------------|
| Zero-shot | 5/5 | Lista numerada con explicaciones entre paréntesis | No |
| One-shot | 5/5 | Lista numerada solo con la etiqueta | Sí |
| Few-shot | 5/5 | Formato estricto "Texto" -> Etiqueta | Sí |

## Ejercicio 3: Chain of Thought 
| Enfoque del Prompt | Respuesta Final | ¿Desglosó Cálculos? | ¿Resultado Correcto? |
| :--- | :---: | :---: | :---: |
| *Directo (Sin Chain of Thought)* | S/ 318.60 | No | Sí |
| *Paso a Paso (Con Chain of Thought)* | Muestra: Subtotal (S/ 120 \times 0.75 = S/ 90), IGV (S/ 90 \times 1.18 = S/ 106.20) y Total (S/ 106.20 \times 3 = S/ 318.60) | Sí | Sí |

## Ejercicio 4: Role prompting 
| Versión | Vocabulario (sencillo/técnico) | Usa ejemplos o código | A quién le sirve más |
|---------|--------------------------------|-----------------------|----------------------|
| **Sin Rol** | General / Neutro | Concepto teórico breve sin ejemplos complejos | Público general o personas sin conocimientos previos |
| **Rol Docente** | Sencillo, accesible y pedagógico | Analogías de la vida cotidiana y ejemplos paso a paso | Estudiantes, principiantes o aprendices |
| **Rol Senior** | Altamente técnico (terminología de arquitectura y memoria) | Ejemplos prácticos con bloques de código fuente | Desarrolladores, ingenieros y compañeros de equipo |

## Ejercicio 5: Descomposicion 
* *Fase 1 (Requerimientos):* Definición de los 5 pilares funcionales (inventario, alertas, stock mínimo, categorías y reportes).
* *Fase 2 (Arquitectura):* Modelado UML/Clases de las entidades Producto, Inventario y Categoria con tipos de datos definidos.
* *Fase 3 (Implementación):* Generación del código fuente POO en Java de la clase Producto incluyendo encapsulamiento completo.
* *Fase 4 (Optimización):* Incorporación de mejoras defensivas (manejo de BigDecimal para montos, validaciones numéricas e instanciación de toString()).

## Ejercicio 6: Prompt estructurado y autocritica
### Prompts utilizados

**1. Prompt estructurado:**
```text
<rol>Actua como analista de pruebas de software.</rol> 
<contexto>Login web con correo y contrasena. La cuenta se bloquea despues de 3 intentos fallidos.</contexto> 
<tarea>Piensa paso a paso que puede fallar y escribe 6 casos de prueba.</tarea> 
<formato>Tabla con las columnas: ID, escenario, datos de entrada, resultado esperado.</formato>
``` 
| Qué revisar | Cumple (Sí / No) |
|-------------|------------------|
| ¿Tiene las 4 columnas pedidas? | Sí |
| ¿Incluye el bloqueo después de 3 intentos? | Sí |
| ¿Incluye casos con campos vacíos? | Sí |
| ¿Indica qué casos agregó en la autocrítica? | Sí |
| ¿Hay algún caso repetido o que no tenga sentido? | No |
