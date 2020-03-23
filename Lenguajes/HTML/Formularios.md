Formularios
=======================================

Los formularios en HTML permiten al usuario interactuar con los sitios web,
Los formularios permiten a los usuarios introducir datos, los cuales,
generalmente son enviados a un servidor web, para procesamiento y almacenamiento.
También pueden ser utilizados del lado del servidor, para inmediatamente
actualizar el contenido en la interfaz de alguna manera (por ejemplo, agregar
otro elemento a una lista, o mostrar u ocultar parte de la interfaz de usuario).

Un formulario web en HTML está constituido por uno o más **controles de formulario**
(algunas veces denominados **widgets**), y algunos elementos adicionales que
ayudan a la estrucutra general del formulario &mdash; a menudo son referidos como
**formularios HTML**.
Los controles pueden ser campos de una sola línea o multilinea, listas
desplegables, botones, cuadros de verificación, botones de radio, y la mayoría
se crean utilizando el elemento `<input>`, a pesar de existen algunos otros
elementos también.

Los controles de los formularios también pueden ser programados para forzar
formatos específicos, o valores para se introducidos **validación de formularios**,
y son emparejados con etiquetas de texto, que describen el propósito, tanto para
usuarios normales, como invidentes.

Diseño de un formulario
---------------------------------------
Antes de comenzar a codificar, siempre es mejor detenerse y tomarse el tiempo
para pensar acerca del formulario. Siempre es recomendalbe diseñar un boceto
(*mockup*) que ayude a definir el conjunto adecuados de datos que se solicitan
al usuario.
Desde el punto de vista de la experiencia de usuario (UX), es importante recordar
que entre más extenso sea el formulario, se corre más riesgo de fustrar a la
gente y peder a los usuarios. Debe mantenerse simple y enfocado: pregunta sólo
los datos que son absolutamente requeridos.

Diseñar formularios es un paso importante cuando se van a crear sitios o
aplicaciones. Existen algunas guías sobre experiencia de usuario en formularios.

* https://www.smashingmagazine.com/2018/08/ux-html5-mobile-form-part-1/
* https://www.smashingmagazine.com/2011/11/extensive-guide-web-form-usability/
* https://www.uxmatters.com/mt/archives/2012/05/7-basic-best-practices-for-buttons.php
* https://www.uxmatters.com/mt/archives/2010/03/pagination-in-web-forms-evaluating-the-effectiveness-of-web-forms.php
* https://xd.adobe.com/ideas/principles/web-design/best-practices-form-design/

La elaboración de los bocetos no requiere el uso de herramientas especiales,
pueden realizarse con cosas tan simples como lapiz y papel, pizarrones,
herramientas de dibujo básico, etc. El propósito se ilustrar la información
requerida, y su disposición.

> **Consejos**
> 
> La elaboración del bosquejo del formulario, permite tomar decisiones sobre
> la forma en que se mostrará el contenido al usuario, por lo que se recomienda
> tener en cuenta lo siguiente:
> * Ordenar los datos campos de manera lógica y congruente.
>   Por ejemplo, es más congruente: Nombre(s), Primer apellido, Segundo apellido,
>   Fecha de nacimiento, Estado, Municipio, Colonia, Calle y Número exterior.
>   Que poner: Estado, Municipio, Calle, Número, Colonia, Nombre(s),
>   Fecha de nacimiento, Primer apellido y Segundo apellido.
> * Agrupar campos con información común. Similar al consejo anterior, siempre
>   es mejor tener una separación clara de los contenidos solicitados.
>   Por ejemplo:
>   * Información personal: Nombre(s), Primer apellido, Segundo apellido y
>     Fecha de nacimiento.
>   * Domicilio: Estado, Municipio, Colonia, Calle y Número exterior.
> * El orden de los campos es en el que la mayoría de los usuarios capturan
>   la información, por lo que si el contenido es dinámico debe tomarse que
>   los requisitos sean atendidos primero.
>   Por ejemplo, si al seleccionar el estado, se muestran los municipios.
>   Entonces en ese orden deben aparecer.

Haciendo un formulario
---------------------------------------

Para crear el formulario se utilizarán los siguientes elementos: `<form>`,
`<label>`, `<input>`, `<textarea>` y `<button>`.

### El elemento `<form>`

Todos los elementos `<form>` lucen de la siguiente manera:

```html
<form method="POST" action="/destino-formulario">

</form>
```

Este elemento define un formulario. Es un tipo de contenedor como `<section>` o
`<footer>`, pero específico para contener formularios; también soporta algunos
atributos específicos para configurar la manera en que se comporta. Todos sus
atributos son opcionales, pero la práctica estándar siempre establece por lo
menos los atributos `method` y `action`:

