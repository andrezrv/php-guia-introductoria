# Operadores

PHP soporta varias clases de operadores para modificar datos y evaluar condiciones de verdad. Los más utilizados son los operadores de asignación, los aritméticos, los de comparación, los de incremento y decremento, y los lógicos.

## Operadores de asignación

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

## Operadores aritméticos

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

## Operadores de comparación

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

## Operadores de incremento y decremento

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
?>
```

## Operadores lógicos

Sirven para asignar valores de verdad a evaluaciones sobre diferentes datos.

| Operador | Nombre | Ejemplo | Descripción |
| -- | -- | -- | -- |
| `&&` | Conjunción ("y") | `$a && $b` | `true` si `$a` y `$b` son `true` |
| `and` | Conjunción ("y", sintaxis alternativa) | `$a or $b` | `true` si `$a` y `$b` son `true`  |
| <code>&#124;&#124;</code> | Disyunción ("o") | <code>$a &#124;&#124; $b</code> | `true` si `$a` es `true` o `$b` es `true` |
| `or` | Disyunción ("o", sintaxis alternativa) | `$a or $b` | `true` si `$a` es `true` o `$b` es `true`  |
| `xor` | Disyunción exclusiva ("o ... o ...") | `$a xor $b` | `true` si `$a` es `true` o `$b` es `true`, pero no ambos |
| `!` | Negación ("no") | `! $a` (o `$a != true`) | `true` si `$a` no es `$true` |
