PHP: Acceso a base de datos MySQL
=======================================
Una de las principales funcionalidades de las aplicaciones dinámicas, es el
almacenamiento y consulta persistente de datos, generalmente estos se almacenan
en diversos contenedores, que por la naturaleza multiusuario de los sistemas web,
la estrategia más común para implementarlo es mediante bases de datos.

Conexión a la base de datos
---------------------------------------

Para establecer la conexión con la base de datos, es necesario contar con
la configuración que permitirá el acceso. Esta configuración es proporcionada
por el proveedor de servicio de base de datos.

La conexión se realiza de la siguiente forma:
```php
<?php
// definir los parámetros de conexión
$db_serv = 'localhost';     // nombre o dirección del servidor de base de datos
$db_user = 'root';          // nombre de usuario
$db_pwrd = '12345';         // contraseña asociada al usuario (si existe)
$db_name = 'bd_ejemplo';    // nombre de la base de datos
$db_port = 3306;            // puerto de acceso 

// crear objeto y establecer conexión
$mysqli = new mysqli($db_serv, $db_user, $db_pwrd, $db_name, $db_port);

// verificar si la conexión fue fallida y reportar el fallo.
if ($mysqli->conect_errno) {
    echo "Fallo al conectar a MySQL: $mysqli->connect_error";
}
```

### Código reutilizable

Debido a que los parámetros de la conexión (servidor, usuario, contraseña)
pueden cambiar con el paso del tiempo, y la acción de conectarse a una base de
datos se realiza en diferentes momentos de la aplicación conviene encapsular
el código de manera reutilizable.

```php
<?php
/**
 * Clase envoltorio de conexiones a bases de datos de MySQL.
 */
class MySQLDB
{
    static private $config = [];
    static private $conexiones = [];

    /**
     * Registra los parámetros de conexión de base de datos y los asocia a un
     * nombre ($alias) para identificarlos.
     *
     * @param string $alias     nombre de la conexión
     * @param string $database  nombre de la base de datos
     * @param string $user      nombre de usuario que se conecta a base de datos
     * @param string $password  contraseña del usuario que se conecta a la base de datos
     * @param string $server    nombre o dirección de servidor de base de datos
     * @param string $port      número del puerto de acceso
     */
    static public registrar($alias, $database, $user, $password = '', $server = 'localhost', $port = 3306)
    {
        static::$config[$alias] = array(
            'database' => $database,
            'user' => $user,
            'password' => $password,
            'server' => $server,
            'port' => $port
        );
    }

    /**
     * Establece o reutiliza una conexión abierta de base de datos mediante el
     * nombre ($alias) de identificación de los parámetros.
     *
     * @param string $alias     nombre de la conexión
     */
    static public conectar($alias)
    {
        if (array_key_exists($alias, static::$conexiones)) {
            return static::$conexiones[$alias];
        }
        if (!array_key_exists($alias, static::$config)) {
            throw new Error("No hay configuración para '$alias' en base de datos.");
        }

        extract(static::$config[$alias]);

        static::$conexiones[$alias] = new mysqli($database, $user, $password, $server, $port);

        return static::$conexiones[$alias];
    }
}

// Registrar los parámetros de conexión de base de datos y asigna el alias `bd`
MySQLDB::register('bd', 'bd_ejemplo', 'root', '12345', 'localhost', 3306);
```

Para utilizar la conexión se puede invocar de la siguiente manera.

```php
<?php
// Conectar a la base de datos con alias `bd`
$conexion = MySQLDB::conectar('bd');
```


Manipulación de datos
---------------------------------------

Las acciones principales de bases de datos incluyen la consulta y manipulación
de los datos, estas son: Inserción, Actualización, Eliminación y Consulta.

En esta sección se describen los mecanismos para realizar cada una de estas
acciones.

### Inserción

La inserción consiste en agregar un nuevo registro a una tabla de la base de
datos. Esta acción se hace mediante la ejecución del comando `INSERT INTO`.

El comando debe construirse mediante la asignación de valores a los parámetros,
generalmente provenientes de variables.

A continuación se presenta la un ejemplo de inserción de datos, con la librería
`mysqli` de PHP.

