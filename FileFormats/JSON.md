JSON (JavaScript Object Notation)
=================================

JSON es una sintaxis para serializar estructuras de datos, como son: objetos,
arreglos, números, cadenas, booleanos y `null`. Está basado en la sintaxis de
JavaScript, pero es distinto.

A pesar de estar basado en el lenguaje de programación estándar JavaScript
(ECMA-262). JSON es un formato de texto completamente independiente del
lenguaje, pero utliza convenciones que son familiares para los programadores de
los lenguajes de la familia C, incluyendo C, C++, C#, Java, JavaScript, Perl,
Python, y muchos otros. Estas propiedades convierten a JSON en un lenguaje de
intercambio de datos ideal.

JSON está constituido por dos estructuras:

  - Una colección de pares de nombre/valor. Envarios lenguajes es conocido como
    un *objeto*, registro, estructura, diccionario, tabla hash, lista de claves
    o arreglo asociativo.
  - Una lista ordenada de valores. En la mayoría de los lenguajes esto se
    implementa como arreglos, vectores, listas o secuencias.

Estas estructuras son universales; virtualmente todos los lenguajes de
programación las soportan de una forma u otra.

## Tipos de Datos

Tipo        | Descripción
:-----------|:--
**Número**  | Secuencia numérica de punto flotante con precisión doble.
**Cadena**  | Secuencia de caracteres entre comillas, permite caracteres unicode con secuencia de escape.
**Booleano**| Valores booleanos `true` o `false`.
**Null**    | Representa la ausencia de un valor.
**Objeto**  | Estructura que almacena conjuntos de pares nombre/valor, encapsulados entre `{ }`.
**Arreglo** | Colección de valores separados por coma de cualquier tipo encapsulados entre `[ ]`.

### Número

Cualquier secuencia numérica que represente números positivos o negativos,
enteros o de punto flotante con precisión double. Pueden incluir notación
exponencial numérica. **No se soportan valores octales o hexadecimales**.

Ejemplos:
  - `14`
  - `23.2`
  - `-13.3`
  - `53.5e+2`
  - `38e-2`

### Cadena

Cualquier secuencia de caracteres entre comillas dobles `" "`.

Ejemplo: `"Hola Mundo"`

Adicionalmente se permiten secuencias de escape, utilizando `\` seguido de un
caracter definido, para representar caracteres especiales o ambiguos en el
formato.


Secuencia   | Descripción                                   | Unicode
------------|-----------------------------------------------|--------
"           | Representa el caracter comillas dobles.       | `\u0022`
\\          | Representa el caracter diagonal invertida.    | `\u005C`
/           | Representa el caracter diagonal.              | `\u002F`
b           | Representa el caracter retroceso.             | `\u007F`     
f           | Representa el caracter form feed.             | `\u000C`
n           | Representa el caracter de nueva línea.        | `\u000A`
r           | Representa el caracter retorno de carro.      | `\u000D`
t           | Representa el cacacter tabulador              | `\u0009`
uXXXX       | Representa el caracter según el código Unicode de 4 dígitos.

Ejemplos:
  * ```json
    "Cadena simple"
    ```
    Salida obtenida:  
    ```
    Cadena simple
    ```

  * ```json
    "Cadena que tiene secuencias de escape\nSeparada en dos renglones."
    ```
    Salida obtenida:  
    ```
    Cadena que tiene secuencias de escape
    Separada en dos renglones.
    ```

  * ```json
    "Cadena con acento ortogr\u00e1fico."
    ```
    Salida obtenida:  
    ```
    Cadena con acento ortográfico
    ```
    Algunos caracteres comunes:
    
    Letra `Código` | Letra `Código`  | Letra `Código` | Letra `Código`
    ---|---|---|---
    Á `\u00C1` | á `\u00E1` | Ñ `\u00D1` | ñ `\u00F1`
    É `\u00C9` | é `\u00E9` | Ü `\u00DC` | ü `\u00FC`
    Í `\u00CD` | í `\u00ED` | ¡ `\u00A1` | ¿ `\u00BF`
    Ó `\u00D3` | ó `\u00F3` 
    Ú `\u00DA` | ú `\u00FA`
    
    [Sitio para buscar más caracteres y claves Unicode](https://unicode-table.com/es/)

### Booleano

Representa un valor binario con los estados `true` y `false`.

### Objetos

  - Es una secuencia, no ordenada, de pares nombre/valor.
  - Los objetos se delimitan con *llaves*, lo que significa que un objeto inicia
    con `{` y termina con `}`.
  - Los nombres de los atributos, tambien conocidos como clave (*key*), se
    encapsulan entre comillas dobles `"`.
  - La separación entre la clave y el valor de un atributo es `:` *(dos puntos)*.
  - Para separar cada par de clave/valor se utiliza `,` *(coma)*.

Ejemplos:
  - Objeto vacío, sin atributos:
    ```json
    {}
    ```
  - Objeto simple:
    ```json
    {
        "proyecto": "SIITEC 2",
        "liberado": true,
        "activo": true,
        "framework": "CodeIgniter 2.1.3"
    }
    ```
  - Objeto con atributo de tipo arreglo:
    ```json
    {
        "titulo": "Fundamentos de Bases de Datos",
        "autores": [
            "Silberschatz, Abraham",
            "Korth, Henry F.",
            "Sudarshan, S."
        ]
    }
    ```

### Arreglo

  - Es una colección ordenada de valores.
  - La colección está delimitada por corchetes, lo que significa que un arreglo
    inicia con `[` y termina con `]`.
  - Los valores independientes son separados utilizando `,` *(coma)*.
  - Los arreglos sólo pueden contener elementos cuando su índice es con valores
    enteros secuenciales.

Ejemplos:
  - Arreglo vacío, sin elementos:
    ```json
    []
    ```
  - Arreglo de números:
    ```json
    [ 1, 2, 3, 4 ]
    ```
  - Arreglo de cadenas:
    ```json
    [ "cinco", "seis", "siete", "ocho" ]
    ```
  - Arreglos anidados:
    ```json
    [
        [ 1, 2, 3],
        [ 4, 5, 6],
        [ 7, 8, 9]
    ]
    ```
  - Arreglo de objetos:
    ```json
    [
        { "lenguaje":"JavaScript", "publicado":"2019-11-12" },
        { "lenguaje":"PHP", "version":"1.23" }
    ]
    ```

> **NOTA IMPORTANTE**  
> Aunque no todos los lenguajes los soporten, en JSON se permite que
> los arreglos tengan elementos de tipos heterogéneos, donde sus elementos
> pueden ser de tipos, no necesariamente compatibles. Por ejemplo:
> ```json
> [
>   1,
>   2,
>   3.0,
>   "cuatro",
>   { "numero": 5 },
>   { "numero": 6 },
>   "siete",
>   "ocho",
>   9
> ]
> ```

## Referencias
- [1]: Introducción a JSON (https://www.json.org/json-es.html)
- [2]: JSON - Data Types (https://www.tutorialspoint.com/json/json_data_types.htm)

## Vease también
- [YAML](yaml.md)
- [XML](xml.md)

