Lenguaje PHP
=======================================

- [Lenguaje PHP](#lenguaje-php)
  - [Instalación](#instalaci%c3%b3n)
  - [Primera página de PHP](#primera-p%c3%a1gina-de-php)
  - [Sintaxis del lenguaje](#sintaxis-del-lenguaje)
    - [Etiquetas](#etiquetas)
    - [Variables](#variables)
      - [Asignación por referencia](#asignaci%c3%b3n-por-referencia)
    - [Tipos de datos](#tipos-de-datos)
      - [Booleanos](#booleanos)
      - [Enteros](#enteros)
      - [Números de punto flotante](#n%c3%bameros-de-punto-flotante)
      - [Cadenas](#cadenas)
        - [Comillas simples](#comillas-simples)
        - [Comillas dobles](#comillas-dobles)
          - [Conversión de variables en cadenas](#conversi%c3%b3n-de-variables-en-cadenas)
      - [Arreglos](#arreglos)
        - [Claves](#claves)
      - [Objetos](#objetos)
      - [Recursos](#recursos)
      - [NULL](#null)
      - [Callbacks](#callbacks)

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
<?php
$a = 20;
$b = &$a;       // <-- Nótese el & antes de la variable $a

$b++;

print_r($a);    // Resultado: 21
print_r($b);    // Resultado: 21
```

### Tipos de datos
[[2]]

Aunque al momento de declarar una variable no se especifique el tipo de dato,
estos continúan existiendo en el lenguaje. Los tipos más comunes de tipos de
dato son:

#### Booleanos
Este es el tipo de dato más simple. Sólo tiene dos posibles valores: `true` y
`false`.

#### Enteros
Un entero es un número sin valores decimales, que incluye positivos, negativos
y cero. Se aceptan diferentes tipos de representaciones de los datos.
```php
<?php
$a = 1234;    // número decimal
$a = 0123;    // número en octal (equivale a 83 decimal)
$a = 0x1A;    // número hexadecimal (equivalente a 26 decimal)
$a = 0b11111111;  // número binario (equivalente a 255 decimal)
```

#### Números de punto flotante 
Los números de punto flotante (tambien conocidos como "flotantes" o "reales")
son aquellos que tienen punto decimal y se pueden expresar de la siguiente
manera:
```php
<?php
$a = 1.234;
$b = 1.2e3; // equivale a 1200 (el punto se "recorre" 3 espacios a la derecha)
$c = 7e-10; // equivale a 0.0000000007 (el punto se "recorre" 10 espacios a la izquierda).
```

#### Cadenas
Una cadena es una serie de caracteres, donde un caracter es lo mismo que un
byte. Esto significa que PHP sólo soporta conjuntos de 256 caracteres, y no
ofrece soporte nativo a Unicode.

Las cadenas pueden especificarse de cuatro maneras distintas *comillas simples*`,
*comillas dobles*, *sintaxis heredoc* y *sintaxis heredoc* (En esta guía sólo se tratarán las dos primeras, que son las más comunes).

##### Comillas simples

La manera más simple de especificar una *string* es encerrando entre comillas
simples `'`.

Cuando una cadena utiliza comillas simples, puede incluirse el caracter dentro
de la misma utilizando la secuencia de escape `\'`. Para incluir una diagnoal
invertida se puede utilizar `\\` doble diagonal invertida. Todas las demás
secuencias de escape no son compatibles con este tipo de cadena, por lo que
utilizar secuencias `\r`, `\n` o `\t` no serán convertidas y se mostrarán tal
cual en la cadena.

> **Nota:** A diferencia de las sintaxis de comillas doble y heredoc, las
> variables y secuencias de escape para caracteres especiales no serán expandidas
> cuando se utilizen cadenas de una sola comilla.

```php
<?php
echo 'esta es una cadena simple';

echo 'También se pueden incluir saltos de línea
en cadenas de esta manera y
está bien hacerlo así';

// Salida: Arnold una vez dijo: "I'll be back"
echo 'Arnold una vez dijo: "I\'ll be back"';

// Salida: ¿Desea borrar  C:\*.*?
echo '¿Desea borrar C:\\*.*?';

// Salida: Esto no se va a extender: \n una nueva línea
echo 'Esto no se va a extender: \n una nueva línea';

// Salida: Variables no se $expanden $tampoco
echo 'Variables no se $expanden $tampoco';
```

##### Comillas dobles

Si la cadena se encierra entre comillas dobles `"`, PHP va a interpretarr las
siguientes secuencias de escape para caracteres especiales:

**Secuencias de escape**
Secuencia | Significado
`\n` | Alimentación de línea (LF o 0x0A(10) en ASCII)
`\r` | Retorno de carro (CR o 0x0D(13) en ASCII)
`\t` | Tabulación horizontal (HT o 0x09(9) en ASCII)
`\v` | Tabulación vertical (VT o 0x0B(11) en ASCII)
`\e` | Escape (ESC o 0x1B(27) en ASCII)
`\f` | Alimentación de formularrio (FF o 0x0C(12) en ASCII)
`\\` | Diagonal invertida
`\$` | Signo de dolar
`\"` | Comillas dobles
`\u0000` | Valor hexadecimal de un caracter unicode, el cual será representado utilizando la representación en UTF-8

Si se utiliza la diagonal invertida en conjunto a cualquier otro caracter, se
mostrará la diagonal invertida.

Una de las ventajas de utilizar cadenas con comillas dobles, es qeu los nombres
de las variables serán expandidas. Esto significa que en lugar de mostrar
el nombre de la variable, se sustituirá con el valor de dicha variable.

###### Conversión de variables en cadenas

Existen dos tipos de sintaxis: la simpel y la compleja.
* **La sintaxis simple** es la más común y conveniente. Proporciona una manera de
  incrustar una variable, valor de arreglo o propiedad de objeto con un mínimo
  de esfuerzo.
* **La sintaxis compleja** se reconoce con la utilización de llaves `{}` rodeando
  el nombre de la variable. Y permite la utilización de expresiones complejas.

```php
<?php
$jugo = "manzana";

// PHP_EOL = PHP_END_OF_LINE (fin de línea o salto de línea)
// El caracter `.` (punto) se utiliza para concatenar(unir dos cadenas).

echo "Él bebió algo de jugo de $jugo.".PHP_EOL;

// Inválido: tiene un nombre incorrecto de la variable, porque es $jugo, no $jugos
echo "Él bebió algún jugo hecho de $jugos.";

// Válido: se especifica el fin de la variable encerrándola entre llaves
echo "Él bebió algún jugo hecho de ${jugo}s.";
```

El ejemplo anterior dará la siguiente salida:
```
Él bebió algo de jugo de manzana.
Él bebió algún jugo hecho de .
Él bebió algún jugo hecho de manzanas.
```

De igual manera, un indice de arreglo o una propiedad de objeto puede convertirse.
Con los indices de arreglo, los corchetes de cierre `]` señala el fin del índice.
Las mismas reglas aplican para propiedades de objetos como variables simples.

```php
$jugos = array('manzana', 'naranja', 'tang'=>'uva');

echo "Él bebió algún jugo de $jugos[0].".PHP_EOL;
echo "Él bebió algún jugo de $jugos[1].".PHP_EOL;
echo "Él bebió algún jugo de $jugos[tang].".PHP_EOL;

class personas {
    public $juan = "Juan Pérez";
    public $maria = "María Pérez";
    public $roberto = "Roberto Cortés";

    public $perez = "Pérez";
}

$personas = new personas();

echo "$gente->juan bebió jugo de $jugos[0].".PHP_EOL;
echo "$gente->juan luego dijo hola a $gente->maria.".PHP_EOL;
echo "La esposa de $gente->juan saludó a $gente->roberto.".PHP_EOL;
echo "$gente->roberto saludó a los dos $gente->perales."; // <--- No funcionará
```

El ejemplo anterior dará la siguiente salida:
```
Él bebió algún jugo de manzana.
Él bebió algún jugo de naranja.
Él bebió algún jugo de uva.
Juan Pérez bebió jugo de manzana.
Juan Pérez luego dijo hola a María Pérez.
La esposa de Juan Pérez saludó a Roberto Cortés.
Roberto Cortés saludó a los dos .
```

La **Sintaxis Compleja** permite utilizar expresiones complejas dentro de las
cadenas, además de permitir variables de tipo escalar, elementos de arreglos,
propiedades de objetos. Así mismo puede incluir invocaciones a métodos de un
objeto.

Para utilizar esta sintaxis, sólo se debe envolver la expresión dentro de llaves
`{ }`. Debido a que `{` no puede ser escapada, la sintaxis sólo se reconoce
cuando se utiliza inmediatamente `$`.

```php
// Mostrar todos los errores
error_reporting(E_ALL);

$genial = 'fantastico';

// No funcionará, salida: Esto es { fantastico}
echo "Esto es { $genial}";

// Funciona, salida: Esto es fantastico
echo "Esto es {$genial}";

// Funciona
echo "Este cuadrado es {$cuadrado->ancho}00 centimetros ancho.";

// Funciona, las claves enrtre comillas funcionan con sintaxis de llaves
echo "Esto funciona: {$arreglo['clave']}";

// Funciona
echo "Esto funciona: {$matriz[4][3]}";

// Esto no va a funcionar porque las claves en la sintaxis con llaves deben
// incluir las comillas. Sin las comillas buscará el nombre de la clave como
// el nombre de una constante.
echo "Esto está mal: {$arreglo[clave][3]}";

// Funciona. Cuando se utilicen arreglos multidimensionales dentro de las cadenas
// se debe usar la sintaxis de llaves
echo "Esto funciona: {$arreglo['clave'][3]}";

// Funciona.
echo "Esto funciona: ".$arreglo['clave'][3];

echo "Esto funciona también: {$obj->valores[3]->nombre}";

echo "Este es el valor de la variable llamada $nombre: {${$nombre}}";

echo "Este es el valor de la variable llamada por el valor de retorno de getName(): {${$getName}}";

echo "Este es el valor de la variable llamada por el valor de retorno de \$obj->getName(): {${$obj->getName()}}";

// No funcionará, salida: Este es el valor de retorno de getName(): {getName()}
echo "ESte es el valor de retorno de getName(): {getName()}";
```

* **Variedad de funciones de cadena**  
  <https://www.php.net/manual/es/ref.strings.php>

#### Arreglos

Los arreglos en PHP son un mapa, que asocia valores con claves, de manera ordenada. Dada su naturaleza se puede utilizar como una amplia variedad de
estructuras de coleccción de datos, equivaliendo a: arreglo, lista (vector),
tabla hash, diccionario, colección, pila, cola, etc. Y dado que un arreglo
puede contener otros arreglos, también es posible formar árboles o arreglos
multidimensionales.

Un arreglo puede ser creado utilizando la función constructora del lenguaje
`array()`. En la cual hay un conjunto de pares *clave*/*valor* separados por
coma.

```
array(
    clave  => valor,
    clave2 => valor2,
    clave3 => valor3,
    ...
)
```

Ejemplo de arreglo simple:
```php
<?php
$numeros = array(1, 2, 3, 4, 5);

$cadenas = array("Alfa", "Bravo", "Charlie", "Delta");
```

Los arreglos en PHP son heterogéneos, lo que significa que el mismo arreglo
puede contener elementos de diferentes tipos de datos, aunque estos no tengan
relación directa.

```php
<?php
$mixto = array(
    1,                  // entero
    2,                  // entero
    "tres",             // cadena
    4.0,                // flotabte
    "5",                // cadena numérica
    new stdClass(),     // objeto
    true,               // booleano
    8,                  // entero
    array(9, 9.5, 9.9), // arreglo
    10                  // entero
);
```

##### Claves

Las claves en los arreglos son los valores con los que se pueden indizar los
elementos de un arreglo, estos pueden ser enteros o cadenas.

```php
<?php
$arreglo = array(   // <-- El arreglo contiene únicamente claves numéricas.
    0   => 'Cero',
    1   => 'Uno',
    2   => 'Dos',
    3   => 'Tres'
);

$diccionario = array(
    '09290324'  => 'Osiel',
    '09290325'  => 'Elva',
    '09290326'  => 'Nancy',
    '09290327'  => 'Martha',
    '09290328'  => 'Francisco',
    '09290329'  => 'Oscar'
);
```

En caso de que se quieran registrar otros tipos de datos, ocurren
las siguientes conversiones:
* **Cadenas:** Que tengan enteros decimales, a menos de que el número sea
  precedido por un signo de +, se convertirá en un tipo de entero. Es decir,
  que `"8"` se almacenará como `8` (entero positivo ocho).
* **Flotantes:** Los flotantes tambien se convierten en enteros, lo que significa
  que su parte fraccional será truncada. Ejemplo `8.7` se convertirá en `8`.
* **Booleanos:** Serán convertidos a enteros. `true` será `1`, y `false` será `0`
* **Null:** Se convertirán a cadenas vacías.
* **Arreglos y objetos:** no se permiten como claves y se arrojará una advertencia.

```php
<?php
$arreglo = array(
    1    => "a",
    "1"  => "b",
    1.5  => "c",
    true => "d",
);
var_dump($arreglo);
```

```
array(1) {
    [1] =>
    string(1) "d"
}
```

* **Variedad de funciones de arreglos**  
  <https://www.php.net/manual/es/ref.array.php>

#### Objetos


#### Recursos


#### NULL


#### Callbacks



[2]: https://www.php.net/manual/en/language.types.php