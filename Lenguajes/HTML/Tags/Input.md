Etiqueta `<input>`
=======================================

El elemento `<input>` es utilizado para crear controles interactivos para
formularios basados en web, con la intención de aceptar datos del usuario; una
amplia variedad de tipos de datos y controles están disponibles, dependiendo del
dispositivo y *agente de usuario*. El elemento `<input>` es uno de los más
potentes y complejos de todo HTML, debido a su amplio número de combineaciones
para tipos de entrada y atibutos.

- [Etiqueta `<input>`](#etiqueta-input)
  - [Atributos](#atributos)
    - [Atributo `type`](#atributo-type)
      - [Tipo `text`](#tipo-text)
      - [Tipo `password`](#tipo-password)
      - [Tipo `hidden`](#tipo-hidden)
      - [Tipo `number`](#tipo-number)
      - [Tipo `date`](#tipo-date)
      - [Tipo `time`](#tipo-time)
      - [Tipo `checkbox`](#tipo-checkbox)
      - [Tipo `radio`](#tipo-radio)
      - [Tipo `file`](#tipo-file)
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
  - [Referencias](#referencias)

Atributos
---------------------------------------

### Atributo `type`

El funcionamiento de un `<input>` varía considerablemente dependiendo del valor
de su atributo `type`. El valor predeterminado para el tipo es `text`.

#### Tipo `text`

Es el valor predeterminado. Es un campo de texto de una sóla línea. Los saltos
de línea son removidos automáticamente del valor del input.

#### Tipo `password`

Es un campo de texto de una sóla línea, cuyo valor está obstruido. Alertará al
usuario si el sitio no es seguro.

#### Tipo `hidden`

Es un control que no se despliega, pero su valor es enviado al servidor.

#### Tipo `number`

Un control para introducir un número. Despliega un selector y agrega una
validación cuando esta es soportada. Muestra un teclado numérico en algunos
dispositivos con teclados dinámicos.

#### Tipo `date`

Es un control para introducir uan fecha (año, mes y día).
Abre un selector de fecha o listas selectoras para el año, mes, día cuando está
activo en los navegadores que lo soportan.

#### Tipo `time`

Permite introducir una hora, sin incluir zona horaria.

#### Tipo `checkbox`

Es una caja de verificación que permite seleccionar valores independientes para
ser seleccionados o deseleccionados.

#### Tipo `radio`

Permite seleccionar a un único valor entre un conjunto de múltiples opciones con
el mismo `name`.

#### Tipo `file`

Permite al usuario seleccionar un archivo. Utiliza el atributo `accept` para
definir los tipos de archivos que el control puede seleccionar.

### Atributo `value`

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

### Atributos `min` y `max`

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

### Atributos `maxlength` y `minlength`

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

### Atributo `placeholder`

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

### Atributo `inputmode`

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

### Atributo `list`

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

### Atributo `autofocus`

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

### Atributo `readonly`

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

### Atributo `disabled`

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

### Atributo `required`

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

### Atributo `pattern`

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

Referencias
---------------------------------------
* https://developer.mozilla.org/en-US/docs/Learn/Forms/Basic_native_form_controls