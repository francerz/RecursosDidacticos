```json
[
    { id_carrera:  1, nombre: "Arquitectura" },
    { id_carrera:  2, nombre: "Contador Público" },
    { id_carrera:  3, nombre: "Ingeniería Ambiental" },
    { id_carrera:  4, nombre: "Ingeniería Bioquímica" },
    { id_carrera:  5, nombre: "Ingeniería en Gestión Empresarial" },
    { id_carrera:  6, nombre: "Ingeniería Industrial" },
    { id_carrera:  7, nombre: "Ingeniería Informática" },
    { id_carrera:  8, nombre: "Ingeniería Mecatrónica" },
    { id_carrera:  9, nombre: "Ingeniería en Sistemas Computacionales" },
    { id_carrera: 10, nombre: "Licenciatura en Administración" },
]
```

```html
<form method="POST" action="alumnos.php">
    <div>
        <label for="txtNombre">Nombre:</label>
        <input id="txtNombre" type="text" name="nombre" required />
    </div>
    <div>
        <label for="txtApellido1">Primer apellido:</label>
        <input id="txtApellido1" type="text" name="apellido1" required />
    </div>
    <div>
        <label for="txtApellido2">Segundo apellido:</label>
        <input id="txtApellido2" type="text" name="apellido2" />
    </div>
    <div>
        <label for="txtCURP">C.U.R.P.:</label>
        <input id="txtCURP" type="text" name="curp" pattern="[A-Z]{4}[0-9]{6}[HM][A-Z]{5}[0-9A-Z][0-9]" required />
    </div>
    <div>
        <button type="submit">Registrar</button>
    </div>
</form>
```