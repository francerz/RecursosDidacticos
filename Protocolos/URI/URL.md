URL: Uniform Resource Locator
=======================================

El **Localizador de Recursos Uniforme** (más conocido por sus siglas en inglés
**URL**, *Uniforme Resource Locator*) es un tipo de identificador de recursos
uniforme (*Uniform Resource Identifier*, ***URI***) cuyos recursos referidos
pueden cambiar, es decir, la dirección puede apuntar a recursos variables en el
tiempo.
Se conforman por una secuencia de caracteres utilizando un formato modélico y
estándar que designa recursos en una red.

- [URL: Uniform Resource Locator](#url-uniform-resource-locator)
  - [Formato general](#formato-general)
  - [Uso ejemplificado](#uso-ejemplificado)
  - [Recursos adicionales](#recursos-adicionales)

Formato general
---------------------------------------

La estructura general de un URL es la siguiente:

```
userinfo = usuario[:contraseña]
autoridad = [userinfo@]máquina[:puerto]

URI = esquema:[//autoridad]ruta[?consulta][#fragmento]
```

Componentes de la URL:

+ **esquema** (*schema*)  
  Es una secuencia de caracteres que comienzan con una letra y seguida por una
  combinación de letras, dìgitos, signos de más (`+`), puntos (`.`), o guiones
  (`-`).
  Aunque los esquemas no son sensibles a mayúsculas o minúsculas, la forma
  canónica es escribiéndose completamente en minúsculas.
  Algunos ejemplos populares de esquemas incluyen: `http`, `https`, `ftp`,
  `mailto`, `file`, `data`, `irc`.
  Los esquemas deberán ser registrados a la Autoridad de Números Asignados a
  Internet (***IANA***, *Internet Assigned Numbers Authority*).
+ **autoridad** (*authority*)  
  Un componente opcional puede ser precedido por una doble diagonal (`//`):
  + **userinfo**  
    El subcomponente que puede consistir en un nombre de usuario y una
    contraseña opcional, precedida por dos puntos (`:`), seguido por un símbolo
    de arroba (`@`). El uso del formato `usuario:contraseña` ha sido *desaprobado*
    debido a razones de seguridad. Las aplicaciones no deben incluir texto
    claro después delos primeros dos puntos (`:`), a menos de que sea una cadena
    vacía (indicando que no hay contraseña).
  + **máquina**  
    Este subcomponente consiste en un nombre (incluyendo pero no limitado a
    nombre de dispositivo), o una dirección IP, las direcciones IPv4 deben estar
    en formato decimal con puntos, e IPv6 deben encerrarse entre corchetes.
  + **puerto**  
    El subcomponente opcional del puerto de escucha, precedido por dos puntos
    (`:`). Los valores de puerto en el Protocolo de Internet (IP) van desde el
    0 hasta el 65535.
+ **ruta** (*path*)  
  Consiste en una secuencia de segmentos de ruta separados por una diagonal (`/`).
  Las rutas siempre se definen para una URI, incluso aunque la ruta pueda ser
  vacía (longitud cero).
  Un segmento puede también estar vacío, resultando en dos diagonales
  consecutivas (`//`) en el componente de la ruta.  
  El componente de la ruta puede parecerse o coincidir con las rutas de un
  sistema de archivos, aunque no siempre implica una relación con uno. Si se
  especifica un componente de **autoridad**, entonces el componente de ruta
  puede ser vacío o comenzar con una diagonal (`/`).  
  Si el componente de **autoridad** está ausente, la ruta no puede iniciar
  con un segmento vacío, es decir con doble diagonal (`//`), puesto que los
  siguientes caracteres se interpretarían como el componente autoridad.
+ **consulta** (*query_string*)  
  Este componente es precedido por un signo de interrogación de cierre (`?`), y
  contiene datos no jerárquicos. Su formato no está bien definido, pero por
  convención se utiliza una secuencia de **pares de clave-valor** separados
  por un delimitador.
  Por ejemplo: `clave1=valor1&clave2=valor2`
+ **fragmento** (*fragment*)  
  El componente opcional es precedido por una almohadilla o gato (`#`). El
  fragmento contiene un identificador, que proporciona un recurso secundario
  como el encabezado de un artículo, identificado por el residuo de la URI.  
  Cuando el recurso primario es un documento HTML, el fragmento es con
  frecuencia el atributo `id` del elemento específico, y los navegadores harán
  desplazamiento del elemento hacia la vista.

Uso ejemplificado
---------------------------------------

+ **`mailto:correo@dominio.com`**
  
  Utiliza el protocolo `mailto` para preparar un mensaje de correo electrónico
  a la dirección de correo electrónico proporcionada.
  El valor `correo` corresponde al nombre de usuario, seguido de la `@` y la
  máquina o dominio al que corresponde.

+ **`http://www.ejemplo.com`**
  
  Se utiliza el protocolo de hipertexto con el esquema `http` y se conectan
  directamente la autoridad `www.ejemplo.com`. La *ruta* permanece vacía.

+ **`http://www.ejemplo.com:8080`**
  
  Similar al ejemplo anterior, sólo que ahora se especifica el puerto de
  conexión `8080`.

+ **`http://www.ejemplo.com/res/img/fondo.jpg`**
  
  Se utiliza el protocolo de hipertexto con el esquema `http` y se hace la
  conexión a la autoridad `www.ejemplo.com`. La *ruta* se designa mediante
  tres segmentos `res`, `img` y `fondo.jpg`, los cuales representan de manera
  jerárquica la localización del recurso, que se puede interpretar de la
  siguiente manera: El archivo `fondo.jpg` ubicado en el directorio `img` dentro del directorio `res`.

+ **`postgres://pguser:pgpassword@dbserver:5432/my_database`**

  Se utiliza el esquema `postgres` para indicar que se consiste en conexión con
  el motor de base de datos **PostgreSQL**,
  *este esquema no está registrado en la IANA*.

  La autoridad incluye el usuario `pguser`, contraseña `pgpassword`, la máquina
  `dbserver` y el puerto `5432`.

  Adicionalmente se utiliza el apartado correspondiente al **path** para
  localizar la base de datos `my_database`.

+ **`https://www.google.com.mx/search?q=cachorros`**
  
  Se utiliza el protocolo HTTP sobre SSL, identificado por el esquema `https`
  que conecta al dominio `www.google.com.mx`, dentro del dominio se accede
  a la ruta `/search` que corresponde a la búsqueda en la web.

  Se incluye la *cadena de consulta* (*query string*) `q=cachorros` localizada
  después del signo de cierre de interrogación `?`. La interpretación de la
  misma es que la clave `q` tiene el valor `cachorros`.

+ **`https://api.cvu.acad-tecnm.mx/catalogos/carreras?nivel=licenciatura&area=computaci%C3%B3n`**
  
  Se utiliza el protocolo HTTP sobre SSL, identificado por el esquema `https`
  que conecta al dominio `api.cvu.acad-tecnm.mx`, dentro del dominio se accede a
  la ruta `/catalogos/carreras` que corresponde a un listado de todas las
  carreras disponibles.

  En la *cadena de consulta* (*query_string*) `nivel=licenciatura&area=computaci%C3%B3n`
  se aplica un filtro mediante dos parámetros `nivel` y `area`. Los valores de
  dichos parametros se encuentran codificados en formato de URL, debido a que sólo se permite un conjunto limitado de caracteres, para evitar ambigüedad.

  + El valor de `nivel` es `licenciatura`.
  + El valor de `area` es `computación`, donde la `ó` fue sustituida por `%C3%B3`.

+ **`http://app.sitio.com/assets/graphics.svg#logo-pagina`**
  
  Se utiliza el protocolo HTTP con el esquema `http` que conecta al dominio
  `app.sitio.com`, dentro del dominio se accede a la ruta `/assets/graphics.svg`
  la cual corresponde a un archivo.

  Se añade el componente *fragmento* después del `#` para identificar el elemento `logo-pagina` dentro del recurso.

Recursos adicionales
---------------------------------------
+ [Codificador en formato URL](https://www.urlencoder.org/)
+ [Función `urlencode` de PHP](https://www.php.net/manual/es/function.urlencode.php)
+ [Función `urldecode` de PHP](https://www.php.net/manual/es/function.urldecode.php)