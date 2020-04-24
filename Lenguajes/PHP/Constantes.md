PHP: Constantes Predefinidas
=======================================

El lenguaje PHP ofrece un confjunto de constantes predefinidas para los scripts
en ejecución, muchas de las constantes se crean con diferentes extensiones y
sólo estarán presentes si las extensiones están disponibles.

En PHP las constantes se identifican principalmente por el uso del estilo
[`PascalCase`](../../Glosarios/ProgrammingStyle.md#pascalcase)

Constantes Mágicas[[1]]
---------------------------------------

Existen nueve constantes mágicas que cambian su valor dependiendo del contexto
en donde se utilicen, y resultan de utilidad para esclarecer funciones
especiales basadas en el contexto.

Las constantes mágicas generalmente se identifican por iniciar y terminar con
doble guión bajo `__`.

| **Nombre**              | **Descripción**
| ----------------------- | ---
| **__LINE__**            | El número de línea en el archivo actual.
| **__FILE__**            | Ruta completa y nombre del archivo con los enlaces simbólicos resueltos. Si se utiliza dentro de un `include`, devolverá el nombre del archivo incluido.
| **__DIR__**             | Directorio del archivo. Si se utiliza dentro de un `include`, devolverá el directorio del archivo incluido. Esta constante equivale a `dirname(__FILE__)`. El nombre del directorio no lleva diagonal al final (`/`), salvo que se trate del directorio raiz.
| **__FUNCTION__**        | Nombre de la función.
| **__CLASS__**           | Nombre de la clase. El nombre de la clase incluye el *namespace* declarado.
| **__TRAIT__**           | Nombre del trait. El nombre del trait incluye el *namespace* en el que fue declarado.
| **__METHOD__**          | Nombre del método de la clase.
| **__NAMESPACE__**       | Nombre del espacio de nombres actual.
| **NombreClase::class**  | El nombre de clase completamente.

Constantes de extensión DIR[[2]]
---------------------------------------

| **Nombre** | **Descripción**
| ---------- | ----------------
| **DIRECTORY_SEPARATOR** | Representa el símbolo utilizado para separa las carpetas. En Windows es `\` diagonal invertida, en Linux y MacOS es `/`.
| **PATH_SEPARATOR** | Punto y coma `;` en Windows, dos puntos `:` en caso contrario.
| **SCANDIR_SORT_ASCENDING** | Se utiliza en conjunto con función [scandir][3].
| **SCANDIR_SORT_DESCENDING** | Se utiliza en conjunto con función [scandir][3].
| **SCANDIR_SORT_NONE** | Se utiliza en conjunto con función [scandir][3].

[1]: https://www.php.net/manual/es/language.constants.predefined.php
[2]: https://www.php.net/manual/es/dir.constants.php
[3]: https://www.php.net/manual/es/function.scandir.php