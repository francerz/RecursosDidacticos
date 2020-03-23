YAML (YAML Ain't Markup Language)
====================================

Es un estandar de serialización de datos para todos los lenguajes, caracterizado
por lo fácil de ser leído y comprendido para los seres humanos.

En su versión 1.2 cuenta con integración de JSON como un subconjunto oficial.
Siendo necesario que los valores booleanos sean serializados como `true` o
`false`; el escalar vacío sea `null`, pero manteniendo la compatibilidad con
versiones anteriores del estándar.

Existen cientos de estructuras de datos, pero pueden ser representadas en tres
tipos básicos de primitivas: mapeos(tablas hash / diccionarios), secuencias
(arreglos / listas) y escalares (cadenas / numeros).

## Objetivos del lenguaje

Los objetivos de diseño en YAML son, en prioridad descendente:

  1. YAML es legible para los humanos.
  2. Los datos en YAML son portables entre diferentes lenguajes de programación.
  3. Las estructuras de YAML concuerdan con estructuras de datos nativas de los lenguajes ágiles.
  4. YAML tiene un modelo consistente para soportar herramientas genéricas.
  5. YAML soporta el procesamiento en un solo paso.
  6. YAML es expresivo y extendible.
  7. YAML es facil de implementar y utilizar.

## Estructura

La identación de YAML es similar al alcance que el de Python (sin las
ambiguedades causadas por las tabulaciones). Los bloques indentados facilitan
la inspección de la estrutura de datos. Adicionalmente permite el uso del
alcance similar a JSON y Perl, en la cual el contenido se encuentra delimitado
por caracteres específicos. Ambos estilos pueden anidarse libremente.

En cuanto a los contenidos entre comillas dobles `" "`  se permite el uso de 
secuencias de escape en estilo C.

Cuenta con normalización de fin de línea, donde un salto de línea singular es
representado como un espacio en blanco, mientras que líneas vacías serán
interpretadas como saltos de línea.

## Relación con JSON

Tanto JSON como YAML son formatos de intercambio de datos que pretenden ser
legibles por los seres humanos. Sin embargo, JSON y YAML tienen diferentes
prioridades. El objetivo principal de JSON es la simplicidad y universalidad.
Por lo tanto, JSON es trivial para generar y convertir, con el costo de
legibilidad reducida para los seres humanos. También utiliza el modelo de
información con menor común denominador, asegurándose que cualquier dato en JSON
puede ser fácilmente procesado por un ambiente de programación moderno.

En contraste, los objetivos de diseño más imporantes en YAML son la legibilidad
para los humanos, y el soporte para serializar estructura de datos nativas
arbitrarias. Por lo tanto, permite archivos fáciles de leer, pero mucho más
complejos de leer y convertir. Adicionalmente, YAML se extiende por sobre el
común denominador de los tipos de datos, requiriendo procesamiento más complejo
cuando se intercambia entre diferentes ambientes de programación.

## Relación con XML

A pesar de que los dos lenguajes pueden competir en varios dominios de
aplicación, no existe correlación directa entre ambos.

YAML es un lenguaje de serialización de datos. XML fue diseñado para ser
retrocompatible con el Lenguaje Estándar de Marcado Generalizado (SGML), el cual
fue diseñado para soportar documentación estructurada. XML por otro lado, tiene
muchas restricciones en lugares donde YAML no las comparte. XML es pionero en
varios dominios, YAML es el resultado de las lecciones aprendidas en XML y otras
tecnologías.

## Estructura

YAML cuenta con estructuras complejas que permiten representar múltiples contenidos, pero se clasifican principalmente en tres tipos: escalares,
secuencias y mapas.

### Escalares

Son datos que son atómicos por sí mismos y tienen un valor preciso en un momento
determinado. Se clasifican en tres: enteros, flotantes y cadenas.

#### Enteros

Representan cualquier secuencia de dígitos numéricos, incluyendo valores
negativos, en los que no existe parte fraccional.

Ejemplos:
  * `0`
  * `23`
  * `-4`
  * `+234`
  * `34,642`

#### Flotantes

Representan cualquier secuencia de dígitos numéricos, incluyendo valores
negativos,, en los que existe una parte fraccional, representada por un `.`
*(punto)*.

Ejemplos:
  * `0.0`
  * `53.6`
  * `-84.62`
  * `+323.34`
  * `56,853.6`

#### Cadenas

Son secuencias de caracteres, que representan valores de texto.

Opcionalmente pueden ir delimitadas por comillas dobles (`"`), o comilla simple
(`'`).

Cuando se utilizan comillas dobles (`"`), es posible representar secuencias de
escape utilizando el estilo del lenguaje C, utilizando la diagonal invertida
(`\`).

Ejemplos:
  * `Lenguaje`
  * `Etiquetas de marcado`
  * `"Entre comillas dobles."`
  * `'Entre comillas simples.'`
  * `"Texto entre comillas dobles.\n\tIncluye secuencias de escape."`

> **NOTA**  
> Es común utilizar comillas, ya sean dobles o simples, para delimitar textos,
> principalmente cuando estos pueden contener caracteres que pueden ser
> interpretados como parte de la sintaxis estructural.

También es posible escribir texto en bloques, permitiendo cadenas multilínea.
Contando con dos símbolos particulares para su utilización.

  * `|` Se utiliza para preservar los saltos de línea en la cadena.
  * `>` Se utiliza para que los saltos de línea colapsen en un espacio en blanco.

Ejemplos:
  * Multilínea preservando los saltos. Es importante notar los saltos de línea
    y el uso de las tabulaciones, para describir el texto contenido.
    ```yaml
    texto: |
        El viejo Señor Gómez pedía queso, kiwi y habas, pero le ha tocado un saxofón.
        Mi hijo degustó en el festival de bayas una extraña pizza de kiwi con queso.
    ```
  * Multilínea ignorando salto de línea. Es importante notar el uso de las
    tabulaciones para describir el texto contenido.
    ```yaml
    texto: >
        Un pangrama es un texto que utiliza todas las letras posibles del
        alfabeto de un idioma. Los pangramas más llamativos son, por lo general,
        los que usan el menor número de letras.
    ```

### Secuencias

Las secuencias consisten en un conjunto ordenado de elementos, que se colocan
de manera adyacente. Comúnmente se identifican como listas, arreglos o vectores.

Para el formato de las listas, YAML cuenta con dos formas distintas de
representarlas.
  * **Formato de línea.**
  * **Formato de bloque.**

  ```yaml
  --- #Lista de enteros en bloque
  - 134
  - -342
  - 23,642
  - -4,564

  --- #Lista de enteros en fila
  [134, -342, 23,642, -4,564]

  --- # Lista de cadenas en bloque
  - Rojo
  - 'Verde'
  - "Azul"

  --- # Lista de cadenas en línea
  [ rojo, 'Verde', "Azul"]
  ```

### Mapas

- [1] YAML (https://yaml.org/)
- [2] YAML Ain't Markup Languaje (YAML) Version 1.2 (https://yaml.org/spec/1.2/spec.html)