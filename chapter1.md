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

## Comentarios

En todos los lenguajes de programación existe alguna manera de dejar comentarios de texto para uso propio o de otros desarrolladores, a manera de documentación interna. Estos comentarios pueden escribirse dentro de los mismos archivos donde se escribe el código, sin tener ningún tipo de impacto en la aplicación.

En PHP pueden escribirse comentarios de dos maneras:

### Comentarios de línea única

Con `//` pueden iniciarse comentarios que solamente se extienden por una línea del código:

```php
<?php
// Imprimo texto:
echo '¡Hola Mundo!';
?>
```

### Comentarios de líneas múltiples

Comentarios más extensos, que puedan llegar a contar con varias líneas, deben iniciarse con `/*` y terminar con `*/`.

```php
<?php
/*
Yo imprimo texto porque me gusta imprimir texto
Yo nací para imprimir texto...
*/
echo '¡Hola Mundo!';
?>
```

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

## Constantes

Son similares a las variables, con la diferencia de que no pueden sobreescribirse. También difieren en que se las declara con la función `define()`, y no hace falta que lleven el símbolo `$`. Generalmente se usan para guardar datos de configuración de una aplicación, y por convención se las declara con mayúsculas.

```php
<?php
define( 'MENSAJE', '¡Hola mundo!' );

echo MENSAJE; // Imprime "¡Hola mundo!".
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

Debido a que el lenguaje no es declarativo acerca del tipo de datos que se asignan a variables (es decir que al momento de crear la variable no se especifica de qué tipo es el dato contenido), PHP reconoce el tipo de cada dato de forma automática, y al mismo tiempo otorga cierta flexibilidad al comparar entre diferentes tipos.

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

### Número de punto flotante

También conocido como *float*, es un dato numérico que puede ser expresado como cualquier tipo de número real, aunque principalmente se lo usa con decimales.

```php
<?php
$a = 1.0;
$b = 1.01;
$c = 100.123;
?>
```

### Cadenas de caracteres

También llamado *string*, es un tipo de dato expresado como una cadena de caracteres en diferentes formatos, aunque los más utilizados son los siguientes:

#### Comillas simples o dobles

El uso de ambos tipos de comillas suele producir resultados similares, aunque existen algunas diferencias considerables entre cada uno.

Por ejemplo, la siguiente pieza de código imprime exactamente el mismo texto para los dos casos:

```php
<?php
echo "¡Hola Mundo!"; // Imprime "¡Hola Mundo!";
echo '¡Hola Mundo!'; // Imprime "¡Hola Mundo!";
?>
```

Sin embargo, en este caso se presentan diferencias:

```php
<?php
$mensaje = '¿Cómo estás?';

echo "¡Hola Mundo! $mensaje"; // Imprime "¡Hola Mundo! ¿Cómo estás?";
echo '¡Hola Mundo! $mensaje'; // Imprime "¡Hola Mundo! $mensaje";
?>
```

Como se ve en el ejemplo, usando comillas dobles, las variables dentro del texto se interpretan como tales; mientras que, usando comillas simples, se interpreta como texto el nombre de la variable.

Para resolver este problema con las comillas simples, puede usarse una concatenación de texto:

```php
<?php
$mensaje = '¿Cómo estás?';

echo "¡Hola Mundo! $mensaje"; // Imprime "¡Hola Mundo! ¿Cómo estás?";
echo '¡Hola Mundo! ' . $mensaje; // Imprime "¡Hola Mundo! ¿Cómo estás?";
?>
```

Por otra parte, una limitacion de las comillas dobles es que no soportan saltos de línea ni tabulaciones.

```php
<?php
$mensaje = "¡Hola Mundo!
  ¿Cómo estás?";

echo $mensaje;
// Imprime:
// ¡Hola Mundo! ¿Cómo estás?

$mensaje = '¡Hola Mundo!
  ¿Cómo estás?';

echo $mensaje;
// Imprime:
// ¡Hola Mundo!
//   ¿Cómo estás?
?>
```

Según el ejemplo, la impresión derivada de la variable declarada con comillas simples respetó el salto de línea y la tabulación, pero la derivada de la variable con comillas dobles fue de una única línea. Para que estos caracteres sean respetados por las comillas dobles, necesitamos reponerlos con las expresiones `\b`, para el salto de línea, y `\t` para la tabulación.

```php
<?php
$mensaje = "¡Hola Mundo!\b
\t¿Cómo estás?";

