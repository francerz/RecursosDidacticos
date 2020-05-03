PHP: Servidor REST nativo
=======================================



Requisitos Previos
---------------------------------------

+ [HTTP: Aspectos Técnicos](../../../Protocolos/HTTP/AspectosTecnicos.md)
+ [URL (Uniform Resource Locator)](../../../Protocolos/URI/URL.md)
+ [REST (REpresentational State Transfer)](../../../Tecnologias/ServiciosWeb/REST.md)
+ [PHP: Manejo del protocolo HTTP](../ManejoHTTP.md)
+ [PHP: Acceso a base de datos MySQL](../BasesDatos/MySQL.md)

Planteamiento del ejercicio
---------------------------------------

```sql
CREATE DATABASE ejemplo_rest
    DEFAULT COLLATE 'utf8_spanish_ci';

USE ejemplo_rest;

CREATE TABLE alumnos (
    id_alumno   INTEGER     NOT NULL    AUTO_INCREMENT,
    num_control VARCHAR(20) NOT NULL,
    nombres     VARCHAR(50) NOT NULL,
    apellido1   VARCHAR(20) NOT NULL,
    apellido2   VARCHAR(20),
    PRIMARY KEY (id_alumno),
    UNIQUE KEY  (num_control)
);
```