# Tarea: Mi prompt avanzado 
## Tarea elegida 
Generación y documentación de un conjunto completo de casos de prueba (funcionales, de seguridad y de valores límite) para el módulo de registro de nuevos usuarios de una plataforma web de comercio electrónico.
## Version 1: prompt basico 
**Prompt:** Dame casos de prueba para un registro de usuarios.
```text
Técnica agregada:Zero-shot
Por qué: Es la primera interacción intuitiva que un usuario realiza sin restricciones.

Qué mejoró en la respuesta: Entregó una lista genérica y desordenada de puntos. Faltaron criterios de aceptación claros, delimitación de campos, formatos de entrada y casos bordes de seguridad.
```
## Version 2 
**Prompt:** Actúa como QA Lead Senior. Diseña casos de prueba para el módulo de registro de usuarios que requiere email, contraseña y fecha de nacimiento. Muestra la respuesta en una tabla con las columnas: ID, Escenario, Datos de Entrada y Resultado Esperado.
```text
Técnica agregada: Role prompting y Definición de formato (Tabla).

Por qué: Para elevar el nivel técnico del vocabulario utilizado por la IA y forzar una presentación limpia y legible.

Qué mejoró en la respuesta: Adoptó una perspectiva profesional de control de calidad y organizó los datos en una tabla legible. Sin embargo, los escenarios seguían siendo muy básicos (happy path) y omitió escenarios límite como caracteres especiales o vulnerabilidades de inyección.
```
## Version 3: prompt final 
**Prompt** : 

<rol>Actúa como QA Lead Automation Senior especializado en seguridad e interfaces web.</rol>

<contexto>
Formulario de registro de usuarios de un e-commerce con los siguientes campos y reglas:
- Email (único, formato válido).
- Contraseña (mínimo 8 caracteres, al menos un número y un símbolo).
- Fecha de Nacimiento (usuario debe ser mayor de 18 años).
</contexto>

<instruccion>
Piensa paso a paso en los escenarios de prueba funcionales, de seguridad y de valores límite (Chain of Thought). Diseña una matriz inicial de 5 casos de prueba siguiendo estrictamente la estructura del ejemplo provisto.
</instruccion>

<ejemplos>
| ID | Escenario | Datos de Entrada | Resultado Esperado |
| TC-01 | Email con formato inválido | user@domain | Mensaje de error: "Formato de correo no válido" |
</ejemplos>

<autocritica>
Posteriormente, revisa si tu tabla incluye pruebas de inyección SQL básica o campos con espacios en blanco al inicio/final. Agrega los casos faltantes a la matriz e indícalos explícitamente al final.
</autocritica>
## Tecnicas usadas en el prompt final 
## Evaluacion del resultado 
## Por que elegi estas tecnicas

```text
Técnica agregada: Prompt Estructurado (etiquetas XML), Few-shot, Chain of Thought y Autocrítica.

Por qué: Para evitar ambigüedades, obligar al modelo a razonar excepciones no evidentes, estandarizar la sintaxis de salida e incentivar un segundo filtro de calidad automático.

Qué mejoró en la respuesta: Logró precisión absoluta en los datos, estandarizó las columnas sin texto introductorio innecesario, cubrió el cálculo de mayoría de edad (18 años) e identificó por sí sola la necesidad de agregar pruebas de seguridad y espacios en blanco.
```

## Técnicas usadas en el prompt final

| Parte del prompt final | Técnica correspondiente |
|------------------------|-------------------------|
| `<rol>Actúa como QA Lead Automation Senior...</rol>` | **Role prompting (Rol específico)** |
| `<rol>`, `<contexto>`, `<instruccion>`, `<ejemplos>`, `<autocritica>` | **Prompt estructurado (Etiquetas separadoras)** |
| `Piensa paso a paso en los escenarios...` | **Chain of Thought (Cadena de pensamiento)** |
| `<ejemplos>\| ID \| Escenario \|...</ejemplos>` | **Few-shot (Ejemplo de formato delimitado)** |
| `<autocritica>Posteriormente, revisa si tu tabla incluye...</autocritica>` | **Autocrítica (Filtro de auto-revisión)** |

## Evaluación del resultado

| Criterio de evaluación | Cumple (Sí / No) |
|------------------------|------------------|
| ¿Adoptó un rol específico de QA Senior y un lenguaje profesional? | Sí |
| ¿Respetó estrictamente la estructura de tabla solicitada? | Sí |
| ¿Identificó escenarios de valores límite, validaciones de edad y seguridad? | Sí |
| ¿Ejecutó el mensaje de autocrítica agregando e identificando los casos faltantes? | Sí |

## Por que elegi estas tecnicas
Elegí Role Prompting,Prompt Estructurado, Few-shot,Chain of Thought y Autocrítica debido a que el aseguramiento de calidad (QA) exige máxima precisión. Por un lado, asignar un rol específico orienta el criterio técnico hacia la seguridad e interfaz, mientras que la estructura XML y el few-shot eliminan redundancias para generar una tabla directamente exportable a herramientas como Jira. Por otro lado, la cadena de pensamiento obliga al modelo a evaluar las reglas de negocio paso a paso antes de listar los escenarios. Finalmente, la autocrítica funciona como un filtro preventivo para detectar y corregir casos límite o vulnerabilidades omitidas inicialmente.