echo $mensaje;
// Imprime:
// ¡Hola Mundo!
//   ¿Cómo estás?

$mensaje = '¡Hola Mundo!
  ¿Cómo estás?';

echo $mensaje;
// Imprime:
// ¡Hola Mundo!
//   ¿Cómo estás?
?>
```

Una limitación de ambos tipos de comillas es que no pueden contenerse a sí mismos dentro de las cadenas que encierran:

```php
<?php
$mensaje = "<p class="texto">¡Hola Mundo!</p>";
echo $mensaje; // Imprime un error.

$mensaje = '<p class='texto'>¡Hola Mundo!</p>';
echo $mensaje; // Imprime un error.
?>
```

Esto ocurre porque PHP interpreta que la primera comilla que aparece en el texto está cerrando la declaración, y toma el código que está a continuación como inválido, por lo cual da un error. Para evitar este problema existen dos posibles soluciones: intercalar tipos de comillas o realizar un escape de caracteres con `\`.

```php
<?php
$mensaje = "<p class='texto'>¡Hola Mundo!</p>"; // Intercalando tipos de comillas.
echo $mensaje;
// Imprime:
// <p class='texto'>¡Hola Mundo!</p>

$mensaje = "<p class=\"texto\">¡Hola Mundo!</p>"; // Escapando caracteres.
echo $mensaje;
// Imprime:
// <p class="texto">¡Hola Mundo!</p>

$mensaje = '<p class="texto">¡Hola Mundo!</p>'; // Intercalando tipos de comillas.
echo $mensaje;
// Imprime:
// <p class="texto">¡Hola Mundo!</p>

$mensaje = '<p class=\'texto\'>¡Hola Mundo!</p>'; // Escapando caracteres.
echo $mensaje;
// Imprime:
// <p class='texto'>¡Hola Mundo!</p>
?>
```

### Arrays

#### Concatenación

La concatenación es la unión de dos o más cadenas de caracteres. En PHP existen dos maneras de concatenar caracteres.

##### Concatenación simple

Con el caracter `.` (punto) pueden unirse dos cadenas de texto al momento de imprimir o asignar.

```php
<?php
$mensaje = '¡Hola Mundo!';

echo $mensaje . ' ¿Cómo estás?'; // Imprime "¡Hola Mundo! ¿Cómo estás?".
?>
```

##### Concatenación por asignación

También pueden concatenarse textos por medio de una nueva asignación a una variable previamente declarada. Para eso se usa el operador `.=`, el cual añade el nuevo valor al final de la cadena original.

```php
<?php
$mensaje = '¡Hola Mundo!';
$mensaje .= ' ¿Cómo estás?';

echo $mensaje; // Imprime "¡Hola Mundo! ¿Cómo estás?".
?>
```

## Operadores

PHP soporta varias clases de operadores para modificar datos y evaluar condiciones de verdad. Los más utilizados son los operadores de asignación, los aritméticos, los de comparación, los de incremento y decremento, y los lógicos.

### Operadores de asignación

Asignan o modifican el valor de una variable. El operador de asignación básico es `=`, que ya utilizamos tanto para inicializar como para sobreescribir una variable.

```php
<?php
$mensaje = '¡Hola mundo!';  // Asigna "¡Hola Mundo!" a $mensaje.
$mensaje = 'Chau mundo :('; // Sobreescribe $mensaje con "Chau mundo :(".
?>
```

También vimos el operador `.=`, el cual adjunta una cadena de caracteres al final de otra.

```php
<?php
$mensaje = '¡Hola mundo!';  // Asigna "¡Hola Mundo!" a $mensaje.
$mensaje .= ' ¿Cómo estás?'; // Adjunta " ¿Cómo estás?" a $mensaje.

echo $mensaje; // Imprime "¡Hola mundo! ¿Cómo estás?".
?>
```

Los operadores de asignación también pueden combinarse con operadores aritméticos. Por ejemplo, existe el operador `+=`, utilizado para sumar un valor numérico a otro. Estos operadores combinados trabajan casi indistintamente sobre números enteros y de punto flotante, por lo cual se pueden combinar ambos tipos, y convertirlos de uno a otro.

```php
<?php
$a = 3;  // $a vale 3.
$a += 2; // $a vale 5.

