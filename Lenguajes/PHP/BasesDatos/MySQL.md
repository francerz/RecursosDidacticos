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

### Encapsular en función



Manipulación de datos
---------------------------------------

### Inserción

```php
<?php
$conexion = conectar_mysql();

$num_control = $conexion->escape_string("17460237");
$nombres     = $conexion->escape_string("Victoria Elizabeth");
$apellido1   = $conexion->escape_string("Rivera");
$apellido2   = $conexion->escape_string("Fuentes");


$conexion->query("INSERT INTO alumnos (num_control, nombres, apellido1, apellido2)
    VALUES ($num_control, $nombres, $apellido1, $apellido2)");
```

> **Nota:**  
> La función `escape_string()` y `real_escape_string()` se utiliza para
> sustituir los caracteres que pueden ser confundidos con sintaxis de SQL.
> Por ejemplo, se escapan las comillas simples (`'`) dentro de una cadena por
> `\'`, que de no hacerse podría interpretearse como el cierre de la cadena.
> Hacer esto **es muy importante** debido a que previene ataques de de inyección
> SQL.