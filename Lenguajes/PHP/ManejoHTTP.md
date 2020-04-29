PHP: Manejo del protocolo HTTP
=======================================

Los usos más comunes del lenguaje PHP es la implementación de sitios web y la 
publicación de estos en formato HTML, PDF, XML, JSON, etc. Asumiendo que es lo
único para lo que se puede utilizar, sin embargo, el lenguaje tiene una utilidad
mayor si se considerar que su objetivo principal ha sido simplificar el manejo
del protocolo HTTP en C++.

- [PHP: Manejo del protocolo HTTP](#php-manejo-del-protocolo-http)
  - [Requisitos previos](#requisitos-previos)
  - [Mensaje de petición](#mensaje-de-petici%c3%b3n)
    - [Método](#m%c3%a9todo)
    - [Headers](#headers)
    - [Contenido](#contenido)
      - [Variable global `$_POST`](#variable-global-post)
      - [Usando `php://input` y `parse_str()`](#usando-phpinput-y-parsestr)
      - [Otros `Content-Type`](#otros-content-type)

## Requisitos previos
- [Aspectos Técnicos del Protocolo HTTP](../../Protocolos/HTTP/AspectosTecnicos.md)

Mensaje de petición
---------------------------------------

PHP cuenta con mecanismos diversos para reconstruir una petición en orden inverso.
Es decir, tomar la petición actual que invocó PHP, para procesar localmente su
contenido.

```http
POST /login/acceder.php HTTP/1.1
Host: www.myapp.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 51
Referer: www.myapp.com/login/index.php

usuario=mi_nombre_usuario&contra=mi_contrase%C3%B1a
```

### Método

El método se puede obtener mediante la variable global `$_SERVER` de php,
utilizando la clave `'REQUEST_METHOD'`.

```php
<?php

$request_method = $_SERVER['REQUEST_METHOD'];

echo $request_method;
```

**Salida:**
```
POST
```

### Headers

Un listado de los Headers recibidos en la petición pueden recuperarse en un
arreglo con pares `'clave' => valor` utilizando la función `getallheaders()`.

```php
<?php

// Recuperar todos los headers de la petición
$headers = getallheaders();

// Normalizar los nombres a minúsculas
$headers = array_change_key_case($headers, CASE_LOWER);

// Recuperando el valor del header Content-Type
$headerContentType = $header['content-type'];

foreach ($headers as $name => $content) {
    echo "$name: $content".PHP_EOL;
}
```

**Salida:**
```
host: www.myapp.com
content-type: application/x-www-form-urlencoded
content-length: 51
referer: www.myapp.com/login/index.php
```

### Contenido

Recuperar el contenido de un mensaje HTTP puede resultar algo más complejo de
lo usual, dependiendo del tipo de contenido que se reciba por medio del mensaje.

#### Variable global `$_POST`
Por ejemplo, si se trata del método `POST` con `Content-Type` igual a
`application/x-www-form-urlencoded` o `multipart/form-data`, es posible
recuperar el valor de las variables codificadas utilizando la variable global
`$_POST`.

```php
<?php

var_dump($_POST);
```

**Salida:**
```
array(2) {
  ["usuario"]=>
  string(17) "mi_nombre_usuario"
  ["contra"]=>
  string(14) "mi_contraseña"
}
```

#### Usando `php://input` y `parse_str()`
Si se trata de otro método, por ejemplo `PUT` o `PATCH`, y el `Content-Type` es
`application/x-www-form-urlencoded` se deberá extraer desde el buffer de entrada
en PHP, y posteriormente convertir su contenido.

```php
<?php

// Recuperar los datos en el buffer de entrada de PHP
$php_input = file_get_contents('php://input');

// Convierte la cadena como si fuera Query String codificada en URL
parse_str($php_input, $_DATA);

var_dump($_DATA);
```

**Salida:**
```
array(2) {
  ["usuario"]=>
  string(17) "mi_nombre_usuario"
  ["contra"]=>
  string(14) "mi_contraseña"
}
```

#### Otros `Content-Type`
Si se trata de cualquier método, pero `Content-Type` es cualquier otro formato,
este puede recuperarse mediante el buffer de entrada de PHP.

A continuación, se muestra un ejemplo cuando se reciben los datos en formato
JSON con header `Content-Type: application/json`.

**Petición HTTP:**
```http
POST /articulos HTTP/1.1
Content-Type: application/json

{"nombre":"Teclado portatil","precio":140.23,"existencias":32}
```

**Script PHP:**
```php
<?php

$php_input = file_get_contents('php://input');

$data = json_decode($php_input);

var_dump($data);
```

**Salida:**
```
object(stdClass)#1 (3) {
  ["nombre"]=>
  string(16) "Teclado portatil"
  ["precio"]=>
  float(140.23)
  ["existencias"]=>
  int(32)
}
```