<style>
  .html-example {
    border: 1px solid #888;
    margin: 0px 16px;
    padding: 0px 8px;
    background-color: rgba(128,128,128, 0.2);
  }
</style>
Introducción a HTML
===================

El lenguaje de marcas de hipertexto ***HyperText Markup Language*** se utiliza,
de manera estandarizada, para la elaboración de páginas web, las cuales pueden
contener texto, imagenes, vídeos, juegos y más.

La organización a cargo del lenguaje es el W3C *World Wide Web Consortium*.

Es considerado como el lenguaje web más importante, y ha sido declarado para el
diseño y visualización de páginas web. Actualmente todos los navegadores
soportan la representación gráfica de estos documentos.

La función principal de HTML consiste en la representación semántica de los
componentes de una página web, además de la incrustación de diferentes elementos
mediante referencias y vínculos a los elementos externos, por ejemplo: imágenes,
vídeos, scripts, recursos, etc. Los navegadores se encargan de interpretar todos
los elementos y unirlos en forma de una representación única del documento.

Sintaxis
-------------
El lenguaje esta basado en SGML por lo que utiliza estructuras en forma de
etiquetas, las cuales se identifican utilizando corchetes angulares `<` y `>`.

Las etiquetas tienen la siguiente estructura:

```html

<!-- Etiqueta simple -->
<etiqueta />

<!-- Etiqueta con apetura y cierre -->
<etiqueta>Contenido de la etiqueta</etiqueta>

<!-- Etiqueta con atributos modificadores -->
<etiqueta atributo="valor" otro="valorcito" />

<!-- Etiqueta con atributos y contenido -->
<etiqueta atributo="valor">
    Contenido de la etiqueta
</etiqueta>
```

Documento
------------

Un documento HTML tiene una estrcutura básica fundamental, la cual se muestra a
continuación:

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>Título del documento</title>
    </head>
    <body>
        <!-- Contenido del documento HTML -->
    </body>
</html>
```

Descripción de los elementos:

* `<!DOCTYPE html>`: permite idetificar el tipo de contenido del documento.
* `<html>`: La etiqueta raiz estándar de todo documento HTML, donde se colocará
  todo el contenido de la página.
* `<head>`: Es la parte de un documento HTML que no se muestra por el navegador
  cuando la página se carga, pero contiene información relativa al contenido.
  Es el lugar adecuado para colocar el título, enlaces a CSS, favicon, y otros
  metadatos.
* `<meta charset="utf-8" />`: Con esta etiqueta se especifica la codificación
  de los caracteres del documento.
* `<title>`: Define el título del documento, el cual se muestra en la barra de
  título del navegador, o en la pestaña de la página. Sólo puede contener texto,
  las etiquetas en el interior, son ignoradas.
* `<body>`: Representa el contenido de un documento HTML. Sólo puede existir un elemento `body` en el documento.

Etiquetas más comunes
---------------------

### Encabezados

Los encabezados representan seis niveles de encabezado del documento, el `<h1>`
es el más importante, y `<h6>`, el menos importante. Un elemento de encabezado
describe brevemente el tema de la sección que presenta. Generalmente el orden
y jerarquía de los encabezados se utiliza para construir tablas de contenidos
automáticas.

> **NOTA:**
> * No se deben usar diferentes etiquetas para cambiar los tamaños de la fuente,
> para eso se debe utilizar la propiedad `font-size` en CSS.
> * Evitar omitir niveles de encabezado: siempre comenzar con `<h1>`, continuar
> con `<h2>`, seguido de `<h3>` y así sucesivamente.

El siguiente código muestra todos los niveles de encabezado.
```html
<h1>Encabezado nivel 1</h1>
<h2>Encabezado nivel 2</h2>
<h3>Encabezado nivel 3</h3>
<h4>Encabezado nivel 4</h4>
<h5>Encabezado nivel 5</h5>
<h6>Encabezado nivel 6</h6>
```

El resultado del código.

<div class='html-example'>
  <h1>Encabezado nivel 1</h1>
  <h2>Encabezado nivel 2</h2>
  <h3>Encabezado nivel 3</h3>
  <h4>Encabezado nivel 4</h4>
  <h5>Encabezado nivel 5</h5>
  <h6>Encabezado nivel 6</h6>
</div>
---

### Párrafos

Son elementos que se representan como bloques de texto separados de bloques
adyacentes por espacios vacíos o por sangría en la primera línea.

Los párrafos son *elementos a nivel de bloque*, y se cerrarán automáticamente si
otro elemento a nivel de bloque se encuentra antes de la etiqueta de cierre.

```html
<p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Libero quos
  adipisci consectetur? Officia repudiandae illum consectetur tenetur error
  aperiam reprehenderit explicabo natus saepe ratione! Reiciendis doloribus
  inventore magnam blanditiis doloremque!</p>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Esse dicta odit
  reprehenderit, minus sapiente saepe debitis blanditiis voluptatum accusantium
  nisi?</p>
