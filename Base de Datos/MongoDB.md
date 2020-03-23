MongoDB
=================

  * Listar todas las bases de datos:
    ```js
    db.adminCommand({ listDatabases:1 })
    ```
  * Listar todas las bases de datos con filtro de tamaño:
    
    ```js
    // Tamaño mayor a 50000 bytes
    db.adminCommand({ listDatabases:1, filter:{sizeOnDisk:{$gt:50000}} })

    // Tamaño menor a 50000 bytes
    db.adminCommand({ listDatabases:1, filter:{sizeOnDisk:{$lte:50000}} })
    ```

    Operadores de comparación:
    Nombre| Operación | Descripcion
    ---|---|---
    `$eq`   | `=` |Coincide con valores que son iguales al valor especificado.
    `$ne`   | `!=` |Coincide con valores que no son iguales al especificado.
    `$gt`   | `>` |Coincide con valores que son mayores a los especificados.
    `$gte`  | `>=` |Coincide con valores que son mayores o iguales a los especificados.
    `$lt`   | `<` |Coincide con valores que son menores que el valor especificado.
    `$lte`  | `<=` |Coincide con valores que son menores o iguales al especificado.
    `$in`   |  |Coincide con valores que se encuentren en un arreglo.
    `$nin`  |  |No coincide con alguno de los valores especificados en un arreglo.

  * Listar el nombre de todas las bases de datos:
    ```js
    db.adminCommand({ listDatabases:1, nameOnly:1 })
    ```
  * Seleccionar una base de datos (viajes):
    ```js
    use viajes
    ```
  * Listar nombres de las colecciones en la base base de datos actual:
    ```js
    db.runCommand({ listCollections:1, nameOnly:1 })
    ```
  * Mostrar todos los documentos en una colección:
    ```js
    db.viajes.find()
    ```
  * Obtener de todos los viajes únicamente el pais y la ciudad
    ```js
    db.viajes.find({}, {_id:false, pais:true, ciudad:true})
    ```
  * Aplicando filtros en la búsqueda.
    ```js
    // Buscar todos los viajes cuyo país sea Canada
    db.viajes.find({pais:{$eq:"Canada"}})

    // Buscar todos los viajes cuyo pais empiece con Ca
    db.viajes.find({pais:{$regex:/^Ca/}})

    // Buscar todos los viajes cuyo pais termine con a (mayúscula o minúscula)
    db.viajes.find({pais:{$regex:/a$/i}})

    // Buscar todos los viajes cuyo nombre de pais contenga acento ortográfico
    db.viajes.find({pais:{$regex:/[áéíóú]/i}})

    // Buscar todos los viajes cuyo nombre de pais no contenga acento ortográfico
    db.viajes.find({pais:{$not:/[áéíóú]/i}})
    ```

    ```js
    db.viajes.findAndModify({
      query: {
        pais:{$eq:"Cambodia"}
      },
      update: {
        $set: {
          pais: "Cambodya"
        }
      }
    })
    ```

    ```js
    db.viajes.deleteMany({
      pais:"Cambodya"
    })
    ```