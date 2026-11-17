# Bitácora de técnicas avanzadas

**Laboratorio 07:** Técnicas Avanzadas de Prompting.

**Herramienta de IA usada:** ChatGPT

## Ejercicio 2: Zero-shot, one-shot y few-shot

### Objetivo

Comparar las técnicas Zero-shot, One-shot y Few-shot para identificar cómo influye la cantidad de ejemplos proporcionados en la clasificación de comentarios de clientes.

### Comentarios utilizados

1. Me encantó, llegó rápido.
2. No lo recomiendo.
3. Es aceptable por el precio.
4. Pésima atención, no vuelvo.
5. Excelente calidad, lo volvería a comprar.

### 1. Zero-shot

**Prompt utilizado:**

Clasifica los cinco comentarios de clientes según su sentimiento: Positivo, Negativo o Neutral.

**Resultado obtenido:**

| N.º | Clasificación |
|---|---|
| 1 | Positivo |
| 2 | Negativo |
| 3 | Neutral |
| 4 | Negativo |
| 5 | Positivo |

**Observación:**

La IA realizó la clasificación sin recibir ejemplos previos. Presentó una tabla, un resumen estadístico y una conclusión.

### 2. One-shot

**Prompt utilizado:**

Clasifica cada comentario como Positivo, Negativo o Neutral.

Ejemplo: "Me gustó mucho" → Positivo.

**Resultado obtenido:**

1. Positivo
2. Negativo
3. Neutral
4. Negativo
5. Positivo

**Observación:**

Se proporcionó un ejemplo para orientar a la IA. La respuesta fue breve y directa, mediante una lista numerada.

### 3. Few-shot

**Prompt utilizado:**

Clasifica los comentarios como Positivo, Negativo o Neutral.

Ejemplos:

- "El producto es excelente" → Positivo.
- "El servicio fue pésimo" → Negativo.
- "El producto es regular" → Neutral.

**Resultado obtenido:**

1. Positivo
2. Negativo
3. Neutral
4. Negativo
5. Positivo

**Observación:**

Se utilizaron tres ejemplos para orientar la clasificación. La IA presentó el resultado mediante una lista numerada.

### Comparación de resultados

| Técnica | Ejemplos previos | Aciertos (de 5) |
|---|---:|---:|
| Zero-shot | 0 | 5 |
| One-shot | 1 | 5 |
| Few-shot | 3 | 5 |

### Tabla de registro de resultados

| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Sí/No) |
|---|---:|---|---|
| Zero-shot | 5 | Tabla, resumen y conclusión | No |
| One-shot | 5 | Lista numerada | No |
| Few-shot | 5 | Lista numerada | No |

### Conclusión

Las tres técnicas obtuvieron las mismas cinco clasificaciones. Zero-shot permitió resolver la tarea sin ejemplos, One-shot utilizó un ejemplo de referencia y Few-shot proporcionó tres ejemplos para orientar la respuesta.

En esta prueba, las tres técnicas llegaron al mismo resultado, aunque presentaron diferencias en el formato de respuesta.

---

## Ejercicio 3: Chain of Thought

### Objetivo

Comparar una respuesta directa con una respuesta desarrollada paso a paso para comprender cómo se obtiene el resultado de un problema matemático.

### Problema planteado

Un producto cuesta S/ 120. La tienda aplica un descuento del 25 % y luego suma el 18 % de IGV sobre el precio con descuento. Un cliente compra 3 unidades. ¿Cuánto paga en total?

### 1. Pedido directo

**Prompt utilizado:**

```text
Un producto cuesta S/ 120. La tienda aplica un descuento del 25 % y luego suma el 18 % de IGV sobre el precio con descuento.

Un cliente compra 3 unidades. ¿Cuánto paga en total?

Responde solo con el número.
```

**Resultado obtenido:**

S/ 318.60.

### 2. Pedido paso a paso

**Prompt utilizado:**

