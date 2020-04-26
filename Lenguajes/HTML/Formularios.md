Formularios
=======================================

- [Formularios](#formularios)
  - [Diseño de un formulario](#dise%c3%b1o-de-un-formulario)
  - [Haciendo un formulario](#haciendo-un-formulario)
    - [El elemento `<form>`](#el-elemento-form)
    - [Los elementos `<label>`, `<input>` y `<textarea>`](#los-elementos-label-input-y-textarea)
      - [Etiqueta `<input>`](#etiqueta-input)
        - [Atributo `type`](#atributo-type)
        - [Atributo `value`](#atributo-value)
        - [Atributos `min` y `max`](#atributos-min-y-max)
        - [Atributos `maxlength` y `minlength`](#atributos-maxlength-y-minlength)
        - [Atributo `placeholder`](#atributo-placeholder)
        - [Atributo `inputmode`](#atributo-inputmode)
        - [Atributo `list`](#atributo-list)
        - [Atributo `autofocus`](#atributo-autofocus)
        - [Atributo `readonly`](#atributo-readonly)
        - [Atributo `disabled`](#atributo-disabled)
        - [Atributo `required`](#atributo-required)
        - [Atributo `pattern`](#atributo-pattern)
    - [El elemento `<select>`](#el-elemento-select)
    - [El elemento `<button>`](#el-elemento-button)
  - [Referencias](#referencias)

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
Como puede notarse, a diferencia del elemento `<input>` cuyo contenido se
incrusta en el atributo `value`, el elemento `<textarea></textarea>` requiere
una etiqueta de cierre, puesto que el contenido del mismo se debe incluir entre
estas dos etiquetas.

```html
<input type="text" value="Texto contenido dentro del elemento" />

<textarea>Texto contenido dentro del elemento</textarea>
```

#### Etiqueta `<input>`

La etiqueta `<input>` es sumamente versatil, puesto que su apariencia y
comportamiento cambian drásticamente modificando el atributo `type`. Y dada
esa versatilidad, cuenta con atributos que permiten modificar su comportamiento,
límites y funcionalidad.

##### Atributo `type`



##### Atributo `value`

El atributo `value` permite establecer el valor actual del `<input>`, comunmente
utilizado para establecer el valor predeterminado de un campo, o los valores
previamente capturados en un registro.

```html
<label for="txtTitulo">Título</label>
<input id="txtTitulo" type="text" name="titulo" value="Fundamentos de Bases de Datos" />
```

<section class="example">
  <label for="txtTitulo">Título</label>
  <input id="txtTitulo" type="text" name="titulo" value="Fundamentos de Bases de Datos" />
</section>

##### Atributos `min` y `max`

Los atributos `min` y `max` delimitan en rango de valores que puede contener un
control de tipo numérico, es decir, aquellos cuyo atributo `type` sea `number` o
`range`.
También funciona con los controles de tipo fecha y hora, es decir, aquellos cuyo
atributo `type` sea `date`, `month`, `week`, `time` o `datetime-local`.

```html
<label for="numDuracion">Duración(en minutos)</label>
<input id="numDuracion" type="number" name="duracion" value="30" min="1" max="60" />
<label for="rngCalificacion">Calificación</label>
<input id="rngCalificacion" type="range" name="calificacion" min="70" max="100" />
```

<section class="example">
  <label for="numDuracion">Duración(en minutos)</label>
  <input id="numDuracion" type="number" name="duracion" value="30" min="1" max="60" />
  <label for="rngCalificacion">Calificación</label>
  <input id="rngCalificacion" type="range" name="calificacion" min="70" max="100" />
</section>

```html
<label for="dateInicio">Fecha de inicio</label>
<input id="dateInicio" type="date" name="fecha_inicio" value="2020-04-25" min="2020-04-25" max="2020-07-17" />
<label for="timeInicio">Hora de inicio</label>
<input id="timeInicio" type="time" name="hora_inicio" value="09:00" min="07:00" max="18:00" />
```

<section class="example">
  <label for="dateInicio">Fecha de inicio</label>
  <input id="dateInicio" type="date" value="2020-04-25" min="2020-04-25" max="2020-07-17" />
  <label for="timeInicio">Hora de inicio</label>
  <input id="timeInicio" type="time" name="hora_inicio" value="09:00" min="07:00" max="18:00" />
</section>

##### Atributos `maxlength` y `minlength`

Estos atributos permiten delimitar la cantidad de caracteres que puede tener en
su contenido, esto es particularmente útil para prevenir el desbordamiento de
registros en la base de datos.

El dato R.F.C. (Registro Federal de Contribuyentes) en México tiene una longitud
de 12 caracteres para personas morales (sociedades mercantiles) y de 13 para
personas físicas. Por lo tanto se quiere restringir que su longitud mínima
sea de 12 y la máxima de 13.

```html
<label for="txtRFC">R.F.C.</label>
<input id="txtRFC" type="text" name="rfc" minlength="12" maxlength="13" />
```

<section class="example">
  <label for="txtRFC">R.F.C.</label>
  <input id="txtRFC" type="text" name="rfc" minlength="12" maxlength="13" />
</section>

##### Atributo `placeholder`

El atributo `placeholder` permite colocar un texto predefinido y diferente al
valor del `<input>`.

Se recomienda utilizarlo para dar indicaciones adicionales al usuario, así como
en la ejemplificación de entradas complejas, indicando que se trata sólo de un
ejemplo y no un valor predefinido.

```html
<label for="txtTitulo">Título</label>
<input id="txtTitulo" type="text" name="titulo" placeholder="Introduzca del título del libro" />
<label for="txtAutores">Autores</label>
<input id="txtAutores" type="text" name="autores" placeholder="Ejemplo: Silberschatz, Abraham; Korth, Henry F.; Sudarshan, S." />
```

<section class="example">
  <label for="txtTitulo">Título</label>
  <input id="txtTitulo" type="text" name="titulo" placeholder="Introduzca del título del libro" />
  <label for="txtAutores">Autores</label>
  <input id="txtAutores" type="text" name="autores" placeholder="Ejemplo: Silberschatz, Abraham; Korth, Henry F.; Sudarshan, S." />
</section>

##### Atributo `inputmode`

El atributo `inputmode` Permite a los navegadores identificar el tipo de teclado
virtual que debe utilizarse cuando se edite el elemento y su contenido.

Los valores permitidos son: `none`, `text`, `tel`, `url`, `email`, `numeric`,
`decimal` y `search`.

> Esta configuración se establece automáticamente en los elementos `<input>`
> cuando se establece su atributo `type` equivalente.

```html
<label for="txtCP">Código Postal</label>
<input id="txtCP" type="text" name="codigo_postal" inputmode="numeric" />
```

<section class="example">
  <label for="txtCP">Código Postal</label>
  <input id="txtCP" type="text" name="codigo_postal" inputmode="numeric" />
</section>

##### Atributo `list`

El atributo `list` permite identificar un elemento `<datalist>`, ubicado en el
mismo documento, a partir de su atributo `id`.

El elemento `<datalist>` proporciona una lista de valores predefinidos que se
sugieren al usuario para el elemento. <em>Sólo se muestran valores del atributo
que sean compatibles con el `type` del elemento `<input>` al que se asigna</em>.

```html
<label for="txtMunicipio">Municipio</label>
<input id="txtMunicipio" type="text" list="lstMunicipios" />
<datalist id="lstMunicipios">
  <option value="Armería">
  <option value="Colima">
  <option value="Comala">
  <option value="Coquimatlán">
  <option value="Cuauhtemoc">
  <option value="Ixtlahuacán">
  <option value="Manzanillo">
  <option value="Minatitlán">
  <option value="Tecomán">
  <option value="Villa de Álvarez">
</datalist>
```

<section class="example">
  <label for="txtMunicipio">Municipio</label>
  <input id="txtMunicipio" type="text" list="lstMunicipios" />
  <datalist id="lstMunicipios">
    <option value="Armería"></option>
    <option value="Colima"></option>
    <option value="Comala"></option>
    <option value="Coquimatlán"></option>
    <option value="Cuauhtemoc"></option>
    <option value="Ixtlahuacán"></option>
    <option value="Manzanillo"></option>
    <option value="Minatitlán"></option>
    <option value="Tecomán"></option>
    <option value="Villa de Álvarez"></option>
  </datalist>
</section>

> **Nota**  
> Este atributo sirve cuando los valores presentados son sugeridos, pero su
> valor puede ser modificado por el usuario, para una lista de valores fijos,
> por ejemplo, de un catálogo de base de datos, utilizar la etiqueta
> [`<select>`](#el-elemento-select)

##### Atributo `autofocus`

El atributo `autofocus` permite establecer el punto inicial de foco del teclado
al momento de terminar la carga de la página. Sólo un elemento de la ppagina
puede contener el atributo autofocus.

> **Recomendación**  
> Como parte de experiencia de usuario, se recomienda que se coloque únicamente
> en el primer control del formulario, siempre y cuando el formulario sea la
> función principal de dicha página.  
> <em>El uso de este atributo está desaconsejado debido a los conflictos que puede
> ocasionar con lectores en pantalla de personas con discapacidad visual.</em>

```html
<label for="txtNombre">Nombre(s)</label>
<input id="txtNombre" type="text" name="nombre" autofocus />
<label for="txtApellido1">Primer apellido</label>
<input id="txtApellido1" type="text" name="apellido1" />
<label for="txtApellido2">Segundo apellido</label>
<input id="txtApellido2" type="text" name="apellido2" />
```

##### Atributo `readonly`

Este atributo establece el contenido como de sólo lectura, lo que significa que
se puede visualizar el campo de entrada y su contenido, además de permitir la
selección y copiado del mismo, pero no podrá ser modificado.

```html
<label for="txtInstitucion">Institución:</label>
<input id="txtInstitucion" type="text" name="institucion" value="Instituto Tecnológico de Colima" readonly />
```

<section class="example">
  <label for="txtInstitucion">Institución:</label>
  <input id="txtInstitucion" type="text" name="institucion" value="Instituto Tecnológico de Colima" readonly />
</section>

##### Atributo `disabled`

Este atributo establece el control como deshabilitado, por lo que no se podrá
interactuar con él.

El valor de su contenido **no será validado ni se enviará** al servidor cuando se
utilice el comando `submit`.

```html
<label for="txtCiudad">Ciudad:</label>
<input id="txtCiudad" type="text" name="ciudad" value="Villa de Álvarez" disabled />
```

<section class="example">
  <label for="txtCiudad">Ciudad:</label>
  <input id="txtCiudad" type="text" name="ciudad" value="Villa de Álvarez" disabled />
</section>

##### Atributo `required`

Este atributo esencial en la validación de formularios, puesto que restringe
el envío del mismo hasta que se hayan completado los campos obligatorios.

```html
<label for="txtNombre">Nombre</label>
<input id="txtNombre" type="text" name="nombre" required />
```

<section class="example">
  <label for="txtNombre">Nombre</label>
  <input id="txtNombre" type="text" name="nombre" required />
</section>

##### Atributo `pattern`

Este atributo es bastante útil en la validación de formularios, puesto que
permite establecer las características generales de la entrada esperada.

El dato CURP (Clave Única de Registro Poblacional) tiene una estructura fija
que sirve para identificar a todos los mexicanos. Se compone de las siguientes
partes:
1. Primera **letra** del primer apellido
1. Primera **vocal** del primer apellido.
1. Primera **letra** del segundo apellido.
1. Primera **letra** del nombre (excepto si tiene dos nombres y el primero es J.
   o José, en el caso de los hombres, o María, Ma, o M, en el caso de las mujeres).
1. Fecha de nacimiento codificada en **dos dígitos** del año, **dos** del mes y
   **dos** del día.
1. **H** en caso de ser hombre, **M** en caso de ser mujer.
1. **Dos letras** que representan la entidad federativa en que nació.
1. Primera **consonante** (después de primera letra) del primer apellido.
1. Primera **consonante** (después de primera letra) del segundo apellido.
1. Primera **consonante** (después de primera letra) del nombre.
1. **Un número** para nacidos antes del 2000, **o una letra** si nació a partir
   del 1 de enero del 2000.
1. **Un número** del 0 al 9 como dígito verificador.

Por lo tanto, tenemos las siguientes características y su equivalencia en
expresión regular *RegExp*.

**Patrón:**
- *Inicio*: `^`
- 1 letra: `\w`
- 1 vocal: `[AEIOU]`
- 2 letras: `\w{2}`
- 2 digitos del 00 al 99: `\d{2}`
- 2 dígitos del 01 al 12: `(0[1-9]|1[012])`
- 2 dígitos del 01 al 31: `(0[1-9]|[12]\d|3[01])`
- 1 ('H' o 'M'): `[HM]`
- 2 letras: `\w{2}`
- 3 consonantes: `[BCDFGHJKLMNPQRSTVWXYZ{3}`
- 1 (letra o número): `[\w\d]`1. 1 número: `\d`
- *Fin*: `$`

Trasladando lo anterior a la sintaxis de RegExp queda de la siguiente manera
```regexp
^\w[AEIOU]\w{2}\d{2}(0[1-9]|1[012])(0[1-9]|[12]\d|3[01])[HM]\w{2}[BCDFGHJKLMNPQRSTVWXYZ]{3}[\w\d]\d$
```

Este mismo patrón se introduce como parte del atributo `pattern` en la etiqueta
`<input>`.

```html
<label for="txtCURP">CURP</label>
<input id="txtCURP" type="text" name="curp" pattern="^\w[AEIOU]\w{2}\d{2}(0[1-9]|1[012])(0[1-9]|[12]\d|3[01])[HM]\w{2}[BCDFGHJKLMNPQRSTVWXYZ]{3}[\w\d]\d$" />
```

<section class="example">
  <label for="txtCURP">CURP</label>
  <input id="txtCURP" type="text" name="curp" pattern="^\w[AEIOU]\w{2}\d{2}(0[1-9]|1[012])(0[1-9]|[12]\d|3[01])[HM]\w{2}[BCDFGHJKLMNPQRSTVWXYZ]{3}[\w\d]\d$" />
</section>

### El elemento `<select>`



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