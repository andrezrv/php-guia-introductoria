# PHP y MYSQL

## Conexión

Para conectar PHP con una base de datos MySQL, necesitamos usar la función `mysqli_connect()`.

```php
// Conexión:
/**
 * Notas sobre el uso de mysqli_connect():
 *
 * Parámetro 1: dominio o servidor al cual conectarse. Generalmente es "localhost" o "127.0.0.1".
 * Parámetro 2: usuario MySQL. Cuando trabajamos con XAMPP es normalmente "root".
 * Parámetro 3: contraseña del usuario MySQL. Cuando trabajamos con XAMPP suele estar vacía. También puede ser "root" o "password".
 * Parámetro 4: nombre de la base de datos con la que queremos conectarnos.
 */
$mysqli = mysqli_connect( 'localhost', 'user', 'password', 'db' );
```

Es importante guardar el resultado de mysqli_connect() en una variable, o usarlo como valor de retorno en una función, ya que vamos a necesitarlo a la hora de hacer consultas.

## Queries

Para realizar solicitudes a una base de datos se usa la función `mysqli_query()`. Esta función usa como primer parámetro el resultado de una conexión, y como segundo parámetro una solicitud MySQL:

```php
// Conexión.
$mysqli = mysqli_connect( 'localhost', 'user', 'password', 'db' );

// Consulta a base de datos.
$result = mysqli_query( $mysqli, "SELECT * FROM posts" );
```

## Obtención de datos

Para obtener y usar información existente en una base de datos necesitamos, en primer lugar, realizar una consulta MySQL, y luego convertir el resultado de esa consulta en un array.

En el siguiente ejemplo, obtenemos el resultado de una consulta por un valor único (un post con ID igual a 2), lo convertimos en un array (usando `mysqli_fetch_assoc()`) e imprimimos sus valores usando `var_dump()`.

```php
// Conexión.
$mysqli = mysqli_connect( 'localhost', 'user', 'password', 'db' ); 

// Consulta a base de datos.
$result = mysqli_query( $mysqli, "SELECT * FROM posts WHERE id = 2" );

// Si la consulta devuelve resultados ...
if ( mysqli_num_rows( $result ) ) {
    // Se convierte el resultado en un array.
    $row = mysqli_fetch_assoc( $result );

    var_dump( $row );
}
```

Nótese que se chequea si la consulta obtuvo valores con la función `mysqli_num_rows()`, ya que de lo contrario PHP puede mostrar errores o advertencias al intentar convertir el resultado en un array.

**Para obtener y usar múltiples datos**, el proceso es muy similar, aunque va a usarse un `while()` para poder procesar todos los valores:

```php
// Conexión.
$mysqli = mysqli_connect( 'localhost', 'user', 'password', 'db' ); 

// Consulta a base de datos.
$result = mysqli_query( $mysqli, "SELECT * FROM posts WHERE id = 2" );

// Array donde se van a guardar los valores de cada fila.
$rows = array();

// Si la consulta devuelve resultados ...
if ( mysqli_num_rows( $result ) ) {
    while ( $row = mysqli_fetch_assoc( $result ) ) {
        // Se guarda cada fila en una variable.
        $rows[] = $row;
    }
}

var_dump( $rows );
```

## Insertar datos

La inserción de datos es similar a la obtención: seguimos usando los datos de conexión y `mysqli_query()`, pero en este caso la solicitud hecha a MySQL es del tipo “INSERT”.

Esto suele combinarse con valores ingresados por el usuario, que pueden llegar por medio de un formulario con los métodos GET o POST.

En el siguiente ejemplo tomamos los campos “titulo” y “contenido” enviados a través de un formulario, y los insertamos en la base de datos:

```php
if ( isset( $_POST['titulo'] ) && isset( $_POST['contenido'] ) ) {
    // Conexión.
    $mysqli = mysqli_connect( 'localhost', 'user', 'password', 'db' );

    // Inserción.
    mysqli_query( $mysqli, "INSERT INTO posts (titulo, contenido) VALUES ('" . $_POST['titulo'] . "', '" . $_POST['contenido'] . "')" );
}
```