```text
Un producto cuesta S/ 120. La tienda aplica un descuento del 25 % y luego suma el 18 % de IGV sobre el precio con descuento.

Un cliente compra 3 unidades. ¿Cuánto paga en total?

Resuélvelo paso a paso: muestra cada cálculo y comprueba el resultado antes de dar la respuesta final.
```

**Resultado obtenido:**

- Descuento por unidad: S/ 30.00.
- Precio con descuento: S/ 90.00.
- IGV por unidad: S/ 16.20.
- Precio final por unidad: S/ 106.20.
- Total por 3 unidades: S/ 318.60.

### 3. Comprobación con calculadora

| Paso | Cálculo | Resultado |
|---|---|---:|
| 1. Precio con descuento | 120 × 0.75 | 90 |
| 2. Precio con IGV | 90 × 1.18 | 106.20 |
| 3. Total por 3 unidades | 106.20 × 3 | 318.60 |

**Resultado esperado:** El total correcto es S/ 318.60. El pedido paso a paso muestra cada cálculo y permite compararlo con la tabla.

### 4. Registro de resultados

| Pedido | Respuesta de la IA | Muestra los pasos (Sí/No) | Correcta (Sí/No) |
|---|---:|---|---|
| Directo | S/ 318.60 | No | Sí |
| Paso a paso | S/ 318.60 | Sí | Sí |

### Comparación y observación

Ambos pedidos obtuvieron el mismo resultado: S/ 318.60. Sin embargo, el pedido paso a paso presentó los cálculos y permitió comprobar cómo se obtuvo la respuesta.

### Conclusión

La técnica Chain of Thought permite solicitar una explicación ordenada de un problema. Esto facilita revisar los cálculos y comprender el procedimiento utilizado para llegar al resultado.

---

## Ejercicio 4: Role prompting

### Objetivo

Comparar las respuestas de la IA al explicar un tema sin asignarle un rol y asignándole diferentes perfiles relacionados con la enseñanza y la programación.

### 1. Pedido sin rol

**Tema solicitado:**

Explicar qué es una variable en programación para una persona que está empezando a aprender.

**Resultado obtenido:**

La IA explicó qué es una variable, presentó ejemplos en Python, describió los tipos de datos y agregó una pequeña evaluación.

### 2. Pedido con rol de docente

**Prompt utilizado:**

```text
Actúa como un docente de programación para principiantes. Explica qué es una variable en programación utilizando palabras sencillas y un ejemplo práctico en Python. Organiza la explicación para que un estudiante pueda comprenderla fácilmente.
```

**Resultado obtenido:**

La IA respondió como un docente. Explicó el concepto de variable, presentó ejemplos de código Python, tablas, ejercicios de práctica y un resumen de la clase.

### 3. Pedido con rol de desarrollador senior

**Prompt utilizado:**

```text
Actúa como un desarrollador senior especializado en Python. Explica qué es una variable desde una perspectiva técnica. Incluye características principales, sintaxis, ejemplos de código, tipos de datos y consideraciones técnicas importantes. Utiliza vocabulario especializado y ejemplos prácticos.
```

**Resultado obtenido:**

La IA explicó las variables desde una perspectiva técnica. Incluyó conceptos como identificadores, referencias a objetos, asignación, tipado dinámico y mutabilidad. También presentó ejemplos de código Python, análisis técnico y consideraciones sobre las variables.

### 4. Registro de diferencias

| Versión | Vocabulario (sencillo/técnico) | Usa ejemplos o código | A quién le sirve más |
|---|---|---|---|
| A. Sin rol | Sencillo | Sí, ejemplos y código Python | Principiantes |
| B. Rol docente | Sencillo y didáctico | Sí, ejemplos y código Python | Estudiantes principiantes |
| C. Rol senior | Técnico y especializado | Sí, ejemplos y código Python | Personas con conocimientos básicos de programación |

### 5. Comparación y observación

Al comparar las tres respuestas, se observa que el rol asignado influye en el vocabulario, el nivel de detalle y la organización de la explicación. La versión sin rol ofrece una explicación general, la versión docente utiliza un lenguaje didáctico y la versión senior profundiza en conceptos técnicos.