```php
<?php
// Conectar a la base de datos `bd`
$conexion = MySQLDB::conectar('bd');

// Asignar valores escapados para la sentencia SQL
$num_control = $conexion->escape_string("17460237");
$nombres     = $conexion->escape_string("Victoria Elizabeth");
$apellido1   = $conexion->escape_string("Rivera");
$apellido2   = $conexion->escape_string("Fuentes");

// Ejecutar la sentencia SQL
$resultado = $conexion->query("INSERT INTO alumnos (num_control, nombres, apellido1, apellido2)
    VALUES ('$num_control', '$nombres', '$apellido1', '$apellido2')");

// Verificar el estado de realización de la sentencia SQL
if (!$resultado) {
    throw new Error("Ocurrió un error al insertar: $conexion->error");
} else {
    echo "Insertadas $conexion->affected_rows filas, el primer ID insertado es: $conexion->insert_id.";
}
```

> **Nota:**  
> La función `escape_string()` y `real_escape_string()` se utiliza para
> sustituir los caracteres que pueden ser confundidos con sintaxis de SQL.
> Por ejemplo, se escapan las comillas simples (`'`) dentro de una cadena por
> `\'`, que de no hacerse podría interpretearse como el cierre de la cadena.
> Hacer esto **es muy importante** debido a que previene ataques de de inyección
> SQL.

### Actualización

La actualización consiste en la sustitución de valores por otros en registros
existentes. Para esta operación se utiliza la sentencia `UPDATE` de SQL.

A continuación se presenta la un ejemplo de actualización de datos, con la
librería `mysqli` de PHP.

```php
<?php
// Conectar a la base de datos `bd`
$conexion = MySQLDB::conectar('bd');

// Asignar los valores escapados para la sentencia SQL
$nombres = $conexion->escape_string('Viktoria Elizabeth');
$id = 1;

// Ejecutar sentencia SQL
$resultado = $conexion->query("UPDATE alumnos SET nombres = '$nombres' WHERE id_alumno = '$id'");

// Verificar el estado de realizaciòn de la sentencia SQL
if (!$resultado) {
    throw new Error("Ocurrió un error al actualizar: $conexion->error");
} else {
    echo "Actualizadas $conexion->affected_rows filas.";
}
```

### Eliminación

La acción de eliminación de registro, implica el borrado físico del registro
en la tabla. Esta operación utiliza la sentencia `DELETE` de SQL.

A continuación se presenta la un ejemplo de eliminación de datos, con la
librería `mysqli` de PHP.

```php
<?php
// Conecctar a la base de datos `bd`
$conexion = MySQLDB::conectar('db');

$id = 1;

// Ejecutar sentencia SQL
$resultado = $conexion->query("DELETE FROM alumnos WHERE id_alumno = '$id'");

// Verificar el estado de realización de la sentencia SQL
if (!$resultado) {
    throw new Error("Ocurrió un error al eliminar: $conexion->error");
} else {
    echo "Eliminadas $conexion->affected_rows filas.";
}
```

### Consulta

La consulta es la operación más común en base de datos, puesto que permite
recuperar los datos almacenados. Para esta operación se utiliza la sentencia
`SELECT` del Lenguaje de Consultas Estándar (***SQL***, *Standard Query Language*).

A diferencia de las otras instrucciones (`INSERT`, `UPDATE`, `DELETE`), la
ejecución de una consulta, la cual puede devolver contenido, devuelelve un
objeto `mysqli_result`, el cual representa el resultado de la consulta, y su 
resultado puede extraerse mediante funciones integradas.

A continuación se presenta un ejemplo de una consulta y, en caso
de ejecutarse satisfactoriamente, desplegará los datos en una tabla de HTML.

```php
<?php
// Conectar a la base de datos `bd`
$conexion = MySQLDB::conectar('db');

// Ejecutar la consulta SQL
$resultado = $conexion->query("SELECT * FROM alumnos");

// Verificar que la consulta se haya ejecutado correctamente, en caso contrario
// lanzar un Error.
if (!$resultado) {
    throw new Error("Ocurrió un error al consultar: $conexion->error");
}
?>
<p>Encontrados <?=$resultado->num_rows?> alumnos</p>
<table>
    <thead>
        <tr><th>ID</th>
            <th>Num. Control</th>
            <th>Nombre completo</th>
        </tr>
    </thead>
    <tbody>
        <?php while($alumno = $resultado->fetch_object()): ?>
        <tr><td><?=$alumno->id_alumno?></td>
            <td><?=$alumno->num_control?></td>
            <td><?="$alumno->nombres $alumno->apellido1 $alumno->apellido2"?></td>
        </tr>
        <?php endwhile; ?>
    </tbody>
</table>
```

> **NOTA**  
> Para mantener la modularidad de la estructura de código se puede seguir
> [Separar la lógica de la presentación][1]

[1]:../IntegracionHTML.md#separando-la-l%c3%b3gica-de-la-presentaci%c3%b3n