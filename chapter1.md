## Tags de apertura y cierre
PHP es un lenguaje de programación orientado a imprimir y procesar texto. Por esto mismo, todo aquello que escribimos de manera directa en un archivo con extensión `.php` puede ser interpretado como texto plano, HTML o XML, dependiendo del formato de marcado con el que lo escribamos. De esta manera, un archivo PHP en el cual solamente tengamos un contenido como el siguiente se va a ver igual que si el archivo tuviera la extensión `.html`:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Mi sitio web</title>
  </head>
  <body>
    <p>Hola Mundo!</p>
  </body>
</html>
```

Sin embargo, con la introducción en este archivo de las etiquetas de apertura y cierre de PHP, `<?php` y `?>` respectivamente, todo lo que escribamos entre esas etiquetas pasa a interpretarse como código PHP:

```php
<!DOCTYPE html>
<html>
  <head>
    <title>Mi sitio web</title>
  </head>
  <body>
    <p>Lista de compras:</p>
    <ul>
      <?php
        $productos = array( 'Pan', 'Azúcar', 'Harina', 'Vino' );

        foreach( $productos as $producto ) {
          echo '<li>' . $producto . '</li>';
        }
      ?>
    </ul>
  </body>
</html>
```

No importa si en este punto el código todavía es incomprensible, pero sí puede notarse, en base al ejemplo, cómo el HTML correspondiente a la lista de compras se genera dinámicamente por medio de PHP.

## Variables
Las variables son elementos de un lenguaje de programación que permiten guardar ciertos datos de una aplicación para luego poder reutilizarlos.

En PHP, las variables se nombran con el signo `$` y un nombre alfanumérico (letras de la A a la Z, sin caracteres especiales ni acentos, y números del 0 al 9). Permiten, además, el caracter `_` (guión bajo, o *underscore*).

Para asignarles un valor se usa el caracter `=`, y a continuación se declara dicho valor. La declaración termina con `;`.

```php
<?php
$mensaje = '¡Hola mundo!';
?>
```

Las variables llevan ese nombre debido a que el valor que se les asigna puede cambiar de un momento a otro, es decir que las variables pueden sobreescribirse.

Ejemplo:

```
<?php
$mensaje = '¡Hola mundo!'; // Se declara el valor de la variable.

echo $mensaje; // Se imprime en pantalla "¡Hola mundo!"

$mensaje = '¿Cómo estás?'; // Se redeclara el valor de la variable.

echo $mensaje; // Se imprime en pantalla "¿Cómo estás?"
?>
```

## Impresión de texto
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

## Tipos de datos

PHP soporta distintos tipos de datos, los cuales pueden cumplir con diferentes propósitos dentro de una aplicación.

### Booleano

El booleano (también *boolean* o *bool*) es el más simple de todos los tipos de datos, y representa un valor de verdad, el cual puede ser `true` (verdadero) o `false` (falso). Normalmente se lo utiliza para evaluar condiciones.

En el siguiente ejemplo se asigna un valor verdadero a la variable `$foo`, y un valor falso a la variable `$bar`:

```php
<?php
$foo = true;
$bar = false;
?>
```

### Entero

Los números enteros son conocidos como `integer` o `int`, y corresponden a todo número sin decimales igual, mayor o menor a cero. También se interpretan como enteros (aunque son poco utilizados) aquellos expresados en los sistemas octal, hexadecimal y binario.

Ejemplos de números enteros válidos:

```php
<?php
$a = 1234; // Número decimal.
$a = -123; // Número negativo.
$a = 0123; // Número octal (equivalente a 83 decimal).
$a = 0x1A; // Número hexadecimal (equivalente a 26 decimal).
$a = 0b11111111; // Número binario (equivalente a 255 decimal).
?>
```

