Estilos Rápidos
=================================================

Estos son algunos conjuntos de estilos básicos comunmente utilizados para
personalizar los componentes.

Botones
-------------------------------------------------

```css
button,
input[type=button],
input[type=submit],
input[type=reset],
.button {
    text-align: center;     /* Texto centrado */
    cursor: pointer;        /* Poner cursor de mano 👆*/
    color: black;           /* Poner texto color negro */
    background: gray;       /* Poner fondo color gris */
    border: 1px solid transparent; /* Poner borde transparent */
    border-radius: 4px;     /* Poner esquinas redondeadas */
    padding: 0.5em 1em;     /* Separación entre el borde y contenido */
    display: inline-block;  /* Mostrar como bloque en línea */
    box-sizing: border-box; /* Restringir medidas a caja de contorno */
    font: inherit;          /* Normalizar fuente de todos los botones */
}
button:hover {
    background: lightgray;
    border-color: blue;
    text-decoration: none;  /* Quitar subrayado en etiquetas <a> */
}
button:active {
    color: white;
    background: darkgray;
}
button:focus {
    outline: 1px solid black;
    outline-offset: -4px;
}
button:disabled {
    color: darkgray;
    background: gray;
    border-color: transparent;
}
```

```html
<button>button</button>
<button disabled>button:disabled</button>
<input type="button" value="input[type=button]" />
<input type="submit" value="input[type=submit]" />
<input type="reset" value="input[type=reset]" />
<a class="button">a.button</a>
```

<button>button</button>
<button disabled>button:disabled</button>
<input type="button" value="input[type=button]" />
<input type="submit" value="input[type=submit]" />
<input type="reset" value="input[type=reset]" />
<a class="button">a.button</a>


<style>
button,
input[type=button],
input[type=submit],
input[type=reset],
.button {
    text-align: center;     /* Texto centrado */
    cursor: pointer;        /* Poner cursor de mano 👆*/
    color: black;           /* Poner texto color negro */
    background: gray;       /* Poner fondo color gris */
    border: 1px solid transparent; /* Poner borde transparent */
    border-radius: 4px;     /* Poner esquinas redondeadas */
    padding: 0.5em 1em;     /* Separación entre el borde y contenido */
    display: inline-block;  /* Mostrar como bloque en línea */
    box-sizing: border-box; /* Restringir medidas a caja de contorno */
    font: inherit;          /* Normalizar fuente de todos los botones */
}
button:hover {
    background: lightgray;
    border-color: blue;
    text-decoration: none;  /* Quitar subrayado en etiquetas <a> */
}
button:active {
    color: white;
    background: darkgray;
}
button:focus {
    outline: 1px solid black;
    outline-offset: -4px;
}
button:disabled {
    color: darkgray;
}
</style>