* El atributo `method` cuál método HTTP se utiilzará para enviar los datos (por
  lo general `GET` o ``POST`).
* El atributo `action` define la ubicación (URL) donde la información del
  formulario será recibida cuando este sea enviado.

### Los elementos `<label>`, `<input>` y `<textarea>`

El presente ejemplo corresponde a un formulario de contacto, en el cual existen
tres campos de texto y cada uno con su respectivo `<label>`:

* El campo de entrada para el nombre un un campo de texto de una sola línea.
* El campo de entrada para el correo electronico, es un campo de tipo email.
* el campo de entrada para el mensaje que es un `<textarea>`, que es un cuadro
  de texto multilínea.

```html
<form method="POST" action="/contacto">
    <div>
        <label for="txtNombre">Nombre:</label>
        <input type="text" id="txtNombre" name="nombre" />
    </div>
    <div>
        <label for="txtCorreo">Correo electrónico:</label>
        <input type="email" id="txtCorreo" name="correo" />
    </div>
    <div>
        <label for="txtMensaje">Mensaje:</label>
        <textarea id="txtMensaje" name="mensaje"></textarea>
    </div>
    <div>
        <button type="submit">Enviar mensaje</button>
    </div>
</form>
```

Para usabilidad y accesibilidad, se incluye una etiqueta explícita para
cada control del formulario. Nótese que el atributo `for` de todas las `<label>`
tienen el valor del `id` correspondiente al control asociado &mdash; esto es
cómo se asocia un control a su etiqueta.

Hay un gran beneficio de hacer esto &mdash; asocia la etiqueta con el control
del formulario, permitiendo a los usuarios que utilizan mouse, trackpad y
dispositivos táctiles puedan hacer clik en la etiqueta para activar el control
correspondiente, también proporciona un nombre accesible para lectores de
pantalla.

En el elemento `<input>`, el atributo más importante es el `type`. Este atributo
define la manera en la que el elemento `<input>` aparece y se comporta. Existen
diferentes tipos de comportamientos, algunos de estos son:
[`text`](./Tags/Input.md#type-text),
[`password`](./Tags/Input.md#type-password),
[`hidden`](./Tags/Input.md#type-hidden),
[`number`](./Tags/Input.md#type-number),
[`date`](./Tags/Input.md#type-date),
[`time`](./Tags/Input.md#type-time),
[`checkbox`](./Tags/Input.md#type-checkbox),
[`radio`](./Tags/Input.md#type-radio),
[`file`](./Tags/Input.md#type-file),
etc.

Por el momento basta con decir que cada uno de estos tipos permite a los
navegadores adaptar su comportamiento dependiendo de las características
del dispositivo, además de permitir acciones de autocompletado congruentes
con el contenido.

El tipo `text` se utiliza para representar texto en general, en cualquier
formato y contenido. Sólo permite una línea de texto.

El tipo `email` permite la captura de una dirección de correo electrónico,
hace la validación de que el contenido corresponda al formato y en el caso
de utilizar teclados virtuales, este mostrará accesos cortos a caracteres
comunes, por ejemplo el símbolo `@`.

Por último, pero no menos importante, está el elemento `<textarea>`.
Como puede notarse, a diferencia del elemento `<input>`, el elemento
`<textarea></textarea>` requiere una etiqueta de cierre, puesto que el contenido
del mismo se debe incluir entre estas dos etiquetas.

```html
<input type="text" value="Texto contenido dentro del elemento" />

<textarea>Texto contenido dentro del elemento</textarea>
```

### El elemento `<button>`

La revisión del formulario está casi completa, sólo falta un elemento importante.
La opción para permitir al usuario enviar o "someter" los datos una vez que se
haya llenado el formulario. Esto se hace utilizando la etiqueta `<button>`

```html
<button type="submit">Enviar mensaje</button>
```

El elemento `<button>` también acepta el atributo `type` &mdash; este acepta uno
de tres valores: `submit`, `reset`, `button`.

* Un clic en un botón `submit` (valor predeterminado) envía los datos del
  formulario a la página web donde se define el atributo `action` del elemento
  `<form>`.
* Un clic en un botón `reset` restablece todos los controles a su valor
  predeterminado inmediatamente.
  *Desde el punto de vista de la Experiencia de Usuario, esto es considerado una
  mala práctica, por lo que debe evitarse utilizar este tipo de botón, a menos
  de que se tenga una buena razón para incluir uno.*
* Un clic en un botón `button` hace... absolutamente nada. Es bastante útil para
  hacer botones personalizados &mdash; se puede definir su funcionamiento
  utilizando JavaScript.

> **Nota**
> También se puede utilizar el elemento `<input>` con el tipo correspondiente
> para crear un botón, por ejemplo `<input type="submit">`. La principal ventaja
> de utilizar el elemento `<button>` es que el `<input>` sólo permite texto
> plano en sus etiquetas, mientras que el `<button>` permite contenido HTML.

Referencias
---------------------------------------
* https://developer.mozilla.org/en-US/docs/Learn/Forms/Your_first_form
* https://developer.mozilla.org/en-US/docs/Learn/Forms/How_to_structure_a_web_form