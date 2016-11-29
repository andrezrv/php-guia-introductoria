# Sesiones

Durante una solicitud a un servidor web (por ejemplo, la carga de una página), una aplicación construida con PHP regenera su información desde cero. Esto significa que, por cada solicitud o vista de página, por defecto, PHP va a regenerar los valores de variables, constantes, objetos y cualquier tipo de información interna a la aplicación.

Esto puede no ser siempre deseable. Por ejemplo, para aplicaciones en las cuales se necesita mantener algún tipo de información acerca del visitante, como aquellas que cuentan con un área administrativa, es necesario que cierta información acerca del usuario actual se mantenga estable a lo largo de varias solicitudes. De esta manera se le podría permitir o denegar el acceso a ciertas áreas o características determinadas del sistema.

PHP permite hacer esto por medio del uso de sesiones de usuario. Las sesiones de usuario permiten almacenar ciertos datos en la memoria del servidor hasta que el navegador se cierre, y dichos datos pueden mantenerse a lo largo de varias visitas o vistas de página.

Para utilizar sesiones en PHP es indispensable realizar un llamado a la función `session_start()` antes de que se imprima cualquier tipo de contenido. Es recomendable usarla lo antes posible en el proceso de ejecución, y generalmente se la ejecuta entre las primeras líneas del archivo principal.

```php
<?php
session_start();
```

La información de la sesión de un usuario se almacena en la variable superglobal `$_SESSION`, la cual se maneja como un array.

Para ilustrar de qué manera `$_SESSION` mantiene los datos de una sesión de usuario, el siguiente ejemplo imprime un número y le suma una unidad por cada vista de la misma página:

```php
<?php
session_start();

if ( ! isset( $_SESSION['count'] ) ) {
    $_SESSION['count'] = 0;
}

$_SESSION['count']++;

echo $_SESSION['count'];
```

Haciendo uso de `$_SESSION` también puede construirse un proceso que muestra cierto contenido al usuario en caso de estar logueado en un sistema, y un formulario de login en caso de no estarlo:

```php
<?php
// Se crea una función para validar nombre de usuario y contraseña.
function validate_user( $username, $password ) {
    if ( $username === 'admin' && $password === '123456' )    {
        // Si los datos son válidos, se crea el valor de sesión.
        $_SESSION['username'] = $username;
    }
}

// Si se envió información a través del formulario, se intenta validar el usuario.
if ( ! empty( $_POST['username'] ) && ! empty( $_POST['password'] ) ) {
    validate_user( $_POST['username'], $_POST['password'] );
}

// Si existe una sesión de usuario, se imprime un mensaje de bienvenida.
if ( isset( $_SESSION['username'] ) ) {
    echo 'Bienvenido usuario!';
} else {
// Si no existe sesión de usuario, se imprime el formulario de contacto.
?>
<form method="POST" action="">
    <label for="username">Nombre de usuario</label>
    <input name="username" type="text" /><br />

    <label for="password">Contraseña</label>
    <input name="password" type="password" /><br />

    <input type="submit" value="Enviar" />
</form>
<?php
}
?>
```