$b = 1; // $b vale 1.
$b += 0.5; // $b vale 1.5, y se convierte su tipo a flotante.
?>
```

Otros operadores combinados son `-=`, `*=`, `/=` y `%=`.

```php
<?php
$a = 3;  // $a vale 3.
$a -= 2; // $a vale 1.

$b = 1; // $b vale 1.
$b *= 3; // $b vale 3.

$c = 4; // $c vale 4.
$c *= 2; // $c vale 8;

$d = 9; // $d vale 9;
$d /= 3; // $d vale 3;

$e = 10; // $e vale 10.
$e %= 5; // $e vale 0;
?>
```

### Operadores aritméticos

Son los operadores básicos de suma (`+`), resta (`-`), multiplicación (`*`), división (`/`), resto (`%`) y exponente (`**`). En la mayoría de los casos trabajan indistintamente sobre números enteros y flotantes.

```php
<?php
$a = 3 + 2;   // $a vale 5.
$b = 3 - 1.5; // $b vale 1.5.
$c = 2 * 3.5; // $c vale 7.
$d = 9 / 3;   // $d vale 3;
$e = 10 % 5;  // $e vale 0.
$f = 3 ** 2;  // $f vale 9.
?>
```

### Operadores de comparación

Sirven para comparar dos valores y tienen como resultado un valor de verdad: `true` o `false`.

| Operador | Nombre | Uso | Resultado |
| -- | -- | -- | -- |
| == | Igual | $a == $b | `true` si `$a` y `$b` son iguales o equivalentes, aunque sean de diferentes tipos. |
| === | Idéntico | $a === $b | `true` si `$a` y `$b` son iguales y del mismo tipo. |
| != | No igual | $a != $b | `true` si `$a` y `$b` no son iguales o equivalentes, aunque sean de diferentes tipos. |
| <> | No igual | $a <> $b | `true` si `$a` y `$b` no son iguales o equivalentes, aunque sean de diferentes tipos. |
| !== | No idéntico | $a !== $b | `true` si `$a` y `$b` no son iguales ni del mismo tipo. |
| < | Menor | $a < $b | `true` si $a es un entero o flotante menor a $b |
| > | Mayor | $a > $b | `true` si $a es un entero o flotante mayor a $b |
| <= | Menor o igual | $a <= $b | `true` si $a es un entero o flotante menor, igual o equivalente a $b |
| >= | Mayor o igual | $a >= $b | `true` si $a es un entero o flotante mayor, igual o equivalente a $b |

**Ejemplos:**

```php
<?php
// Igualdad:
$a1 = 1 == 1;   // $a1 es true.
$a2 = 1 == 1.0; // $a2 es true.
$a3 = 1 == '1'; // $a3 es true.
$a4 = 1 == 2;   // $a4 es false.

// Identidad
$b1 = 1 === 1;   // $b1 es true.
$b2 = 1 === 1.0; // $b2 es false.
$b3 = 1 === '1'; // $b3 es false.
$b4 = 1 === 2;   // $b4 es false.

// No-igualdad:
$c1 = 1 != 1;   // $c1 es false.
$c2 = 1 != 1.0; // $c2 es false.
$c3 = 1 != '1'; // $c3 es false.
$c4 = 1 != 2;   // $c4 es true.

// No-identidad
$d1 = 1 !== 1;   // $d1 es false.
$d2 = 1 !== 1.0; // $d2 es true.
$d3 = 1 !== '1'; // $d3 es true.
$d4 = 1 !== 2;   // $d4 es true.

// Menor
$e1 = 1 < 2;   // $e1 es true.
$e2 = 1 < 1;   // $e2 es false.
$e3 = 1 < 0.5; // $e3 es false.

// Mayor
$f1 = 1 > 2;   // $f1 es false.
$f2 = 1 > 1;   // $f2 es false.
$f3 = 1 > 0.5; // $f3 es true.

// Menor o igual
$g1 = 1 <= 2;   // $g1 es true.
$g2 = 1 <= 1;   // $g2 es true.
$g3 = 1 <= 0.5; // $g3 es false.