### Conclusión

El uso de Role prompting permite orientar las respuestas de la IA hacia un perfil determinado. Al asignarle el rol de docente, la explicación fue más organizada, didáctica y enfocada en el aprendizaje de principiantes. Con el rol de desarrollador senior, la explicación utilizó términos técnicos y conceptos más avanzados.

---

## Ejercicio 5: Descomposición

### Objetivo

Comparar un pedido realizado de una sola vez con una tarea dividida en pasos pequeños, utilizando la técnica de descomposición para desarrollar un sistema de inventario para una tienda pequeña en Java.

### 1. Pedido de una sola vez

**Prompt utilizado:**

```text
Crea un sistema de inventario para una tienda.
```

**Resultado obtenido:**

La IA generó un sistema de inventario para una tienda utilizando Excel. Incluyó las siguientes funcionalidades:

- Panel de control con total de productos, unidades disponibles, valor del inventario y alertas de reposición.
- Registro de productos con código SKU, nombre, categoría y precios.
- Control de entradas y salidas.
- Registro de compras y ventas.
- Control de existencias y alertas de productos por reponer.

La IA también generó un archivo Excel llamado `sistema_inventario_tienda.xlsx`.

**Observación:**

La respuesta fue general y la IA eligió Excel como herramienta de desarrollo sin que se especificara un lenguaje de programación. Por ello, no se obtuvo directamente el diseño de un sistema desarrollado en Java.

### 2. Pedido por pasos

Para mejorar el resultado, se dividió la tarea en cuatro pasos. Todos los mensajes se enviaron dentro del mismo chat para mantener el contexto de las respuestas anteriores.

#### Paso 1: Identificación de requisitos

**Prompt utilizado:**

```text
Voy a crear un sistema de inventario para una tienda pequeña en Java. Lista los 5 requisitos principales del sistema.
```

**Resultado obtenido:**

La IA identificó cinco requisitos principales:

1. **Gestión de productos:** registrar, modificar, eliminar y consultar productos.
2. **Control de entradas y salidas de inventario:** registrar ingresos, salidas por ventas y actualizar existencias.
3. **Control de stock:** consultar cantidades disponibles y generar alertas cuando los productos lleguen al stock mínimo.
4. **Gestión de ventas:** registrar ventas, calcular totales y descontar productos del inventario.
5. **Generación de reportes:** mostrar el inventario actual, productos más vendidos e historial de movimientos.

También recomendó utilizar Java, MySQL, Java Swing y JDBC como tecnologías para el desarrollo.

**Observación:**

La IA presentó cinco requisitos organizados y relacionados con las necesidades de una tienda pequeña. A diferencia del primer pedido, especificó que el sistema debía desarrollarse en Java.

#### Paso 2: Diseño de clases

**Prompt utilizado:**

```text
Con esos requisitos, diseña las clases necesarias. Para cada clase indica sus atributos con su tipo de dato.
```

Como la primera respuesta solamente presentó dos clases, se solicitó continuar con las seis restantes y completar las ocho clases anunciadas.

**Resultado obtenido:**

La IA propuso ocho clases principales aplicando Programación Orientada a Objetos (POO).

| N.º | Clase | Función principal |
|---:|---|---|
| 1 | Producto | Representar los productos registrados en la tienda. |
| 2 | Inventario | Controlar las existencias de los productos. |
| 3 | MovimientoInventario | Registrar las entradas y salidas de productos. |
| 4 | Venta | Administrar las ventas realizadas en la tienda. |
| 5 | DetalleVenta | Registrar los productos incluidos en cada venta. |
| 6 | Reporte | Generar información del inventario y las ventas. |
| 7 | Usuario | Administrar los usuarios y sus permisos. |
| 8 | ConexionBD | Establecer la conexión entre Java y MySQL. |

**Principales atributos identificados:**

**Clase Producto**

