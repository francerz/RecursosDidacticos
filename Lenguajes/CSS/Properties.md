Propiedades
=================================================

## Propiedad `display`
*(<https://developer.mozilla.org/en-US/docs/Web/CSS/display>)*

Valores: `block`, `inline`, `table`, `table-row-group`, `table-header-group`,
`table-footer-group`, `table-row`, `table-cell`, `table-column-group`, `table-column`,
`table-caption`, `none`, `inline-block`, `inline-table`, `inline-flex`, `inline-grid`, `flex`, `grid`

Define la forma en que se despliega el contenido de un elemento. Existen varios
posibles valores para esta propiedad pero lo más destacados son: `none`, `inline`,
`inline-block` e `block`. Recientemente se añadieron los valores `flex` y `grid`
que dada su extensión se dejan para otro artículo.

El valor `none` se utiliza para ocultar por completo a un elemento de la
interfaz de usuario.

Ejemplo de visualización de display en sus valores destacados.

```css
.inline {
    display: inline;
    background: cyan;
}
.inline-block {
    display: inline-block;
    background: green;
}
.block {
    display: block;
    background: yellow;
}
```
<style>
#example-display .inline {
    display: inline;
    background: cyan;
}
#example-display .inline-block {
    display: inline-block;
    background: green;
}
#example-display .block {
    display: block;
    background: yellow;
}
</style>
<div id="example-display">
    A continuación se incluye tipo en diferentes tipos de contenedores por
    ejemplo <span class='inline'>el texto que utiliza `display:inline` se 
    muestra siguiendo la secuencia del renglón de texto</span>, mientras que
    <span class='inline-block'>`inline-block` produce un bloque el cual no se
    segmenta en renglones</span> y mantiene todo el contenido en un mismo recuadro
    y por último el <span class='block'>`display:block` que crea su propio bloque
    independiente, por lo regular abarcando todo el ancho del contenedor e
    impidiendo que otros elementos a los costados ocupen lugar</span>
</div>

## Propiedad `position`
*(<https://developer.mozilla.org/en-US/docs/Web/CSS/position>)*

Valores: `static`*(default)*, `relative`, `absolute`, `fixed`, `sticky`

Define la forma en que el elemento será posicionado en el documento, utilizando
las propiedades `top`, `left`, `right` y `bottom`.

### Tipos de posicionamiento

* Un **elemento posicionado** es un elemento cuyo valor de `position` sea `relative`, `absolute`, `fixed` o `sticky`.
* Un **elemento posicionado relativamente** es un elemento que valor de `position` es `relative`. Las propiedades `top` y `bottom` especifican el margen vertical de su posición nromal; las propiedades `left` y `right` especifican el margen horizontal.
* Un **elemento posicionado absolutamente** es aquel cuyo valor de `position` es `absolute` o `fixed`. Las propiedades `top`, `right`, `bottom` y `left` especifican los margenes del elemento que contiene el bloque. Si el elemento tien margenes, estos se añaden al los valores de los atributos.
* Un **elemento posicionado pegajoso** es un elemento cuyo valor de `position` es `sticky`. Se trata de un elemento posicionado relativamente hasta que su bloque contenedor cruza un humbral (como el valor puesto en `top` diferente a auto) Manteniendo su posición fija en la interfaz hasta llegar al extremo opuesto de su bloque contenedor.