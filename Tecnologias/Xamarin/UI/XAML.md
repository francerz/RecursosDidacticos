XAML
===========

# Estructura para Xamarin

En el proyecto compartido de una solución de Xamarin.Forms existen los siguientes archivos:

* **App.xaml**, el archivo XAML; y
* **App.xaml.cs**, un *código de respaldo* asociado al archivo XAML.

Es necesario hacer clic en la flecha junto a **App.xaml** para ver el archivo de
código de respaldo.

Ambos **App.xaml** y **App.xaml.cs** contribuyen a una clase denominada `App`
que deriva(hereda) de la clase `Application`.

La mayoría de otras clases con archivos XAML derivan de `ContentPage`; aquellos
archivos que utiliza XAML para definir los componentes visuales de una página
completa.

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:local="clr-namespace:MyProject.Views"
             x:Class="MyProject.Views.MyPage">
    <!-- Contenido de la pagina -->
    <StackLayout>
        <Label Text="¡Hola Mundo!"
               VerticalOptions="CenterAndExpand"
               HorizontalOptions="Center" />
    </StackLayout>
</ContentPage>
```