| Atributo | Tipo de dato |
|---|---|
| idProducto | int |
| codigo | String |
| nombre | String |
| descripcion | String |
| categoria | String |
| precio | double |
| stock | int |
| stockMinimo | int |

**Clase Inventario**

| Atributo | Tipo de dato |
|---|---|
| idInventario | int |
| fechaActualizacion | LocalDateTime |
| productos | List |

**Clase MovimientoInventario**

| Atributo | Tipo de dato |
|---|---|
| idMovimiento | int |
| producto | Producto |
| tipoMovimiento | String |
| cantidad | int |
| fecha | LocalDateTime |
| observacion | String |

**Clase Venta**

| Atributo | Tipo de dato |
|---|---|
| idVenta | int |
| fecha | LocalDateTime |
| detalles | List |

**Clase DetalleVenta**

| Atributo | Tipo de dato |
|---|---|
| idDetalle | int |
| producto | Producto |
| cantidad | int |
| precioUnitario | BigDecimal |
| subtotal | BigDecimal |

**Clase Reporte**

| Atributo | Tipo de dato |
|---|---|
| idReporte | int |
| tipoReporte | String |
| fechaGeneracion | LocalDateTime |
| descripcion | String |

**Clase Usuario**

| Atributo | Tipo de dato |
|---|---|
| idUsuario | int |
| nombre | String |
| usuario | String |
| contrasena | String |
| rol | String |

**Clase ConexionBD**

| Atributo | Tipo de dato |
|---|---|
| url | String |
| usuarioBD | String |
| contrasenaBD | String |
| conexion | Connection |

**Observación:**

La IA organizó el sistema en ocho clases, indicando la función de cada una y sus atributos con los respectivos tipos de datos. Esto permitió comprender mejor cómo se organizaría el proyecto antes de comenzar a programar.

#### Paso 3: Generación del código Java

**Prompt utilizado:**

```text
Escribe el código Java de la clase Producto con sus atributos, un constructor y los métodos get y set.
```

**Resultado obtenido:**

La IA generó la clase `Producto.java` con sus ocho atributos privados, un constructor y los métodos getters y setters correspondientes.

Código generado:

```java
public class Producto {

    // Atributos
    private int idProducto;
    private String codigo;
    private String nombre;
    private String descripcion;
    private String categoria;
    private double precio;
    private int stock;
    private int stockMinimo;

    // Constructor
    public Producto(int idProducto, String codigo, String nombre,
                    String descripcion, String categoria,
                    double precio, int stock, int stockMinimo) {

        this.idProducto = idProducto;
        this.codigo = codigo;
        this.nombre = nombre;
        this.descripcion = descripcion;
        this.categoria = categoria;
        this.precio = precio;
        this.stock = stock;
        this.stockMinimo = stockMinimo;
    }

    // Métodos get y set
    public int getIdProducto() {
        return idProducto;
    }

    public void setIdProducto(int idProducto) {
        this.idProducto = idProducto;
    }

    public String getCodigo() {
        return codigo;
    }

    public void setCodigo(String codigo) {
        this.codigo = codigo;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getDescripcion() {
        return descripcion;
    }

    public void setDescripcion(String descripcion) {
        this.descripcion = descripcion;
    }

    public String getCategoria() {
        return categoria;
    }

    public void setCategoria(String categoria) {
        this.categoria = categoria;
    }

    public double getPrecio() {
        return precio;
    }

    public void setPrecio(double precio) {
        this.precio = precio;
    }

    public int getStock() {
        return stock;
    }

    public void setStock(int stock) {
        this.stock = stock;
    }

    public int getStockMinimo() {
        return stockMinimo;
    }

    public void setStockMinimo(int stockMinimo) {
        this.stockMinimo = stockMinimo;
    }
}
```

**Ejemplo de uso generado por la IA:**

La IA también presentó una clase `Main` para crear un producto llamado Arroz, consultar su información y modificar su stock de 20 a 30 unidades.

**Observación:**

