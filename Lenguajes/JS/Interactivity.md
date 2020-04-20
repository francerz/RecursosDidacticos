Interactividad con JavaScript
=======================================

- [Interactividad con JavaScript](#interactividad-con-javascript)
  - [Evento `click`](#evento-click)
    - [Utilizando el atributo `onclick`](#utilizando-el-atributo-onclick)
    - [Utilizando la API Web estandar `addEventListener`](#utilizando-la-api-web-estandar-addeventlistener)
    - [Utilizando la librería jQuery](#utilizando-la-librer%c3%ada-jquery)
  - [Otros eventos de JavaScript](#otros-eventos-de-javascript)

Una de las características principales del lenguaje JavaScript es que permite
añadir interactividad a los páginas web, de manera que el usuario pueda
interactuar directamente con la interfaz, sin necesidad de recargar las páginas
para cada acción del usuario.

Evento `click`
---------------------------------------

La interacción más básica que existe, es el clic, en la cual mediante un
dispositivo señalador, dígase: ratón, pluma o dedo, realizan una acción sobre
el elemento.

Normalmente el evento `click` suele asociarse con botones, sin embargo en HTML,
es posible adjuntar este evento a casi todos los elementos de la interfaz.

### Utilizando el atributo `onclick`

La primera técnica de agregar un evento es utilizando el atributo del evento en
la etiqueta del elemento al que se desea asignar.

Ejemplo:
```js
function accionClick() {
    alert("Se hizo clic en el botón");
}
```
```html
<button onclick="accionClick()">Hacer Clic</button>
```

> NOTA:
> Esta técnica de añadir el evento `click` aunque es muy sencilla, no es la más
> recomendable, puesto que se pierde la separación entre el código de
> presentación y la estructura de los documentos.
> Las próximas técnicas mantienen la separación de los componentes, al asignar
> los eventos directamente utilizando JavaScript.

### Utilizando la API Web estandar `addEventListener`

La técnica estandar para agregar los eventos es empleando el método
`addEventListener` que permite especificar el tipo de evento y una función
controladora del evento.

Ejemplo:
```js
function accionClick(evt) {
    alert("Se hizo clic en el botón");
}

let boton = document.getElementById("miBoton");
boton.addEventListener("click", accionClick);
```
```html
<button id="miBoton">Hacer Click</button>
```

Es **MUY IMPORTANTE** que este código se ejecute después de que el elemento
`button#miBoton` se haya registrado en el DOM (Document Object Model) de lo
contrario no funcionará.

La primera forma de lograr esto es colocando todos los `<script>` al final
de la carga del documento.

La segunda forma consiste en ejecutar todo dentro del evento `DOMContentLoaded`
del objeto `window` o `document`. De esta forma se asignará el evento una vez
que se haya completado la generación del DOM.

Ejemplo:
```js
function accionClick(evt) {
    alert("Se hizo clic en el botón");
}
window.addEventListener("DOMContentLoaded", function(e) {
    let boton = document.getElementById("miBoton");
    boton.addEventListener("click", accionClick);
});
```

### Utilizando la librería jQuery

La utilización de la librería jQuery simplifica muchas de las acciones comunes
de manipulación con JavaScript. Una de las funcionalidades más comunes es la
asignación de eventos.

El siguiente código es equivalente al ejemplo anterior:
```js
function accionClick(evt) {
    alert("Se hizo clic en el botón");
}
$(function(e) {
    $('#miBoton').on("click", accionClick);
});
```

Como es posible apreciar, se reduce significativamente la longitud del código
para asignar el evento.

Otra de las ventajas de utilizar la librería es que contiene funcionalidades
adicionales que no están integradas o estandarizadas por la API Web. Por lo
que existe una mayor garantía de compatibilidad con diferentes navegadores.

Por ejemplo, el método equivalente a `addEventListener` en Internet Explorer es
`attachEvent`, jQuery hace las adaptaciones de compatibilidad de manera
transparente.

Otros eventos de JavaScript
---------------------------------------

Existe una gran varidad de eventos disponibles en JavaScript, proporcionando
una amplia variedad de acciones del usuario. Estos eventos van desde acciones
concretas con ratón y teclado, hasta interacciones con dispositivos multimedia
como lo es la cámara y micrófono.

* **Eventos del Ratón**  
  `click`, `dblclick`, `mousedown`, `mouseup`, `mousemove`, `mouseenter`,
  `mouseleave`, `mouseover`, `mouseout`  
  <https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent>
* **Eventos de dispositivos señaladores**  
  `pointerenter`, `pointerdown`, `pointermove`, `pointerup`, `pointercancel`,
  `pointerout`, `pointerleave`, `gotpointercapture`, `lostpointercapture`  
  <https://developer.mozilla.org/en-US/docs/Web/API/PointerEvent>
* **Eventos del teclado**  
  `keydown`, `keypress`, `keyup`  
  <https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent>
* **Eventos de arrastrar y soltar**  
  `drag`, `dragend`, `dragenter`, `dragexit`, `dragleave`, `dragover`,
  `dragstart`, `drop`  
  <https://developer.mozilla.org/en-US/docs/Web/API/DragEvent>
* **Eventos del portapapeles**  
  `cut`, `copy`, `paste`  
  * <https://developer.mozilla.org/en-US/docs/Web/API/Element/cut_event>
  * <https://developer.mozilla.org/en-US/docs/Web/API/Element/copy_event>
  * <https://developer.mozilla.org/en-US/docs/Web/API/Element/paste_event>
* **Otros varios eventos**
  <https://developer.mozilla.org/en-US/docs/Web/API/Event>