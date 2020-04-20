Lenguaje PHP
=======================================

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