```

El código anterior se representa de la siguiente manera:

<div class='html-example'>
  <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Libero quos
    adipisci consectetur? Officia repudiandae illum consectetur tenetur error
    aperiam reprehenderit explicabo natus saepe ratione! Reiciendis doloribus
    inventore magnam blanditiis doloremque!</p>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Esse dicta odit
    reprehenderit, minus sapiente saepe debitis blanditiis voluptatum accusantium
    nisi?</p>
</div>

Se pueden colocar otros elementos dentro del parrafo, siendo más comunes
las etiquetas de contenido semántico.

```html
<p>El lenguaje <strike>XML</strike> HTML (<em>HyperText Markup Language</em>
permite definir <strong>documentos web</strong>.</p>
```

<div class="html-example">
  <p>El lenguaje <strike>XML</strike> HTML (<em>HyperText Markup Language</em>
  permite definir <strong>documentos web</strong>.</p>
</div>

### Listas

Mucho del contenido se puede representar mediante listas, por lo que HTML cuenta
con elementos especiales para definirlas. Existen dos tipos de listas comunes,
identificadas por dos tipos de elementos.

* **Listas no ordenadas.** Son aquellas que el orden de los elementos no es
  relevante, como una lista de tareas. Estas se identifican con la etiqueta `<ul>`
  (*unordered list*).
* **Listas ordenadas.** Son aquellas en la que el órden sí es relevante, como
  en un algoritmo. Estas se identifican con la etiqueta `<ol>` (*ordered list*).

Cada uno de los elementos de la lista, independientemente del tipo, se coloca en
un elemento con la etiqueta `<li>` (*list item*).

#### Ejemplo de lista no ordenada
```html
<p>Las carreras del Tecnológico Nacional de México Campus Colima son:</p>
<ul>
  <li>Arquitectura</li>
  <li>Contador Público</li>
  <li>Ingeniería Ambiental</li>
  <li>Ingeniería Bioquímica</li>
  <li>Ingeniería en Gestión Empresarial</li>
  <li>Ingeniería Industrial</li>
  <li>Ingeniería Informática</li>
  <li>Ingeniería Mecatrónica</li>
  <li>Ingeniería en Sistemas Computacionales</li>
  <li>Licenciatura en Administración</li>
</ul>
```

<div class='html-example'>
  <p>Las carreras del Tecnológico Nacional de México Campus Colima son:</p>
  <ul>
    <li>Arquitectura</li>
    <li>Contador Público</li>
    <li>Ingeniería Ambiental</li>
    <li>Ingeniería Bioquímica</li>
    <li>Ingeniería en Gestión Empresarial</li>
    <li>Ingeniería Industrial</li>
    <li>Ingeniería Informática</li>
    <li>Ingeniería Mecatrónica</li>
    <li>Ingeniería en Sistemas Computacionales</li>
    <li>Licenciatura en Administración</li>
  </ul>
</div>

#### Ejemplo de lista ordenada

```html
<p>Cómo...</p>
<ol>
  <li>Primer paso</li>
  <li>Segundo paso</li>
  <li>Tercer paso</li>
</ol>
```

<div class="html-example">
  <p>Cómo...</p>
  <ol>
    <li>Primer paso</li>
    <li>Segundo paso</li>
    <li>Tercer paso</li>
  </ol>
</div>

### Hiperenlaces

Los hiperenlaces, también conocidos como vínculos, permiten conectar distintos
documentos HTML, conformando el componente fundamental de la web. Para definirlo
se utiliza la etiqueta `<a>` que corresponde a la palabra *anchor* (ancla).

```html
Aprender HTML <a href="https://developer.mozilla.org/es/docs/Learn/HTML">aquí</a>.
```

<div class="html-example">
Aprender HTML <a href="https://developer.mozilla.org/es/docs/Learn/HTML">aquí</a>.
</div>

### Tablas

Para la representación de datos es bastante utilizar estructuras que faciliten
la lectura, comprensión y organización de los contenidos.