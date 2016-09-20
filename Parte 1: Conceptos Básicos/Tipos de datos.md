# Impresión de texto

Para imprimir texto en PHP usamos comúnmente la construcción `echo`. Es un comando que acepta uno o más argumentos y los imprime en pantalla como texto plano o HTML.

De esta manera, podemos imprimir el valor de una variable:

```php
<?php
$mensaje = '¡Hola mundo!';

echo $mensaje;
?>
```

O un valor de forma directa:

```php
<?php
echo '¡Hola mundo!';
?>
```

O valores múltiples, separándolos con comas:

```php
<?php
$mensaje1 = '¡Hola mundo!';
$mensaje2 = '¿Cómo estás!';

echo $mensaje1, $mensaje2;
?>
```

Otra construcción que sirve para imprimir texto es `print`, pero a diferencia de `echo`, solamente acepta un único parámetro.

Por ejemplo, este es un uso válido de `print`:

```php
<?php
$mensaje = '¡Hola mundo!';

print $mensaje;
?>
```

Y el siguiente es un uso inválido:

```php
<?php
$mensaje1 = '¡Hola mundo!';
$mensaje2 = '¿Cómo estás!';

print $mensaje1, $mensaje2;
?>
```
