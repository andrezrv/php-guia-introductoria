# Constantes

Son similares a las variables, con la diferencia de que no pueden sobreescribirse. También difieren en que se las declara con la función `define()`, y no hace falta que lleven el símbolo `$`. Generalmente se usan para guardar datos de configuración de una aplicación, y por convención se las declara con mayúsculas.

```php
<?php
define( 'MENSAJE', '¡Hola mundo!' );

echo MENSAJE; // Imprime "¡Hola mundo!".
?>
```