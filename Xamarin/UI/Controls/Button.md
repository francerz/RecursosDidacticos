Button
=======
`Xamarin.Forms.Button`

*Un botón responde a un toque o click que dirige una aplicación o realiza una
tarea concreta*

El botón, es el control interactivo más fundamental n todo Xamarin.Forms.
El `Button` usualmente despliega una cadena de texto corta indicando un comando,
pero también puede mostrar una imagen de mapa de bits, o combinar texto e
imagen. El usuario presiona el `Button` con un dedo o hace clic con un ratón
para iniciar el comando.

## Eventos

Los eventos de los controles permiten realizar tareas concretas, cuando se
realiza una acción sobre los mismos, permitiendo manejar la interactividad.

### Clic
`Button` define un evento `Clicked` que se dispara al momento de que un usuario
pulsa el botón con el dedo o el puntero del ratón. La acción del evento al
momento que se libera el dedo o el botón del ratón de la superficie del botón.

> **NOTA:** El botón debe tener la propiedad `IsEnabled` en `true` para
> responder a la interacción.

#### Ejemplo

Código XAML
```xml
<Button Text="Presioname"
        VerticalOptions="CenterAndExpand"
        HorizontalOptions="Center"
        Clicked="BtnPresionameOnClicked" />
```

Código C#
```C#
async void BtnPresionameOnClicked(object sender, EventArgs args)
{
    await DisplayAlert("Hola","Botón presionado", "OK");
}
```

### Pressed

`Button` define el evento `Pressed` el cual se dispara en el momento presiona el
botón con el dedo o el puntero del ratón. La acción se ejecuta al momento de que
se hace la presión sobre el botón.

### Released
`Button` define también el evento `Released` el cual se dispara al momento de
que se suelta el botón. El evento `Released` se acompaña del evento `Clicked`
que ocurre al mismo tiempo, pero si el dedo o el puntero del ratón se desliza
fuera de la superficie del `Buttton` antes de soltarlo. El evento `Clicked`
podría no ocurrir.

#### Ejemplo
```xml
<Button Text="Presionable"
        Pressed="BtnPresionableOnPressed"
        Released="BtnPresionableOnReleased" />
```

## Desde código C#

El siguiente código de C# realiza las siguientes actividades:
* Crear `boton` del tipo `Button`.
* Asignar valores a las propiedades de `boton`.
* Asignar el método manejador de `Clicked` de `boton`.
* Crear un `StackLayout` y asignarlo al `Content` de la `Page`.
* Asignar `boton` como `Children` del `StackLayout` creado.

```C#
// Crear el botón
Button boton = new Button {
    Text = "Presioname",
    VerticalOptions = LayoutOptions.CenterAndExpand,
    HorizontalOptions = LayoutOptions.Center
};
boton.Clicked += BtnPresionameOnClicked;

Button boton2 = new Button { Text = "Presionable" };
boton2.Pressed += BtnPresionableOnPressed;
boton2.Released += BtnPresionableOnReleased;

// Crear el layout y poner los botones
Content = new StackLayout
{
    Children =
    {
        boton,
        boton2
    }
};
```

Debido a que la acción que tiene el botón al hacer clic ocurre en una sola
línea. Se puede asignar el evento `Clicked` de la siguiente manera:

```C#
boton.Clicked += async(sender, args) => await DisplayAlert("Hola", "Boton presionado", "OK");
```

## Deshabilitar el botón

Algunas veces una aplicación se encuentra en un estado particular donde la
acción de clic en el botón no es válida. Para esos casos, el botón puede
deshabilitarse utilizando la propiedad `IsEnabled` en `false`.

```C#
// Deshabilitar el botón (no acepta la acción clic)
boton.IsEnabled = false;

// Habilitar el botón
boton.IsEnabled = true;
```