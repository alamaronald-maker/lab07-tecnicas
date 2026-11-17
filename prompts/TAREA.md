
# Tarea: Mi prompt avanzado

## Tarea elegida

Generación de casos de prueba para un formulario de registro de usuarios de una aplicación web.

El objetivo es generar casos de prueba que permitan comprobar el funcionamiento del formulario, identificar errores de validación y verificar la seguridad de los datos ingresados.

## Versión 1: Prompt básico

**Prompt utilizado:**

```text
Genera casos de prueba para un formulario de registro de usuarios de una aplicación web.

Incluye escenarios positivos, negativos, validación de datos, seguridad y usabilidad.

Para cada caso indica su nombre, los datos de entrada y el resultado esperado.
```

**Técnica utilizada:** Zero-shot prompting.

**¿Por qué se utilizó?**

Se comenzó con una instrucción básica, sin proporcionar ejemplos ni asignar un rol específico a la inteligencia artificial.

**Resultado obtenido:**

La IA generó 40 casos de prueba organizados en diferentes categorías: funcionales, validación de datos, seguridad y usabilidad.

**Observación:**

La respuesta presentó una cobertura amplia de escenarios, pero algunos casos necesitaban mayor precisión en sus datos de entrada y resultados esperados.

## Versión 2

**Prompt utilizado:**

```text
Actúa como un ingeniero de QA especializado en pruebas de aplicaciones web.

Contexto:
Necesito probar un formulario de registro de usuarios que contiene nombres, apellidos, correo electrónico, nombre de usuario, contraseña y confirmación de contraseña.

Tarea:
Genera 15 casos de prueba positivos y negativos para verificar el funcionamiento del formulario.

Condiciones:
- Incluye campos obligatorios vacíos.
- Valida formatos de correo electrónico.
- Comprueba contraseñas incorrectas y que no coinciden.
- Incluye correos y usuarios duplicados.
- Evita repetir escenarios.

Formato:
Presenta los resultados en una tabla con cuatro columnas:
ID, nombre del caso, datos de entrada y resultado esperado.
```

**Técnicas agregadas:**

- Role prompting.
- Prompt estructurado.

**¿Por qué se agregaron?**

Se asignó el rol de ingeniero de QA para orientar la respuesta hacia las pruebas de software. También se organizaron las instrucciones en contexto, tarea, condiciones y formato para obtener resultados más claros.

**Resultado obtenido:**

La IA generó 15 casos de prueba organizados en cuatro columnas, incluyendo escenarios positivos, negativos, validaciones de campos y datos duplicados.

**¿Qué mejoró en la respuesta?**

La respuesta presentó una estructura uniforme, una cantidad definida de casos y resultados esperados más específicos que en la primera versión.

## Versión 3: Prompt final

**Prompt utilizado:**

```text
Actúa como un ingeniero de QA especializado en pruebas funcionales de aplicaciones web.

Contexto:
Debes evaluar un formulario de registro de usuarios que contiene los siguientes campos: nombres, apellidos, correo electrónico, nombre de usuario, contraseña y confirmación de contraseña.

Objetivo:
Diseñar 15 casos de prueba que permitan verificar el funcionamiento del formulario, incluyendo escenarios positivos y negativos.

Desarrolla la tarea por etapas:

1. Identifica las categorías de validación necesarias: campos obligatorios, formato del correo, contraseñas, confirmación de contraseña y datos duplicados.
2. Diseña casos positivos y negativos, evitando escenarios repetidos.
3. Incluye datos de entrada concretos y resultados esperados que puedan verificarse.
4. Revisa críticamente los casos generados: detecta duplicaciones, resultados ambiguos o reglas no especificadas.
5. Ajusta los casos identificados y presenta la versión final.

Ejemplo del formato esperado:

- ID: CP-001
- Nombre: Registro exitoso
- Datos de entrada: Todos los campos completos con datos válidos y correo no registrado.
- Resultado esperado: El sistema permite registrar al usuario y muestra una confirmación.

Condiciones:
- Genera exactamente 15 casos.
- No inventes reglas de negocio que no estén especificadas.
- Si una validación depende de una regla desconocida, indícala como supuesto pendiente de confirmar.
- Cada caso debe tener datos de entrada y un resultado esperado claro.
- Evita duplicaciones.

Formato de respuesta:
Presenta los resultados en una tabla con cuatro columnas: ID, nombre del caso, datos de entrada y resultado esperado.

Después de la tabla, agrega un breve resumen de la revisión crítica e indica qué ajustes realizaste.
```

