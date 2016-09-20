# Carga de archivos

PHP nos permite separar nuestro código en diferentes archivos para poder mantenerlo de forma más ordenada. Para esto contamos con las construcciones `require`, `require_once`, `include` e `include_once`.

Por ejemplo, si estamos trabajando en un archivo llamado `contacto.php`, y queremos reutilizar el código contenido en `encabezado.php`, debemos usar una de las cuatro construcciones para incluir el archivo:

```php
# contacto.php
<?php
require 'encabezado.php';
require_once 'encabezado.php';
include 'encabezado.php';
include_once 'encabezado.php';
?>
```

Una diferencia entre estas construcciones es que aquellas con el sufijo `_once` solamente incluyen el archivo si no fue incluido previamente en alguna parte de la aplicación, lo cual evita la replicación de código. Sin embargo, a veces es deseable que el código se replique, y en estos casos se debe preferir usar `include` o `require`.

Otra diferencia es que `require` y `require_once` hacen una inclusión estricta, es decir que PHP va a arrojar un error fatal y cortar la ejecución de la aplicación en caso de que el archivo no se encuentre. En el caso de `include` e `include_once` no hay error fatal ni se detiene la ejecución, pero sí se imprime una advertencia.