El código utiliza encapsulamiento mediante atributos privados, un constructor para inicializar los datos y métodos getters y setters para consultar y modificar los atributos.

#### Paso 4: Revisión y propuestas de mejora

**Prompt utilizado:**

```text
Revisa el código de la clase Producto y propone 3 mejoras concretas.
```

**Resultado obtenido:**

La IA revisó el código y propuso tres mejoras:

**1. Validar los datos de los atributos**

Problema: Los métodos setters permiten ingresar valores incorrectos, como precios negativos o cantidades de stock menores que cero.

Mejora: Agregar validaciones en los métodos setters para evitar valores negativos.

Ejemplo:

```java
public void setPrecio(double precio) {
    if (precio < 0) {
        throw new IllegalArgumentException(
            "El precio no puede ser negativo"
        );
    }
    this.precio = precio;
}

public void setStock(int stock) {
    if (stock < 0) {
        throw new IllegalArgumentException(
            "El stock no puede ser negativo"
        );
    }
    this.stock = stock;
}
```

**2. Utilizar BigDecimal en lugar de double**

Problema: El tipo de dato `double` puede generar pequeñas imprecisiones al realizar operaciones matemáticas con dinero.

Mejora: Cambiar el atributo precio de `double` a `BigDecimal`.

```java
import java.math.BigDecimal;

private BigDecimal precio;
```

También se deben adaptar el constructor y los métodos getter y setter para utilizar el nuevo tipo de dato.

Beneficio: Permite realizar cálculos monetarios con mayor precisión, especialmente al registrar ventas y calcular subtotales.

**3. Agregar un método para verificar el stock mínimo**

Problema: La clase tiene el atributo `stockMinimo`, pero no cuenta con un método que permita identificar cuándo un producto necesita reposición.

Mejora: Crear un método llamado `necesitaReposicion()`.

```java
public boolean necesitaReposicion() {
    return stock <= stockMinimo;
}
```

Beneficio: Permite identificar automáticamente los productos que tienen pocas existencias y necesitan ser repuestos.

**Resumen de las tres mejoras**

| N.º | Mejora | Beneficio |
|---:|---|---|
| 1 | Validar los atributos | Evita datos incorrectos. |
| 2 | Utilizar BigDecimal | Mejora la precisión de los precios. |
| 3 | Agregar necesitaReposicion() | Facilita el control del inventario. |

### 3. Comparación entre los dos pedidos

| Aspecto | Pedido de una sola vez | Pedido por pasos |
|---|---|---|
| Resultado | Sistema de inventario en Excel. | Diseño de un sistema en Java. |
| Organización | Respuesta general. | Requisitos, clases, código y mejoras. |
| Nivel de detalle | Funcionalidades generales. | Desarrollo organizado por etapas. |
| Código Java | No se generó. | Se generó la clase Producto. |
| Revisión | No se solicitó. | Se propusieron tres mejoras. |

### 4. Observación general

Al realizar el pedido de una sola vez, la IA generó una solución general en Excel, sin considerar un lenguaje de programación específico. En cambio, al dividir la tarea en pasos, fue posible establecer primero los requisitos, diseñar las clases necesarias, generar el código Java y finalmente identificar mejoras para la clase Producto.

### Conclusión

La técnica de descomposición permite desarrollar tareas grandes de manera organizada, dividiéndolas en actividades más pequeñas y fáciles de revisar. En este ejercicio se comprobó que trabajar por pasos permitió obtener un resultado más detallado y relacionado con los requisitos del sistema de inventario.

---

## Ejercicio 6: Prompt estructurado y autocrítica

### Objetivo

Comparar un prompt básico con un prompt estructurado para generar casos de prueba de un módulo Login. Además, aplicar la autocrítica para que la IA revise sus respuestas, identifique errores y proponga mejoras.

### 1. Prompt básico

**Prompt utilizado:**

```text
Dame casos de prueba para un login.
```

**Resultado obtenido:**

La IA generó 38 casos de prueba organizados en cinco categorías:

- 10 casos funcionales.
- 8 casos de validaciones.
- 8 casos de seguridad.
- 6 casos de interfaz (UI/UX).
- 6 casos de rendimiento y compatibilidad.

También presentó una plantilla profesional para documentar los casos de prueba y un ejemplo completo de inicio de sesión exitoso.

**Observación:**

El prompt básico permitió obtener una respuesta amplia con diferentes escenarios. Sin embargo, no especificaba la cantidad de casos, el formato ni los campos que debía contener cada prueba.

### 2. Prompt estructurado

**Prompt utilizado:**

Se solicitó a ChatGPT actuar como un ingeniero de QA y generar 10 casos de prueba para un módulo Login, indicando que debía presentar una tabla con ID, nombre del caso, descripción, datos de entrada, pasos de ejecución y resultado esperado. También se especificó que incluyera casos positivos y negativos, con lenguaje claro y sin repetir escenarios.

**Resultado obtenido:**

La IA generó 10 casos de prueba organizados en una tabla:

| ID | Nombre del caso |
|---|---|
| CP-001 | Inicio de sesión exitoso |
| CP-002 | Inicio de sesión con contraseña incorrecta |
| CP-003 | Inicio de sesión con usuario inexistente |
| CP-004 | Inicio de sesión con ambos campos vacíos |
| CP-005 | Inicio de sesión con usuario vacío |
| CP-006 | Inicio de sesión con contraseña vacía |
| CP-007 | Inicio de sesión con usuario inactivo |
| CP-008 | Inicio de sesión con contraseña que contiene caracteres especiales |
| CP-009 | Visualización de contraseña |
| CP-010 | Acceso al sistema después de cerrar sesión |

Cada caso incluyó su descripción, datos de entrada, pasos para ejecutar la prueba y resultado esperado.

**Observación:**

El prompt estructurado permitió obtener una respuesta más organizada y específica. La IA respetó la cantidad de casos solicitados y presentó información útil para ejecutar las pruebas.

### 3. Autocrítica de la IA

**Prompt utilizado:**

Se solicitó revisar los 10 casos de prueba desde la perspectiva de un ingeniero de QA, identificando aspectos que podían mejorarse para garantizar que las pruebas fueran más claras, completas, consistentes y fáciles de ejecutar.

**Resultado obtenido:**

La IA realizó una revisión crítica e identificó cinco problemas principales:

1. **Falta de precondiciones:** algunos casos necesitaban usuarios registrados, activos o inactivos, pero no explicaban cómo prepararlos.
2. **Resultados esperados poco específicos:** expresiones como "muestra un mensaje de error" no permitían determinar con precisión si la prueba fue exitosa.
3. **Solapamiento de escenarios:** algunos casos podían confundirse porque comprobaban situaciones similares.
4. **Falta de validaciones de seguridad:** se identificó la necesidad de incluir pruebas de intentos fallidos, inyección SQL y protección de información sensible.
5. **Falta de criterios verificables:** algunos resultados esperados no indicaban claramente qué debía observar el tester para aprobar una prueba.

### 4. Mejoras propuestas por la IA

Después de identificar los problemas, ChatGPT presentó una versión mejorada de los 10 casos de prueba.

| Aspecto mejorado | Cambio realizado | Beneficio |
|---|---|---|
| Descripciones | Se precisó el objetivo de cada prueba. | Facilita entender qué se está validando. |
| Datos de entrada | Se diferenciaron los usuarios y credenciales. | Evita confusiones durante la ejecución. |
| Pasos de ejecución | Se organizaron en acciones concretas y secuenciales. | Facilita reproducir los escenarios. |
| Resultados esperados | Se especificaron comportamientos observables. | Permite determinar si una prueba fue aprobada o fallida. |
| Precondiciones | Se añadieron preparaciones para cuentas inactivas y contraseñas especiales. | Reduce errores durante la ejecución. |
| Seguridad | Se precisó la invalidación de sesión después del cierre. | Mejora la cobertura de seguridad. |

### 5. Recomendaciones adicionales