**Técnicas agregadas:**

- Role prompting: define el rol específico de ingeniero de QA.
- Prompt estructurado: organiza el contexto, objetivo, condiciones y formato.
- Descomposición: divide la tarea en etapas para facilitar su desarrollo.
- Few-shot prompting: incorpora un ejemplo del resultado esperado.
- Autocrítica: solicita revisar y ajustar los casos antes de presentar la respuesta final.

**¿Por qué se agregaron estas técnicas?**

Se incorporaron para mejorar la precisión y la calidad del resultado. El rol orienta la respuesta hacia pruebas de software; la estructura establece instrucciones claras; la descomposición organiza el trabajo; el ejemplo guía el formato y la autocrítica permite detectar errores, duplicaciones y supuestos no confirmados.

**Resultado obtenido:**

Se generaron exactamente 15 casos de prueba, con identificadores consecutivos y una tabla de cuatro columnas. También se incluyó una revisión crítica que identificó escenarios repetidos, resultados que debían aclararse y reglas pendientes de especificación.

**¿Qué mejoró respecto a las versiones anteriores?**

La versión 3 consiguió una respuesta más organizada y verificable. A diferencia de la primera versión, definió un rol, una estructura y un formato concreto. También superó a la segunda al incorporar un ejemplo, dividir el trabajo en etapas y solicitar una revisión crítica antes de entregar el resultado final.

## Técnicas usadas en el prompt final

| Técnica | ¿Dónde se aplicó? | ¿Para qué se utilizó? |
|---|---|---|
| Role prompting | «Actúa como un ingeniero de QA especializado...» | Definir el rol y orientar la respuesta hacia pruebas funcionales. |
| Prompt estructurado | Secciones de contexto, objetivo, condiciones y formato. | Organizar las instrucciones y evitar ambigüedades. |
| Descomposición | Las cinco etapas de desarrollo de la tarea. | Dividir el problema en actividades más sencillas. |
| Few-shot prompting | Ejemplo del caso CP-001. | Mostrar cómo deben presentarse los casos de prueba. |
| Autocrítica | Etapa de revisión crítica y ajustes. | Detectar duplicaciones, resultados ambiguos y reglas no especificadas. |

## Evaluación del resultado

| Criterio de evaluación | Sí | No |
|---|:---:|:---:|
| El prompt define un rol específico. | X | |
| Incluye contexto y objetivo claros. | X | |
| Divide la tarea en etapas. | X | |
| Presenta un ejemplo del formato esperado. | X | |
| Solicita exactamente 15 casos de prueba. | X | |
| Define una estructura de respuesta mediante una tabla. | X | |
| Incluye una revisión crítica del resultado. | X | |
| Evita asumir reglas de negocio no especificadas. | X | |

## ¿Por qué elegí estas técnicas?

Elegí estas técnicas porque se complementan y permiten mejorar progresivamente la calidad de las respuestas. El role prompting establece el perfil que debe adoptar el modelo; el prompt estructurado organiza las instrucciones; la descomposición facilita el desarrollo de tareas complejas; el few-shot prompting proporciona un ejemplo concreto y la autocrítica permite revisar y mejorar el resultado antes de presentarlo. En conjunto, estas técnicas permiten obtener respuestas más claras, organizadas y útiles para el diseño de casos de prueba.
