Etiqueta `<input>`
=======================================

El elemento `<input>` es utilizado para crear controles interactivos para
formularios basados en web, con la intención de aceptar datos del usuario; una
amplia variedad de tipos de datos y controles están disponibles, dependiendo del
dispositivo y *agente de usuario*. El elemento `<input>` es uno de los más
potentes y complejos de todo HTML, debido a su amplio número de combineaciones
para tipos de entrada y atibutos.

Atributo `type`
---------------------------------------

El funcionamiento de un `<input>` varía considerablemente dependiendo del valor
de su atributo `type`. El valor predeterminado para el tipo es `text`.

<a name="type-text"></a>
### `text`

Es el valor predeterminado. Es un campo de texto de una sóla línea. Los saltos
de línea son removidos automáticamente del valor del input.

<a name="type-password"></a>
### `password`

Es un campo de texto de una sóla línea, cuyo valor está obstruido. Alertará al
usuario si el sitio no es seguro.

<a name="type-hidden"></a>
### `hidden`

Es un control que no se despliega, pero su valor es enviado al servidor.

<a name="type-number"></a>
### `number`

Un control para introducir un número. Despliega un selector y agrega una
validación cuando esta es soportada. Muestra un teclado numérico en algunos
dispositivos con teclados dinámicos.

<a name="type-date"></a>
### `date`

Es un control para introducir uan fecha (año, mes y día).
Abre un selector de fecha o listas selectoras para el año, mes, día cuando está
activo en los navegadores que lo soportan.

<a name="type-time"></a>
### `time`

Permite introducir una hora, sin incluir zona horaria.

<a name="type-checkbox"></a>
### `checkbox`

Es una caja de verificación que permite seleccionar valores independientes para
ser seleccionados o deseleccionados.

<a name="type-radio"></a>
### `radio`

Permite seleccionar a un único valor entre un conjunto de múltiples opciones con
el mismo `name`.

<a name="type-file"></a>
### `file`

Permite al usuario seleccionar un archivo. Utiliza el atributo `accept` para
definir los tipos de archivos que el control puede seleccionar.

Referencias
---------------------------------------
* https://developer.mozilla.org/en-US/docs/Learn/Forms/Basic_native_form_controls