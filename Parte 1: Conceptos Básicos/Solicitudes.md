# Solicitudes

Una de las características principales de PHP es la de poder procesar información ingresada por un usuario de un sitio web. Normalmente, esta información se envía al servidor web por medio de un formulario de contacto o por determinados parámetros añadidos a la URL de un sitio. Este tipo de envío de información es lo que en desarrollo web se llama **solicitud** o **_request_**.

Existen dos tipos de solicitudes, a los que llamamos **métodos**: _POST_ y _GET_. La diferencia entre ambos consiste en que, usando _post_, la información es enviada de forma directa al servidor web, de manera invisible al usuario. Usando _get_, la información se agrega a la URL de la página que procesa la solicitud, lo cual el usuario puede ver en su navegador.

## GET

Una manera de entender cómo funciona el método GET es por medio del análisis de una URL como la siguiente:

`http://localhost/misitio/form.php?nombre=Roque&apellido=Molina`

Al visitar esa URL estaríamos enviando los datos `nombre` y `apellido` al archivo `form.php` ubicado en nuestro sitio. Es importante notar cómo se escriben los datos, con el formato `clave=valor`. El primer dato a enviar estará precedido del caracter `?`, y a partir del segundo dato se usa `&`.

Al recibir los datos en PHP, los mismos quedan guardados en la variable superglobal `$_GET` como un array. De esta forma, los datos enviados en el ejemplo serían equivalentes a esto:

```php
<?php
$_GET = array(
    'nombre'   => 'Roque',
    'apellido' => 'Molina',
);
?>
```

Y podríamos obtenerlos de esta manera:

```php
<?php
echo '¡Hola ' . $_GET['nombre'] . ' ' . $_GET['apellido'] . '!';

// Se imprime "¡Hola Roque Molina!".
?>
```

Las URLs con datos adjuntos tambien pueden generarse automáticamente a partir de un formulario HTML.

```php
<form method="GET" action="form.php">
    <label for="nombre">Nombre</label>
    <input name="nombre" type="text" /><br />

    <label for="apellido">Apellido</label>
    <input name="apellido" type="text" /><br />

    <input type="submit" value="Enviar" />
</form>
```

Al completar los datos y enviar el formulario, el navegador se redirige a la página especificada en el atributo `action` de la etiqueta `form`. Si el valor especificado en el atributo `method` es `GET`, a la URL de redirección se le adjuntan como parámetros todos los valores ingresados en el formulario, y los nombres de sus claves se corresponden con los valores del atributo `name` de cada campo.

Por ejemplo, si en el campo "Nombre", generado con el código HTML `<input name="nombre" type="text" />`, se ingresa el valor "Roque", dado que el valor del atributo `name` del campo es `nombre`, se adjunta a la URL la combinación `nombre=Roque`.

Al completar y enviar el formulario, el navegador nos redirige a una URL similar a la del primer ejemplo:

`http://localhost/misitio/form.php?nombre=Roque&apellido=Molina`

## POST

El método POST evita que la información enviada al servidor web sea visible al usuario, inyectándola al navegador de forma directa. Normalmente se lo usa en combinación con formularios HTML, especificando `POST` en el atributo `method` de la etiqueta `form`.

```php
<form method="POST" action="form.php">
    <label for="nombre">Nombre</label>
    <input name="nombre" type="text" /><br />

    <label for="apellido">Apellido</label>
    <input name="apellido" type="text" /><br />

    <input type="submit" value="Enviar" />
</form>
```

Al igual que con GET, al completar el formulario el navegador redirige al usuario a la página especificada en `action`, pero con la diferencia de que no se agrega información a la URL. Esa información es accesible desde PHP usando la variable superglobal `$_POST`, que también almacena los datos recibidos como un array. De esta manera, si hubiéramos ingresado "Roque" para el nombre y "Molina" para el apellido, el valor de `$_POST` sería este:

```php
<?php
$_POST = array(
    'nombre'   => 'Roque',
    'apellido' => 'Molina',
);
?>
```

Y podríamos obtener la información de la misma manera que con GET:

```php
<?php
echo '¡Hola ' . $_POST['nombre'] . ' ' . $_POST['apellido'] . '!';

// Se imprime "¡Hola Roque Molina!".
?>
```

## REQUEST

En PHP también existe la variable superglobal `$_REQUEST`, que es una combinación de los valores recibidos por POST y por GET, es decir de cualquier tipo de solicitud. Por eso podemos usarla para manipular datos indistintamente del método con el que los hayamos recibido:

```php
<?php
echo '¡Hola ' . $_REQUEST['nombre'] . ' ' . $_REQUEST['apellido'] . '!';

// Se imprime "¡Hola Roque Molina!".
?>
```