La IA también recomendó incorporar posteriormente estos escenarios:

- Bloqueo por intentos fallidos.
- Protección contra inyección SQL.
- Expiración de sesión.
- Recuperación de contraseña.
- Control de accesos simultáneos.

### 6. Comparación de resultados

| Aspecto | Prompt básico | Prompt estructurado |
|---|---|---|
| Cantidad de casos | 38 | 10 |
| Organización | Por categorías | Tabla estructurada |
| Datos de entrada | Generales | Especificados |
| Pasos de ejecución | No en todos los casos | Incluidos |
| Resultados esperados | Generales | Más específicos |
| Claridad | Buena | Más precisa |

### 7. Comparación y observación general

Al comparar los resultados, se observa que el prompt básico permitió obtener una lista amplia de casos de prueba, mientras que el prompt estructurado produjo exactamente 10 casos con información más detallada y organizada.

Posteriormente, mediante la autocrítica, la IA identificó aspectos que podían mejorarse y presentó una versión optimizada de los casos de prueba.

Esto permitió obtener resultados más claros, completos y fáciles de ejecutar.

### 8. Evaluación final de los resultados

Después de realizar la última revisión, ChatGPT presentó una tabla final con 13 casos de prueba, organizados en cuatro columnas: ID del caso, nombre del caso de prueba, datos de entrada y resultado esperado.

**Tabla de evaluación:**

| Qué revisar | Cumple (Sí / No) |
|---|---|
| ¿Tiene las 4 columnas pedidas? | Sí |
| ¿Incluye el bloqueo después de 3 intentos? | Sí |
| ¿Incluye casos con campos vacíos? | Sí |
| ¿Indica qué casos agregó en la autocrítica? | Sí |
| ¿Hay algún caso repetido o que no tenga sentido? | No |

**Casos nuevos agregados:**

1. CP-011: Bloqueo de cuenta después de 3 intentos fallidos.
2. CP-012: Inicio de sesión con correo electrónico sin símbolo @.
3. CP-013: Inicio de sesión con correo electrónico vacío y espacios.

**Observación:**

La IA cumplió con los criterios solicitados. Se identificaron tres casos nuevos que permiten mejorar la cobertura de las pruebas. No se identificaron casos duplicados en la revisión final. Sin embargo, el caso CP-011 requiere confirmar que el sistema realmente establezca el bloqueo después de exactamente tres intentos fallidos.

### Conclusión

El uso de prompts estructurados permite orientar mejor las respuestas de la inteligencia artificial, estableciendo un contexto, una tarea y un formato específico. Además, la técnica de autocrítica ayuda a identificar errores, detectar escenarios faltantes y mejorar los resultados.

En este ejercicio comprobé que no basta con solicitar información a la IA, sino que también es importante revisar y evaluar sus respuestas. La evaluación permitió comprobar que la IA puede revisar y mejorar su propio trabajo, pero también puede cometer errores durante ese proceso.

Finalmente, se logró pasar de 10 casos iniciales a una tabla final de 13 casos de prueba, incorporando tres escenarios nuevos y mejorando la cobertura de validaciones del módulo Login. Esto demuestra la importancia de combinar prompts estructurados, autocrítica y revisión humana para obtener resultados más claros, completos y confiables.


---

## Conclusión general del Laboratorio 07

Durante el desarrollo de este laboratorio aprendí a utilizar diferentes técnicas avanzadas de prompting para mejorar las respuestas de la inteligencia artificial.

Se realizaron ejercicios prácticos aplicando Zero-shot, One-shot, Few-shot, Chain of Thought, Role prompting, descomposición, prompt estructurado y autocrítica.

También comprobé que proporcionar instrucciones claras, dividir las tareas y revisar los resultados permite obtener respuestas más organizadas, precisas y útiles.

Finalmente, comprendí que la inteligencia artificial es una herramienta de apoyo, pero siempre es necesario revisar y comprobar sus resultados antes de utilizarlos.

**Fin de la bitácora del Laboratorio 07.**