// Mayor o igual
$h1 = 1 >= 2;   // $h1 es false.
$h2 = 1 >= 1;   // $h2 es true.
$h3 = 1 >= 0.5; // $h3 es true.
?>
```

### Operadores de incremento y decremento

Sirven para aumentar o disminuir un valor numérico en una unidad sin realizar una nueva asignación.

| Operador | Uso | Nombre | Efecto |
| -- | -- | -- | -- |
| ++ | ++$a | Pre-incremento | Suma 1 a $a y lo devuelve. |
| ++ | $a++ | Post-incremento | Devuelve $a y le suma 1. |
| -- | --$a | Pre-decremento | Resta 1 a $a y lo devuelve. |
| -- | $a-- | Post-decremento | Devuelve $a y le resta 1. |

**Ejemplos:**

```php
<?php
// Pre-incremento
$a = 5;
echo ++$a; // Imprime 6.
echo $a;   // Imprime 6.

// Post-incremento
$b = 5;
echo $b++; // Imprime 5.
echo $b;   // Imprime 6.

// Pre-decremento
$c = 5;
echo --$c; // Imprime 4.
echo $c;   // Imprime 4.

// Post-decremento
$d = 5;
echo $d--; // Imprime 5.
echo $d;   // Imprime 4.
?>```

## Estructuras de control

Las estructuras de control sirven para evaluar datos y, en base a sus resultados, ejecutar alguna acción determinada en la aplicación. Existen diferentes tipos de estructuras de control.

### if / elseif / else

La estructura `if()` es la más simple de las estructuras de control, y solamente evalúa si un resultado es verdadero o falso. En caso de que la evaluación sea verdadera, ejecuta el código contenido dentro de la estructura.

```php
<?php
$a = true;
$mensaje = '¡Hola Mundo!';

// Se evalúa si $a es igual a true.
if ( $a == true ) {
  // Si la evaluación es verdadera, se imprime el mensaje.
  echo $mensaje;
}

?>```

Un detalle importante a notar es que los valores booleanos pueden evaluarse sin necesidad de usar operadores de comparación. Teniendo eso en cuenta, el siguiente código es equivalente al anterior:

```php
<?php
$a = true;
$mensaje = '¡Hola Mundo!';

// Se evalúa si $a es igual a true.
if ( $a ) {
  // Si la evaluación es verdadera, se imprime el mensaje.
  echo $mensaje;
}
?>```

En caso de que se necesiten evaluaciones adicionales para ejecutar procesos alternativos, puede introducirse `elseif()` a la estructura de control.

```php
<?php
$a = false;
$b = true;

$mensaje_a = '¡Hola Mundo!';
$mensaje_b = ':(';

if ( $a ) {
  echo $mensaje;
} elseif( $b ) {
  echo $b;
}
?>```

Si se quiere ejecutar un proceso por defecto en caso de que no cumpla ninguna condición de la estructura, puede introducirse `else`.

```php
<?php
$a = false;
$b = false;

$mensaje_a = '¡Hola Mundo!';
$mensaje_b = ':(';

if ( $a ) {
  echo $mensaje;
} elseif( $b ) {
  echo $b;
} else {
  echo ':\'('; // Imprime ":'(".
}
?>```

### switch

Para evitar largas estructuras de `if/elseif/else`, puede usarse la estructura `switch`.

```php
<?php
$a = 'Hola';

switch ( $a ) {
  case 'Hola':
    echo '¡Hola Mundo!';
    break;
  case 'Chau':
    echo 'Chau Mundo :(';
    break;
  default:
    echo ':(';
}
?>```

De esta manera, evaluamos si el valor que se le da a `switch()` como parámetro es igual a alguno de los casos especificados en la estructura. Si es igual, se ejecuta el código contenido en el caso correspondiente. De lo contrario, de ejecuta el código contenido en `default`.

### while

Es una de las estructuras de control del tipo bucle, o *loop*. Esto significa que la estructura se repetirá un número dado de veces, hasta que se le indique que debe dejar de ejecutarse.

**Ejemplo:**

```php
<?php
$i = 0; // Se inicializa un contador.

// Mientras $i sea menor o igual a 5...
while ( $i <= 5 ) {
  echo $i; // Se imprime $i.
  $i++;    // Se suma 1 a $i.
}

// Se imprime "012345".
?>
```

Es muy importante cortar el ciclo en algún punto ya que, de lo contrario, el bucle se ejecutará al infinito, lo cual puede llegar a colgar el equipo debido a un alto consumo de memoria.

### for

### foreach

## Inclusiones
