REST (REpresentational State Transfer)
=======================================

REST es un estilo de arquitectura de software para sistemas hipermedia
distribuidos como la World Wide Web.

Su uso está ampliamente extendido debido a su compatiblidad con el protocolo
HTTP, el cual se utiliza como base de la WWW.

- [REST (REpresentational State Transfer)](#rest-representational-state-transfer)
  - [Requisitos Previos](#requisitos-previos)
  - [Conceptos básicos](#conceptos-b%c3%a1sicos)
    - [Recurso](#recurso)
    - [Sin estado](#sin-estado)
    - [Identificador Uniforme de Recurso (URI)](#identificador-uniforme-de-recurso-uri)
    - [Verbos](#verbos)
    - [Idempotente y Seguro](#idempotente-y-seguro)
    - [Códigos de estado](#c%c3%b3digos-de-estado)
  - [Diseño de un servicio RESTful](#dise%c3%b1o-de-un-servicio-restful)
    - [Nombres de recursos](#nombres-de-recursos)
      - [Reglas para el diseño de rutas URL](#reglas-para-el-dise%c3%b1o-de-rutas-url)
    - [Métodos y códigos de estado](#m%c3%a9todos-y-c%c3%b3digos-de-estado)

Requisitos Previos
---------------------------------------

+ [HTML: Aspectos Técnicos](../../Protocolos/HTTP/AspectosTecnicos.md)
+ [URL: Uniform Resource Locator](../../Protocolos/URI/URL.md)

Conceptos básicos
---------------------------------------

Existen algunos conceptos básicos en este tipo de arquitectura que deben
comprenderse previo a su utilización, puesto que es fundamental la comprensión
de los mismos para hacer un correcto uso de REST:

### Recurso

Un recurso es cualquier objeto, elemento, dato, archivo, etc. que pueda
localizarse en la red, siendo accesibles utilizando un Identificador Uniforme
de Recurso (URI). El intercambio de estos recursos se hace mediante una interfaz
estándar(HTTP).

### Sin estado

Cada petición en REST es única e inconexa con otras peticiones, por lo que toda
la información requerida para que sea atendida, deberá encontrarse dentro de la
misma petición.

Esto significa que dentro de este estilo de arquitctura no existe el concepto de
sesión o conexión persistente.

### Identificador Uniforme de Recurso (URI)

Es un nombre normalizado que se asigna a un recurso para que este sea localizado
en la red. Los URI suelen clasificarse en dos tipos: URN (Nombre de Recurso
Uniforme) y URL (Localizador de Recursos Uniforme).

El formato más popular es URL, algunos ejemplos son:

* `mailto:correo@dominio.com`
* `esquema://mi.dominio.com/ruta/al/recurso?cadena=busqueda`

### Verbos

Son equivalentes a los métodos de HTTP, los cuales en REST se identfician los
siguientes 5:

* `GET`
  Corresponde a la acción de recuperar el recurso, equivalente a consultar
  en una base de datos, leer un archivo o recuperar una página web.
* `POST`
  Correspone a la acción de crear un recurso, es equivalente a insertar un
  registro en una base de datos, crear un archivo o enviar datos en un formulario
  web.
* `PUT`
  Corresponde a la acción de reemplazar un recurso, es equivalente a eliminar 
  un registro existente e insertar uno nuevo como sustituto.
* `PATCH`
  Corresponde a la acción de actualizar un recurso, es equivalente a modificar
  un dato de un registro en una base de datos.
* `DELETE`
  Corresponde a la acción de eliminar un recurso, es equivalente a eliminar un
  registro de base de datos.

### Idempotente y Seguro



### Códigos de estado

Los códigos de estado es un número de tres dígitos que representa el resultado
de una petición, estos son parte del protocolo HTTP.

Los códigos se clasifican en cinco tipos diferentes, detectables por el primer
dígito de estos:

* *1xx respuesta informativa*
* *2xx satisfactorio*
* *3xx redirección*
* *4xx errores del cliente*
* *5xx errores del servidor*

Aunque los valores de los códigos de estado están estandarizados, su
interpretación depende de la petición que causó la respuesta.

* `200 OK`
  Si se utiliza con el método `GET` significa que se encontró el recurso y el
  contenido se incluye en el cuerpo del mensaje.

  Si se utiliza con el método `POST` significa que se realizó el envío
  correctamente, y en el cuerpo del mensaje se incluirá una entidad que describa
  el resultado de la acción.

* `201 CREATED`
  La petición se atendió correctamente y se creó un nuevo recurso.

* `204 NO CONTENT`
  El servior procesó correctamente la petión y no devuelve contenido alguno.

* `400 BAD REQUEST`
  El servidor no puede y no va a procesar la petición debido a que hay aparente
  error del cliente.

* `401 UNAUTHORIZED`
  El servidor recibió la petición y fue entendida, pero no se atenderá debido
  a que se falla en la autenticación de HTTP utilizando el header
  *WWW-Authenticate*.

* `403 FORBIDDEN`
  La petición contiene datos válidos y fue entendia por el servidor, pero se
  niega a atenderla debido a que no se cuentan con los permisos necesarios.

* `404 NOT FOUND`
  El recurso solicitado no se encuentra, pero podría encontrarse en el futuro.

* `405 METHOD NOT ALLOWED`
  Cuando se utiliza un método o *verbo* distinto a los soportados para el
  recurso. Por ejemplo: enviar una petición `POST` cuando sólo se admite `GET`.

* `409 CONFLICT`
  Indica que la petición no puede procesarse debido a que existe un conflicto
  con el estado actual del recurso.

* `500 Internal Server Error`
  Es un mensaje de error genérico del lado del servidor.

* `501 Not Implemented`
  Ocurre cuando el servidor no reconoce el método de la petición, o carece de la
  capacidad para atender dicha petición, sin embargo se espera que en algún
  momento pueda estar disponible.

Diseño de un servicio RESTful
---------------------------------------

### Nombres de recursos

Una de las partes más importantes de la elaboración de una API REST es la
construcción de nombres de recursos, puesto que de estos depende la claridad de
lo que este se refiere.

Los nombres de recursos apropiados proporcionan contexto para la petición de un
servicio, incrementando la comprensibilidad de la API. Los recursos son vistos
jerárquicamente por medio de sus nombres de de identificar (URI), proporcionando
a los clientes una jerarquía intuitiva y fácil de entender.

#### Reglas para el diseño de rutas URL

* Utilizar identificadores en las URL, en lugar de los *Query String*. El uso de
  *Query String* es útil para filtrado, pero no para nombres de recursos.
  + **Correcto**: `/usuarios/12345`
  + **Incorrecto**: `/api?tipo=usuarios&id=12345`
* Adoptar la naturaleza jerárquica del a URL para implicar estructura.
* Diseñar para los clientes, no para los datos.
* Los nombres de los recursos deben ser sustantivos. Evitar utilizar verbos como
  nombres de recursos, para mejorar la claridad. Utilizar los métodos HTTP para
  expecificar la porción del verbo de la petición.
* Usar plurales en los segumentos de URL para mantener las URI de las API
  consistentes a través de los métodos HTTP, utilizando la metáfora de
  colecciones.
  + **Recomendado** `/clientes/12345/ordenes/678/articulos/9`
  + **Evitar** `/cliente/12345/orden/678/articulo/9`
* *Evitar* utilizar verbos en las URLs. Por ejemplo `lista_clientes` como
  recurso. Utilizar la pluralización para indicar la metáfora de colección.
* Utilizar minúsculas para segmentos de URL, separando palabras con guiones
  bajos `_` o medios `-`. Esto evita confusiones con servidores que distinguen
  entre mayúsculas y minúsculas.
* Mantener las URLs tan prontas como sea posible, con tan pocos segumentos como
  tenga sentido.

**Ejemplos correctos**
* `POST http://www.ejemplo.com/clientes`
* `GET http://www.ejemplo.com/clientes/234`
* `POST http://www.ejemplo.com/clientes/234/ordenes`
* `GET http://www.ejemplo.com/clientes/234/ordeneses/56`

**Ejemplos incorrectos**
* `GET http://api.ejemplo.com/servicios?op=insertar_cliente`
* `GET http://api.ejemplo.com/servicios?op=consultar_cliente&id=234`
* `GET http://api.ejemplo.com/registrar_orden?cliente=234`
* `GET http://api.ejemplo.com/clientes/234/actualizar`
* `POST http://api.ejemplo.com/clientes/234/actualizar`

### Métodos y códigos de estado

| Método   | CRUD      | Colección (ej. `/clientes`)                                                                                     | Elemento (ej. `/clientes/{id}`) |
| -------- | --------- | --------------------------------------------------------------------------------------------------------------- | --- |
| `POST`   | Crear     | `201` (Creado)<br>Incluir header `Location` con el enlace a `/clientes/{id}` con el `id` insertado.             | `404` (No encontrado)<br>`409` (Conflicto) si un recurso ya existe. |
| `GET`    | Leer      | `200` (OK)<br>Obtiene una lista de los clientes.                                                                | `200` (OK) con los datos del cliente que tenga el `id`.<br>`404` (No encontrado) Si el `id` no se encuentra o es inválido. |
| `PUT`    | Reemplazar | `405` (Método no permitido)<br>Evitar, a menos de que se quiera reemplazar todos los recursos en la colección. | `200` (OK) o `204` (Sin contenido).<br>`404` (No encontrado), si no se encuentra el `id` o es inválido. |
| `PATCH`  | Modificar | `405` (Método no permitido)<br>Evitar, a menos de que se quiera modificar la colección.                         | `200` (OK) o `204` (Sin contenido).<br>`404` (No encontrado), si no se encuentra el `id` o es inválido. |
| `DELETE` | Eliminar  | `405` (Método no permitido)<br>Evitar, a menos de que se quiera eliminar la colección completa.                 | `200` (OK).<br>`404` (No encontrado), si no se encuentra el `id` o es inválido. |