XML (eXtensible Markup Language)
================================

Es un lenguaje de marcas desarrollado por el W3C (Wold Wide Web) en el propósito
de almacenar datos de manera estructurada y legible para el ser humano.

Su estructura se basa en el lenguaje SGML (Standard Generalized Markup Language)
que permite definir lenguajes de marcado generalizados para documentos. La
estructura debe cumplir las siguientes características.

* Declarativo: debe describir la estrucutra y atributos del documento, en lugar
  de especificar el procesamiento que se realiza sobre el mismo, esto previene
  conflictos con desarrollos futuros.
* Riguroso: con el propósito de permtitir que el marcado tome ventajas sobre
  objetos definidos con rigurosidad, por ejemplo bases de datos.

El propósito de XML es para el intercambio de información estructurada entre
diferentes plataformas, aplicaciones y sistemas. Aunque su uso popular más
extendido es en Internet.

## Conceptos

La especificación de XML utiliza múltiples conceptos para definir la estructura
básica del mismo, algunos de estos conceptos son:

### Caracter
Un documento de XML es un cadena de *caracteres*. Casi cada caracter Unicode
puede aparecer en un documento XML.

### Procesador y aplicación

El *procesador* analiza el marcado y pasa la información estructurada a la
*aplicacion*. La especificación coloca los requerimientos de de lo que un
procesador de XML debe realizar y no debe realizar, pero la aplicación
es tá fuera de su alcance. El procesador comúnmente es referido como un
*XML parser*.

### Estructura de XML

Los caracteres que componen un documento XML se dividen en *marcado* y
*contenido*, el cual puede distinguirse por la aplicación de reglas sintáticas
simples. Generalmente las cadenas pueden constituir marcado si bien empiezan con
`<` y terminar con un `>`, o comienzan con el caracter `&` y terminan en `;`.
Las cadenas de caracteres que no son marcado son Contenido.
Sin embargo, en una sección CDATA, los delimitadores `<![CDATA[` y `]]>` son
clasificados como marcado, mientras que el texto entre ellos, se clasifica
contenido.

### Etiqueta
Una *etiqueta (tag)*es un marcado constructor que comience con `<` y termina
con `>`. Existen tres formas de etiquetas:

* *etiqueta-inicio*, como `<seccion>`.
* *etiqueta-termino*, como `</seccion>`.
* *etiqueta-vacia*, como `<salto-linea />`.

### Elemento

Un elemento es un componente lógico del documento que comienza con una etiqueta
de inicio y termina con una etiqueta de término correspondiente, o sólo consiste
en una etiqueta vacía.
Los caracteres entre la etiqueta de inicio y la de final, si los hay, son el
*contenido* del elemento, y pueden contener marcado, incluyendo otros elementos,
los cuales son llamados elementos *hijos (child)*.