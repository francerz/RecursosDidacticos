Estilos de programación
=======================================

- [Estilos de programación](#estilos-de-programaci%c3%b3n)
  - [Convenciones de nombres](#convenciones-de-nombres)
    - [Estilos comunes](#estilos-comunes)
      - [`camelCase`](#camelcase)
        - [Ejemplos:](#ejemplos)
      - [`PascalCase`](#pascalcase)
        - [Ejemplos:](#ejemplos-1)
      - [`under_score`](#underscore)
        - [Ejemplos:](#ejemplos-2)
      - [`ALL_CAPS`](#allcaps)
        - [Ejemplos:](#ejemplos-3)
      - [`dashed-names`](#dashed-names)
        - [Ejemplos:](#ejemplos-4)

Convenciones de nombres
---------------------------------------

En el mundo de la programación, se requiere utilizar nombres para identificar
los componentes que conforman la lógica de la aplicación, por ejemplo: nombres
de variables, funciones, métodos, clases, etc.

La identificación de estos nombres es crucial en la comprensión del código
fuente, por lo que se han designado diferentes notaciones para identificar cada
uno de los componentes, independientemente del nombre que este tenga. Asimismo,
el contar con un estándar común entre todos los desarrolladores en un mismo
lenguaje de programación facilita la lectura y comprensión de código realizado
por otros programadores. Por lo que se designan reglas que por acuerdo de buenas
prácticas se recomienda su uso. A este conjunto de reglas se les denomina
*Convención de nombres*.

> **Sabias que...**  
> Más del 80% del tiempo dedicado a programar consiste en leer el código
> previamente escrito.

### Estilos comunes

Los estilos más comunes se utilizan en la identificación de diferentes tipos de
elementos a partir del contexto y uso que se les de.

#### `camelCase`

Es una práctica en la que se escriben palabras o abreviaturas conjuntas (sin
espacios o puntuación) y cuya distinción se realiza con mayúscula al
inicio de cada palabra, exceptuando la primer letra del conjunto que siempre se
se escribe en minúsculas.

##### Ejemplos:
- `nombre`
- `primerApellido`
- `segundoApellido`
- `curp` *(La abreviatura CURP se compone de 4 palabras **Clave Única de Registro Poblacional**)*
- `innerHTML` *(La abreviatura HTML se compone de 4 palabras **Hyper-Text Markup Language**)*

> En dos de los casos anteriores se utilizaron abreviaturas bien conocidas:
> `CURP` y `HTML`, las cuales se representaron de forma incongruente, esto se
> debe a su posición en el conjunto de palabras.  
> Si la abreviatura se coloca al principio del conjunto, se escribe todo en
> minúsculas, en cambio, si le precede otra palabra, se escriben mayúsculas.  
> Ejemplo:
> - `miCURP`
> - `htmlBasico`

#### `PascalCase`

También conocido como *Upper Camel Case*, utiliza el mismo principio que
*camelCase* en el que todas las palabras se ponen en conjunto, distinguiéndose
por el uso de mayúsculas al inicio de cada palabra. Sin embargo, difiere en que
la primera letra de todo el conjunto inicia en mayúscula.

##### Ejemplos:
- `Nombre`
- `PrimerApellido`
- `SegundoApellido`
- `CURP`
- `InnerHTML`

> En contraste con `camelCase`, las abreviaturas se escriben siempre con todos
> sus caracteres en mayúsculas.  
> Incluso, si tienen una palabra en continuación, la siguiente palabra iniciará
> también con mayúscula, por ejemplo: `HTMLElement`.

#### `under_score`

Este estilo de escritura conjunta múltiples palabras utilizando como separación
el guión bajo `_`. Por lo regular utilizando minúsculas en toda la palabra.

##### Ejemplos:
- `nombre`
- `primer_apellido`
- `segundo_apellido`
- `curp`
- `inner_html`

#### `ALL_CAPS`

Este estilo de escritura utiliza múltiples palabras todas escritas en mayúsculas
y separadas por guiones (por lo regular guión bajo `_`). De manera generalizada
se utiliza en los lenguajes de programación para referirse a valores constantes
que no son modificables una vez que fueron inicializados.

##### Ejemplos:
- `NOMBRE`
- `PRIMER_APELLIDO`
- `SEGUNDO_APELLIDO`
- `CURP`
- `INNER_HTML`

#### `dashed-names`

Este estilo de escritura utiliza múltiples palabras separándose por guiones
medios `-`. Es poco utilizado en lenguajes de programación, y su uso es
generalmente en lenguajes de presentación como HTML y CSS.

Su uso está restringido en lenguajes de programación debido al a ambiguedad que
existe entre el guión medio y el signo de resta, que genéricamente utilizan el
mismo símbolo.

##### Ejemplos:
- `nombre`
- `primer-apellido`
- `segundo-apellido`
- `curp`
- `inner-html`