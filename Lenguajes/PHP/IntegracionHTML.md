PHP: Integración con HTML
=======================================

- [PHP: Integración con HTML](#php-integraci%c3%b3n-con-html)
  - [Convertir a objetos de PHP](#convertir-a-objetos-de-php)
  - [Colocándolo en HTML](#coloc%c3%a1ndolo-en-html)
  - [Separando la lógica de la presentación](#separando-la-l%c3%b3gica-de-la-presentaci%c3%b3n)
    - [Haciendo el código modular](#haciendo-el-c%c3%b3digo-modular)

El siguiente ejercicio muestra como integrar PHP con HTML, para los siguiente se
utilizará el archivo `categorias.json` el cual representa un conjunto de datos.

Estos ejemplos pueden ser reinterpretados utilizando bases de datos o
servicios web y otros recursos como origen de datos.

> Consultar la [Guía de Sintaxis de JSON][2] para conocer la sintaxis.

Convertir a objetos de PHP
---------------------------------------

**Archivo `/categorias.json`**
```json
[
    {
        "id_categoria": 1,
        "nombre":   "Vehículos"
    },
    {
        "id_categoria": 2,
        "nombre": "Tecnología"
    },
    {
        "id_categoria": 3,
        "nombre": "Hogar y electrodomésticos"
    },
    {
        "id_categoria": 4,
        "nombre": "Joyas y Relojes"
    }
]
```

El primer paso consiste en interpretar el archivo en formato JSON anterior, para
construirlos en objetos y arreglos de PHP.

**Archivo `/categorias.php`]**
```php
<?php
// Leer el archivo en forma de cadena y guardar los datos en la variable $categorias_json
$categorias_json = file_get_contents("categorias.json");

// Convertir la cadena JSON en variables utilizables de PHP
$categorias = json_decode($categorias_json);

// Imprimir el contenido de la variable para asegurarnos de que se haya interpretado
// correctamente.s
print_r($categorias);
```

Al ejecutar el código anterior el resultado es el siguiente:

```
Array
(
    [0] => stdClass Object
        (
            [id_categoria] => 1
            [nombre] => Vehículos
        )

    [1] => stdClass Object
        (
            [id_categoria] => 2
            [nombre] => Tecnologia
        )

    [2] => stdClass Object
        (
            [id_categoria] => 3
            [nombre] => Hogar y electrodomésticos
        )

    [3] => stdClass Object
        (
            [id_categoria] => 4
            [nombre] => Joyas y Relojes
        )

)
```

Como es posible identificar en la decodificación, la estructura se traduce a
un arreglo con 4 elementos, cada elemento corresponde a un objeto de la clase
[`stdClass`][1] (la cual se utiliza para representar objetos genéricos), cada
uno de los objetos tiene dos atributos `id_categoria` y `nombre`.

La forma para recorrer y obtener los datos de este arreglo es la siguiente:

**Archivo `/categorias.php`**
```php
<?php
// ... Código para obtener JSON y variable $categorias

foreach ($categorias as $categoria) {
    echo "$categoria->id_categoria: $categoria->nombre<br/>";
}
```

La salida del código anterior es la siguiente:

```
1: Vehículos
2: Tecnologia
3: Hogar y electrodomésticos
4: Joyas y Relojes
```

Colocándolo en HTML
---------------------------------------

**Archivo `/categorias.php`**
```php
<?php
// Leer el archivo en forma de cadena y guardar los datos en la variable $categorias_json
$categorias_json = file_get_contents("categorias.json");

// Convertir la cadena JSON en variables utilizables de PHP
$categorias = json_decode($categorias_json);
?>
<table>
    <thead>
        <tr>
            <th>ID</th>
            <th>Nombre</th>
        </tr>
    </thead>
    <tbody>
        <?php foreach($categorias as $categoria): ?>
        <tr>
            <td><?=$categoria->id_categoria?></td>
            <td><?=$categoria->nombre?></td>
        </tr>
        <?php endforeach; ?>
    </tbody>
</table>
```

El resultado de la ejecución del código anterior es el siguiente:

```html
<table>
    <thead>
        <tr>
            <th>ID</th>
            <th>Nombre</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>Vehículos</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Tecnologia</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Hogar y electrodomésticos</td>
        </tr>
        <tr>
            <td>4</td>
            <td>Joyas y Relojes</td>
        </tr>
    </tbody>
</table>
```

Posiblemente se haya notado que la sintaxis de `foreach` utilizó `:` en lugar de
`{` para iniciar el bloque, así como `endforeach` en lugar de `}` para terminarlo.
Esta es una sintaxis alternativa, que resulta conveniente utilizarla dentro del
código HTML, puesto que es mucho más explícita y fácil de identificar,
particularmente dentro entre bloques con identación regular, donde el orden
de las llaves puede perderse fácilmente.

```php
<?php
// Leer el archivo en forma de cadena y guardar los datos en la variable $categorias_json
$categorias_json = file_get_contents("categorias.json");

// Convertir la cadena JSON en variables utilizables de PHP
$categorias = json_decode($categorias_json);
?>
<select name="categoria">
    <?php foreach($categorias as $categoria): ?>
    <option value="<?=$categoria->id_categoria?>"><?=$categoria->nombre?></option>
    <?php endforeach; ?>
</select>
```

Separando la lógica de la presentación
---------------------------------------

Para los ejemplos anteriores se utilizó un único archivo PHP que realizara
la consulta y desplegara los datos.

En grandes proyectos esto se vuelve poco viable, debido a la fuerte dependencia
entre el diseño de la interfaz y la lógica de negocio, por lo que han surgido
diversos patrones de diseño de sistemas como los son MVC, MVP o MVVM.

Considerando esta separación, la estructura de la vista debe ser como se
muestra a contiuación:

**Archivo `/vistas/categorias/tabla.php`**
```php
<table>
    <thead>
        <tr>
            <th>ID</th>
            <th>Nombre</th>
        </tr>
    </thead>
    <tbody>
        <?php foreach($categorias as $categoria): ?>
        <tr>
            <td><?=$categoria->id_categoria?></td>
            <td><?=$categoria->nombre?></td>
        </tr>
        <?php endforeach; ?>
    </tbody>
</table>
```

El archivo anterior contiene únicamente la parte visual en HTML. Y podrá
utilizarse indistintamente del lugar del donde sea hubicado, para hacer lo
anterior, se debe hacer la siguiente modificación el código de lógica.

**Archivo `/categorias.php`**
```php
<?php
// Leer el archivo en forma de cadena y guardar los datos en la variable $categorias_json
$categorias_json = file_get_contents("categorias.json");

// Convertir la cadena JSON en variables utilizables de PHP
$categorias = json_decode($categorias_json);

// Incluye el archivo de la vista
include './vistas/categorias/tabla.php';
```

Utilizando la instrucción `include` se hace referencia al archivo externo de la
vista, colocando una ruta relativa al archivo.

### Haciendo el código modular

En el ejemplo anterior se hace referencia a la ubicación relativa de la vista
`/vistas/categorias/tabla` utilizando la instrucción `include`. Lo anterior
puede funcionar siempre y cuando todos los archivos a los que se haga referencia
tengan exactamente la misma ruta, al introducir el archivo en algún directorio
(carpeta), las direcciones relativas cambian, y por tanto los archivos dejan
de ser encontrados por la aplicación.

Para evitar el problema anterior se recomienda utilizar una función que
normalice las direcciones de los archivos, de manera que, todas las referencias
realizadas siempre apunten a la dirección correcta.

En el siguiente ejemplo se creará el archivo `utilerias.php` el cual
contiene la función `vista`, que nos permitirá cargar todas las vistas desde
el directorio `/vistas` del proyecto.

> En esta práctica se utilizan constantes predefinidas para gestionar rutas
> absolutas dentro de las aplicaciones.
> [Consultar más información](Constantes.md).

**Archivo `/utilerias.php`**
```php
<?php
// Prevenir que la función se intente definir más de una vez, en caso de que se
// incluya más de una vez el mismo archivo.
if (!function_exists('vista')) {
    /**
    *  Esta función toma una dirección de la vista y la despliega.
    *
    *  @param string $ruta_vista Ruta relativa al directorio 'vistas' con el archivo php correspondiente.
    *  @param array $vars Arreglo asociativo con las variables que se utilizarán en la vista.
    */
    function vista($ruta_vista, $vars = array())
    {
        // Extrae los valores del arreglo y se asigna la clave como nombre
        // de la variable.
        extract($vars);

        // Asigna la constante DIRECTORY_SEPARATOR a un nombre más corto.
        // En Windows equivale a `\`, en otros sistemas es `/`
        $ds = DIRECTORY_SEPARATOR;

        // Elimina las `/` al principio de la ruta, para evitar duplicidad.
        $ruta_vista = ltrim($ruta_vista, '/');  

        // Se normaliza la '/' para que sea compatible con todos los sistemas.
        $ruta_vista = str_replace('/', $ds, $ruta_vista);

        // Incluye el archivo para que se despliegue.
        include __DIR__ . $ds . 'vistas' . $ds . $ruta_vista . '.php';
    }
}
```

Una vez creada la función anterior, es posible utilizarla en el archivo
donde sea requerido. Por ejemplo en `categorias.php`, donde se remplaza la
inclusión de `/vistas/categorias/tabla.php`, por la inclusión de `utilerias.php`
y posteriormente se invoca la vista correspondiente, relativa al directorio
`/vistas` y omitiendo la extensión `.php`.

**Archivo `categorias.php`**
```php
<?php
// Leer el archivo en forma de cadena y guardar los datos en la variable $categorias_json
$categorias_json = file_get_contents("categorias.json");

// Convertir la cadena JSON en variables utilizables de PHP
$categorias = json_decode($categorias_json);

// Incluye el archivo `utilerias.php` para cargar la función `vista`
include_once './utilerias.php';

// Se invoca la función `vista` con sus argumentos para inicializar la interfaz
vista('categorias/tabla', array(
    'categorias' => $categorias
));
```

[1]: https://www.php.net/manual/es/language.types.object.php#language.types.object.casting
[2]: ../../FileFormats/JSON.md