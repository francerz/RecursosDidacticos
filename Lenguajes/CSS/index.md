CSS (Cascade Style Sheet)
=======================================

- [CSS (Cascade Style Sheet)](#css-cascade-style-sheet)
  - [Sintaxis](#sintaxis)
    - [Selectores](#selectores)
      - [Elemento](#elemento)
      - [Atributo](#atributo)
      - [ID (valor del atributo id)](#id-valor-del-atributo-id)
      - [Clase](#clase)
      - [Pseudo-clase](#pseudo-clase)
  - [Referencia rápida de Selectores](#referencia-r%c3%a1pida-de-selectores)
    - [Selectores generales](#selectores-generales)
    - [Selectores por estado de los elementos](#selectores-por-estado-de-los-elementos)
    - [Selectores por ubicación en el DOM](#selectores-por-ubicaci%c3%b3n-en-el-dom)
    - [Selectores para formularios](#selectores-para-formularios)

Las hojas de estilo en casacada son un lenguaje para establecer la presentación
de los elementos que conforman un documento web, por lo general elaborado en
HTML, sin embargo, puede aplicarse a lenguajes de marcado basados en SGML, como
son: XML, XHTML, SVG, RSS, etc.

La definición de las hojas de estilo permiten separar el contenido de un
documento con la forma en la que este se presanta. Permitiendo aplicar diferente
presentación del contenido sin necesidad de realizar cambios en el mismo. También
permite mediante la utilización de *media queries* aplicar difrentes tipos de
presentacion dependiendo del medio en el que se proyecte, por ejemplo: impresión
en papel, pantalla de computadora, de tableta o dispositivo móvil, incluso 
lectores de pantalla.

Sintaxis
---------------------------------------

La sintaxis de las hojas de estilo es bastante sencilla, componiendo el documento
de reglas, las cuales consisten en uno o más *selectores* y en su interior
se define la declaración que tiene múltiples *propiedades*.

Ejemplo de documento CSS:

```css
/* Aplicar estilo a todas las etiquetas <body> */
body { 
    font-family: Arial;
    background: yellow;
    color: red;
}
/* Aplicar estilo a los elementos con atributo class="panel" */
.panel {
    border-width: 1px;
    border-style: solid;
    border-color: red;
}
/* Aplicar estilo a los elementos con atributo id="titulo" */
#titulo {
    font-size: 2em;
}
```

### Selectores

Los selectores son un componente fundamental en la estructuración de las reglas
CSS, puesto que señalan a qué tipo de elementos se deberán aplicar los estilos.

Existen seist tipos de selectores básicos: [Elemento], [Atributo], [ID], [Clase], 
[pseudo-clase] y [pseudo-elemento].

#### Elemento
Son aquellos que sólo tienen el nombre de la etiqueta a la que aplican el
estilo.

Por ejemplo: `html`, `body`, `h1`, `input`, etc.

Contenido en CSS:
```css
label {
    display: block;
    font-weight: bold; /* letras remarcadas */
}
input {
    border: 1px solid gray; /* borde de línea continua gris */
    border-radius: 4px; /* esquinas redondeadas */
}
```

Contenido en HTML:
```html
<form>
    <label>Nombre</label>
    <input type="text" />
    <label>Descripción</label>
    <textarea></textarea>
    <button type="submit">Guardar</button>
</form>
```

Resultado:
<style>
#example-0 label {
    display: block;
    font-weight: bold; /* letras remarcadas */
}
#example-0 input {
    border: 1px solid gray; /* borde de línea continua gris */
    border-radius: 4px; /* esquinas redondeadas */
}
</style>
<div id="example-0" class="example">
    <form>
        <label>Nombre</label>
        <input type="text" />
        <label>Descripción</label>
        <textarea></textarea>
        <button type="submit">Guardar</button>
    </form>
</div>

#### Atributo
Son aquellos que aplican a un elemento cuando en uno de sus tenga un atributo o
valor un determinado valor en el atributo.

Por ejemplo: `[required]`, `[href]`, `[visible=true]`, etc.

Contenido en CSS:
```css
[required] {
    background-color: rgba(255,0,0,0.2);
}
```

Contenido en HTML:
```html
<form method="POST" action="suscribir.php">
    <label for="inpEmail">Correo electrónico</label>
    <input id="inpEmail" type="email" required />
    <button>Suscribirme</button>
</form>
```

Resultado:
<style>
#example-1 [required] {
    background-color: red;
}
</style>
<div id="example-1" class="example">
    <form method="POST" action="suscribir.php">
        <label for="inpEmail">Correo electrónico</label>
        <input id="inpEmail" type="email" required />
        <button>Suscribirme</button>
    </form>
</div>


#### ID (valor del atributo id)

Son aquellos que aplican a un elemento cuando su atributo `id` tenga el valor
especificado en el mismo selector.

> **NOTA**
> El atributo ID debe de utilizarse a conciencia puesto que sólo puede existir
> una sola vez en todo el documento HTML. Es decir, no se debe tener en el mismo
> dos elementos con exactamente el mismo ID.

Para utilizar este tipo de selector se utiliza el símbolo `#`(numeral) antes
del nombre del identificador.

Por ejemplo: `#titulo` es lo mismo que `[id=titulo]`.

Contenido en CSS:
```css
#azul {
    color: blue;
}
```

Contenido en HTML:
```html
<div>
    <p id="azul">Mi título principal</p>
    <p id="verde">Mi título principal</p>
    <p>Mi título principal</p>
</div>
```

Resultado:
<style>
    #example-2 #azul {
        color: blue;
    }
</style>
<div id="example-2" class="example">    
    <div>
        <p id="azul">Mi título principal</p>
        <p id="verde">Mi título principal</p>
        <p>Mi título principal</p>
    </div>
</div>

#### Clase

Este es el tipo más común de selector, debido a que permite establecer estilos
de manera modular y fácil de manipular.

A diferencia del selector por ID, puede haber tantos elementos se requieran con
el mismo nombre de clase. Asimismo, un elemento puede tener más de una clase
a la vez.

Para identificar este tipo de selector, se utiliza un `.` (punto) antes del
nombre de la clase.

Por ejemplo: `.texto-rojo` aplica para elementos con `class="texto-rojo"`

Contenido en CSS:
```css
.texto-rojo {
    color: red;
}
.fondo-amarillo {
    background: yellow;
}
```

Contenido en HTML
```html
<article>
    <p class="texto-rojo">Lorem ipsum dolor sit amet.</p>
    <p class="fondo-amarillo">Lorem ipsum dolor sit amet.</p>
    <p class="texto-rojo fondo-amarillo">Lorem ipsum dolor sit amet.</p>
</article>
```

Resultado:
<style>
#example-4 .texto-rojo {
    color: red;
}
#example-4 .fondo-amarillo {
    background: yellow;
}
</style>
<div id="example-4" class="example">
    <article>
        <p class="texto-rojo">Lorem ipsum dolor sit amet.</p>
        <p class="fondo-amarillo">Lorem ipsum dolor sit amet.</p>
        <p class="texto-rojo fondo-amarillo">Lorem ipsum dolor sit amet.</p>
    </article>
</div>

#### Pseudo-clase

`:hover`, `:active`, `:link`, `:visited`, `:disabled`, `:readonly`


Referencia rápida de Selectores
---------------------------------------

### Selectores generales

| *Selector*            | *Ejemplo*              | *Descripción de ejemplo*                                                                                 |
| --------------------- | ---------------------- | -------------------------------------------------------------------------------------------------------- |
| `.clase`              | `.intro`               | Selecciona a todos los elementos con `class="intro"`                                                     |
| `.clase1.clase2`      | `.name1.name2`         | Selecciona todos los elementos con ambas clases `name1` y `name2` establecidos en su atributo `class`    |
| `.clase1 .clase2`     | `.name1 .name2`        | Selecciona todos los elementos con clase `name2` que sea descendiente de un elemento con clase `name1`   |
| `#id`                 | `#firstname`           | Selecciona el elemento con `id="firstname"`                                                              |
| `*`                   | `*`                    | Selecciona todos los elementos                                                                           |
| `elemento`            | `p`                    | Selecciona todos los elementos `<p>`                                                                     |
| `elemento.clase`      | `p.intro`              | Selecciona todos los elementos `<p class="intro">`                                                       |
| `elemento, elemento`  | `div, p`               | Selecciona todos los elementos `<div>` y `<p>`                                                           |
| `elemento elemento`   | `div p`                | Selecciona todos los elementos `<p>` dentro de elementos `<div>`                                         |
| `elemento > elemento` | `div > p`              | Selecciona todos los elementos `<p>` donde el padre es un elemento `<div>`                               |
| `elemento + elemento` | `div + p`              | Selecciona todos los elementos `<p>` son elementos colocados inmediatamente después de elementos `<div>` |
| `element1 ~ element2` | `p ~ ul`               | Selecciona cada elemento `<ul>` que sea precedido por un elemento `<p>`                                  |
| `[atributo]`          | `[target]`             | Selecciona todos los elementos con atributo `target`                                                     |
| `[atributo=valor]`    | `[target=_blank]`      | Selecciona todos los elementos con `target="blank"`                                                      |
| `[atributo~=valor]`   | `[title~=flor]`        | Selecciona todos los elementos con atributo título que contengan la palabra `"flor"`                     |
| `[atributo|=value]`   | `[lang|=en]`           | Selecciona todos los elementos con un atributo `lang` que inicien con `"en"`                             |
| `[atributo^=valor]`   | `a[href^="https"]`     | Selecciona cada elemento `<a>` donde el atributo `href` comience con `"https"`                           |
| `[atributo$=valor]`   | `a[href$=".pdf"]`      | Selecciona cada elemento `<a>` donde su atributo `href` termine con `".pdf"`                             |
| `[atributo*=valor]`   | `a[href*="w3schools"]` | Selecciona cada elemento `<a>` donde su atributo `href` contenga la subcadena `"w3schools"`              |

### Selectores por estado de los elementos

| *Selector*       | *Ejemplo*     | *Descripción de ejemplo*                                                  |
| ---------------- | ------------- | ------------------------------------------------------------------------- |
| `:target`        | `:target`     | Selecciona el elemento activo en el *#fragment" de la URL                 |
| `:hover`         | `a:hover`     | Selecciona los enlaces cuando el puntero esté sobre el elemento           |
| `:link`          | `a:link`      | Selecciona todos los enlaces que no han sido visitados                    |
| `:active`        | `a:active`    | Selecciona el hiperenlace cuando está presionado                          |
| `:visited`       | `a:visited`   | Selecciona todos los hiperenlaces visitados                               |
| `:focus`         | `input:focus` | Selecciona el elemento input que tiene el foco                            |
| `:empty`         | `p:empty`     | Selecciona todos los elementos `<p>` que estén vacíos (incluso sin texto) |
| `:not(selector)` | `:not(p)`     | Selecciona todos los elementos que no sean `<p>`                          |

### Selectores por ubicación en el DOM

| *Selector*             | *Ejemplo*             | *Descripción de ejemplo*                                                                                        |
| ---------------------- | --------------------- | --------------------------------------------------------------------------------------------------------------- |
| `:root`                | `:root`               | Selecciona el elemento raiz del documento                                                                       |
| `:lang(idioma)`        | `p:lang(es)`          | Selecciona todos los elementos `<p>` con un atributo de idioma `lang` igual a "es" (español)                    |
| `:first-child`         | `p:first-child`       | Selecciona cada elemento `<p>` que sea el primer hijo de su padre                                               |
| `:first-of-type`       | `p:first-of-type`     | Selecciona todos los elementos `<p>` que sean el primer elemento `<p>` de su padre                              |
| `:nth-child(n)`        | `p:nth-child(2)`      | Selecciona cada elemento `<p>` que sea el segundo elemento hijo de su padre                                     |
| `:nth-of-type(n)`      | `p:nth-of-type(2)`    | Selecciona cada elemento `<p>` que sea segundo elemento `<p>` de su padre                                       |
| `:nth-last-of-type(n)` | `p:last-of-type(2)`   | Selecciona cada elemento `<p>` que sea penúltimo elemento `<p>` de su padre (segundo en reversa desde el final) |
| `:nth-last-child(n)`   | `p:nth-last-child(2)` | Selecciona cada elemento `<p>` que sea penúltimo elemento de su padre (segundo en reversa desde el final)       |
| `:last-of-type`        | `p:last-of-type`      | Selecciona cada elemento `<p>` que sea el último elemento `<p>` de su padre                                     |
| `:last-child`          | `p:last-child`        | Selecciona cada elemento `<p>` que sea el último hijo de su padre                                               |
| `:only-of-type`        | `p:only-of-type`      | Selecciona cada elemento `<p>` que sea el único elemento `<p>` de su padre                                      |
| `:only-child`          | `p:only-child`        | Selecciona cada elemento `<p>` que sea el único hijo de su padre                                                |

### Selectores para formularios

| *Selector*       | *Ejemplo*             | *Descripción de ejemplo*                                                                                                       |
| ---------------- | --------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `:enabled`       | `input:enabled`       | Selecciona todos los elementos `<input>` que estén habilitados.                                                                |
| `:disabled`      | `input:disabled`      | Selecciona todos los `<input>` que estén deshabilitados                                                                        |
| `:required`      | `input:required`      | Selecciona elementos `<input>` con el atributo `required`                                                                      |
| `:optional`      | `input:optional`      | Selecciona elementos `<input>` sin el atributo `required`                                                                      |
| `:checked`       | `input:checked`       | Selecciona un input cuando esté marcado (aplica para `type=radio` y `type=checkbox`)                                           |
| `:indeterminate` | `input:indeterminate` | Selecciona los elementos input que estén en estado indeterminado (checkbox intermedia <input type="checkbox" indeterminate />) |
| `:in-range`      | `input:in-range`      | Selecciona los elementos `<input>` cuando su valor esté en el rango de `min` y `max`                                           |
| `:out-of-range`  | `input:out-of-range`  | Selecciona elementos `<input>` con un valor fuera del rango de `min` y `max`                                                   |
| `:valid`         | `input:valid`         | Selecciona todos los elementos `<input>` con un valor válido                                                                   |
| `:invalid`       | `input:invalid`       | Selecciona todos los elementos `<input>` con un valor invalido                                                                 |
| `:read-only`     | `input:read-only`     | Selecciona elementos `<input>` que NO tengan el atributo `readonly` especificado                                               |
| `:read-write`    | `input:read-write`    | Selecciona elementos `<input>` que tengan el atributo `readonly` especificado                                                  |
| `:default`       | `input:default`       | Selecciona el `<input>` predeterminado (aplica a `button`, `input[type=checkbox]`, `input[type=radio]` y `option`)             |

Referencia rápida de selectores CSS [W3Schools](https://www.w3schools.com/cssref/css_selectors.asp)