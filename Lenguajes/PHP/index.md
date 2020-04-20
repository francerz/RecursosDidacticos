Lenguaje PHP
=======================================

- [Lenguaje PHP](#lenguaje-php)
  - [Instalación](#instalaci%c3%b3n)
  - [Primera página de PHP](#primera-p%c3%a1gina-de-php)
  - [Sintaxis del lenguaje](#sintaxis-del-lenguaje)
    - [Etiquetas](#etiquetas)
    - [Variables](#variables)
      - [Asignación por referencia](#asignaci%c3%b3n-por-referencia)

PHP (PHP: Hipertext Preprocesor) es un lenguaje de programación popular que se
utiliza para *scripting* del lado del servidor y con propósito general,
particularmente utilizado para el desarrollo de aplicaciones web, cuyo contenido
es dinámico.

Ejemplo:
```php
<!DOCTYPE html>
<html>
    <head>
        <title>Ejemplo</title>
    </head>
    <body>
        <?php
            echo "Hola, ¡Soy un script PHP!";
        ?>
    </body>
</html>
```

El ejemplo anterior, aparentemente sencillo, oculta la utilización de múltiples
librerías en C o Perl, que se requieren para generar el documento, recibir
solicitudes al servidor Web HTTP, y devolver una respuesta con el formato
correspondiente.

Para incrustar código en el documento se utilizan las instrucciones de inicio y
término del preprocesamiento `<?php` y `?>` respectivamente.

Una de las ventajas de que el código se ejecute del lado del servidor, es que
únicamente se devuelve al usuario el documento resultante del preprocesamiento.
Sin que el usuario pueda tener conocimiento sobre la forma en que se ejecuta por
detrás.

Instalación
---------------------------------------

Dada la característica del lenguaje implica que se ejecute en un servidor. Los
archivos no pueden ejecutarse simplemente utilizando el navegador, sino que es
necesario hacer la instalación de un Servidor HTTP (Web) como lo es Apache o
IIS, y además configurar la librería PHP correspondiente para que el servidor
sea capaz de interpretar el código.

Se puede hacer la instalación uno a uno utilizando los siguientes componentes:
* **Apache**: <http://httpd.apache.org/download.cgi>
* **PHP**: <https://www.php.net/downloads.php>
* **MySQL**(opcional si se utilizan BD): <https://dev.mysql.com/downloads/mysql/>

O si es para desarrollo, es suficiente con utilizar alguno de los siguientes
paquetes que incluyen esos tres componentes:
* **XAMPP**: <https://www.apachefriends.org/es/download.html>
* **WampServer**: <https://sourceforge.net/projects/wampserver/>

> **NOTA**:  
> La ubicación donde se deberán colocar los archivos `.php` depende de la
> configuración del servidor, o del paquete de instalación utilizado:
> Para el caso de **XAMPP** la ubicación es: `/xampp/htdocs`.
> **A esta ubicación se le identificará como `DOCUMENT_ROOT`**.

Primera página de PHP
---------------------------------------

Para verificar que se haya instalado y configurado correctamente PHP se puede
crear un archivo `hola.php` en `DOCUMENT_ROOT` con el siguiente contenido:

```php
<html>
    <head>
        <title>Prueba PHP</title>
    </head>
    <body>
        <?php echo "<p>Hola Mundo</p>"; ?>
    </body>
</html>
```

Para acceder a este archivo desde el navegador se debe utilizar la dirección
del servidor, por ejemplo `http://localhost/hola.php`.

> Si el servidor está configurado en un puerto distinto al `80`, por ejemplo, el
> `8080` la dirección será: `http://localhost:8080/hola.php`.

> La dirección `localhost` es un nombre dado a la dirección `127.0.0.1`.

El documento resultante de la ejecución anterior debe ser el siguiente.
```html
<html>
    <head>
        <title>Prueba PHP</title>
    </head>
    <body>
        <p>Hola Mundo</p>
    </body>
</html>
```

Si el documento se generó correctamente se puede proceder con el siguiente ejemplo:

`info.php`
```php
<?php phpinfo(); ?>
```

Sintaxis del lenguaje
---------------------------------------

### Etiquetas
Como se ha visto anteriormente, el lenguaje PHP requiere para que sea
identificado, que tenga la extensión `.php` y que el código ejecutable se
coloque dentro de las etiquetas `<?php` y `?>`.

PHP también incluye una sintaxis denominada etiqueta corta de *echo*.
```php
// Las siguientes líneas son semánticamente equivalentes

<?php echo "Etiquetas normales de PHP con echo"; ?>

<?="Etiqueta corta de echo"?>
```

Si un archivo **contiene únicamente código PHP**, es preferible omitir la
etiqueta de cierre al final del archivo. Esto previene que algún espacio en
blanco o saltos de línea se agreguen después de la etiqueta de cierre, lo que
puede provocar efectos no deseados.[[1]]

```php
<?php
echo "Hola mundo";

// ... más código

echo "Última instrucción";

// el archivo concluye aquí sin etiqueta de cierre
```

[1]: https://www.php.net/manual/es/language.basic-syntax.phptags.php

### Variables

En PHP se identifican utilizando el signo de pesos, seguido del nombre de la
variable. Los nombres de las variables son sensibles a mayúsculas y minúsculas.

Las variables en PHP no requieren ser declaradas, ni tampoco están definidas
con un tipo. Únicamente son utilizadas en su asignación.

```php
<?php
$num1 = 10;         // Asignar 10 a variable $num1
$num2 = 8;          // Asignar 8 a variable $num2

$resultado = $num1 + $num2; // Asignar a $resultado la suma de $num1 y $num2

// Usar función print_r para visualizar el valor de una variable
print_r($resultado);    // Salida: 18

// Usar función var_dump para visualizar el valor de una variable y su tipo
var_dump($resultado);   // Salida: int(18)
```

#### Asignación por referencia

De manera predeterminada, la asignación de variables se hace por valor. Lo que
significa que si se asigna una variable a la otra, se hace la copia de su valor
en la variable, lo que significa que al realizarse la modificación de la segunda
el valor de la primera quedaría intacto.

Cuando se hace asignación por referencia, a la nueva variable se le asigna la
dirección de memoria de la variable inicial, de manera que al realizar
modificaciones en una variable, el cambio será visible en ambas.

Para asignar por referencia, sólo se debe colocar ampersand `&` inmediatamente
antes de la variable que será asignada (variable de origen).

Asignación por valor:
```php
<?php
$a = 20;
$b = $a;

$b++;

print_r($a);    // Resultado: 20
print_r($b);    // Resultado: 21
```

Asignación por referencia:
```php
$a = 20;
$b = &$a;       // <-- Nótese el & antes de la variable $a

$b++;

print_r($a);    // Resultado: 21
print_r($b);    // Resultado: 21
```