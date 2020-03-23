XAML (eXtensible Application Markup Language)
=============================================

Es el lenguaje del formato para el diseño de las interfaces de las aplicaciones, desarrollado por Microsoft en el Framework .NET, con la intención de sustituir
a Windows Forms, con el modelo WPF (*Windows Presentation Foundation*).

Este lenguaje y su conceptualización han sido portados a otras tecnologías de
la compañía, como son Silverlight, Windows Phone, aplicaciones modernas de Windows 8 y Windows 10.

La estructura del lenguaje está basada en el formato XML, sólo que optimizado
para el diseño de interfaces de usuario gráficamente potentes. Por lo general
las interfaces de usuario desarrolladas con este lenguaje son asíncronas y el
proceso de dibujado ocurre utilizando la GPU si se encuentra disponible,
permitiendo elaborar interfaces fluidas y dinámicas.

Actualmente es la base para el desarollo de aplicaciones multiplataforma en
Xamarin, utilizando el conjunto de paquetes **Xamarin.Forms**.

Formato
--------

Cuando se representa como texto, los archivos XAML son archivos XML que
generalmente tienen la extensión `.xaml`. Los archivos pueden utilizar cualquier
codificación de XML, aunque lo más común es utilizar UTF-8.

XAML permite la utilización de la arquitectura de aplicaciones **MVVM (Model-View-ViewModel)** en la que los datos son vinculados a elementos visuales
sin necesidad de realizar escritura o actualización de los mismos.

### Ventajas

* XAML es más fácil de leer que el código equivalente.
* La jerarquía de elementos que utiliza XML, permite simular con mayor precisión
  la claridad visual en las jerarquías de objetos en una interfaz de usuario.
* XAML puede ser escrito con facilidad, pero también puede ser administrado
  por herramientas de diseño visual.

### Desventajas

* XAML no puede contener código. Todos los manejadores de eventos se escriben en un archivo independiente de código.
* XAML no puede contener ciclos o procesamiento iterativo. (Sin embargo, muchos
  objetos visuales pueden generar los elementos utilizando la colección
  `ItemsSource` y aplicar plantillas).
* XAML no puede contener procesamiento condicional (Sin embargo, el enlace de
  datos permite hacer conexiones de código que permiten el procesamiento condicional).
* XAML no puede instanciar clases que no definan un constructor sin parámetros.
* XAML por lo general no contiene métodos.

### Diferencias con XML

XAML es básicamente XML, pero contiene algunas características únicas de
sintaxis. Las más importantes son:

* Elementos propiedad
* Propiedades adjuntas.
* Extensiones de marcado.

Estas características *no son* extensiones de XML. XAML es un XML completamente
legal. Pero estas características sintácticas utilizan XML de manera única.

[XAML for XAMARIN](../../Xamarin/UI/XAML.md)