Protocolo HTTP: Aspectos Técnicos
=======================================

El protocolo HTTP es un estándar para el intercambio de información en la web.
Es un protocolo *stateless* (sin estado), por lo que cada mensaje enviado se
hace de manera independiente sin información de conexiones previas, situación
que ha sido solventada utilizando Cookies.

El protocolo utiliza un esquema de **Mensajes** para el intercambio de la
información, separándose en dos tipos: Mensajes de petición y mensajes de
respuesta.

Mensajes de petición
---------------------------------------

Los mensajes de petición contienen una serie de características que
definen la intensión, el recurso, metadatos e información de la petición.

El formato de una petición HTTP es:

```
METODO /ruta/al/recurso HTTP/1.1¶
Host: el.servidor.com¶
Encabezado: Con su respectivo valor¶
Otro-Encabezado: Otro-valor¶
Mas-Encabezados: Y su valor¶
¶
Cuerpo del mensaje http, es decir, los datos que se envían como parte de la
petición, usualmente datos de un formulario web, contenido de algún archivo,
contenido ajax, etc.
```

> El caracter `¶` se utiliza para representar un salto de línea, el cual no es
> visible bajo condiciones normales.

### Ejemplos

Solicitar el recurso *en formato JSON*, ubicado en la dirección:
`http://www.ejemplo.com/categorias/2`, se emite la siguiente petición:

```http
GET /categorias/2 HTTP/1.1
Host: www.ejemplo.com
Accept: application/json; charset=utf-8

```
---
Enviar los datos del siguiente formulario HTML ubicado en la página
*www.myapp.com/login/index.php*:

```html
<form method="POST" action="www.myapp.com/login/acceder.php">
  <div>
    <label for="txtUsuario">Usuario</label>
    <input id="txtUsuario" type="text" name="usuario" required />
  </div>
  <div>
    <label for="pwdPassword">Contraseña</label>
    <input id="pwdPassword" type="password" name="contra" required />
  </div>
  <div>
    <button type="submit">Iniciar sesión</button>
  </div>
</form>
```

Se traduce al siguiente mensaje de petición HTTP:

```http
POST /login/acceder.php HTTP/1.1
Host: www.myapp.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 51
Referer: www.myapp.com/login/index.php

usuario=mi_nombre_usuario&contra=mi_contrase%C3%B1a
```

Nótese que hubo algunos cambios:
- El método cambió de `GET` a `POST` debido a que el primero es para obtener
  datos desde el servidor mientras que el segundo es enviarlos.
- El encabezado `Accept` cambió por `Content-Type` debido a que el primero
  se utiliza para señalar el formato esperado de los datos, mientras que el
  segundo se utiliza para señalar el tipo de dato en el que se transmite el
  contenido del mensaje.
  La clasificación de estos formatos se llama **MIME type**.
- Se incluye cuerpo en el mensaje, debido a que se transmiten estos hacia el
  servidor.

Mensaje de respuesta
---------------------------------------

Los mensajes de respuesta tienen un formato similar a los de petición,
difiriendo principalmente en su primera línea de encabezado.

El formato de una petición HTTP es:

```
CODIGO HTTP/1.1 DESCRIPCION_ESTADO
Encabezado: su respectivo valor
Otro-Encabezado: su-valor-correspondiente
Mas-Encabezados: con-su-valor

Contenido del mensaje HTTP, los datos que devuelve el servidor, incluídos los
documentos HTML de páginas web.
```

### Ejemplos

Los siguientes mensajes de respuesta corresponden a los ejemplos de mensajes de
petición anteriores:

Respuesta *en formato JSON* tras solicitar el recurso en
`http://www.ejemplo.com/categorias/2`.

```http
200 HTTP/1.1 OK
Content-Type: application/json; charset=utf-8
Content-Length: 66

{"id_categoria":2,"nombre":"Electr\u0000nica","num_articulos":274}
```

---

Respuesta al envío de datos por medio de un formulario HTML:

```http
302 HTTP/1.1 FOUND
Location: www.myapp.com/main/index.php
Set-Cookie: session=F4f4gB5tbTYbmvhdkYCj7gvjfvv64bmgc5bYf75V67gvbgdf
```

Nótese que al igual que en los mensajes de petición, se mantuvo la estructura
general, pero cambió el contenido dependiendo del los requerimientos de la
aplicación:
- El código y descripción del estado aparece en `200 OK` en el primer ejemplo
  porque de esta manera el servidor notifica que la petición se recibió y
  atendió correctamente.
- El código y descripción del estado aparece en `302 FOUND` en el segundo
  ejemplo porque señala que se encontró el recurso, pero este fue redirigido.  
  La nueva dirección se establece mediante el encabezado `Location`.