# Tipos de datos

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

Un array es lo que se entiende en programación como un mapa ordenado de datos. Básicamente, permite agrupar diferentes datos de manera ordenada con una combinación de clave y valor.

**Ejemplo:**

```php
<?php
$lista = array( 0 => 'Pan', 1 => 'Leche', 2 => 'Azúcar' );

echo $lista[0]; // Imprime "Pan".
echo $lista[1]; // Imprime "Leche".
echo $lista[2]; // Imprime "Azúcar".
?>
```

También es posible no especificar la clave de cada elemento. En esos casos, PHP asigna una clave numérica al elemento de forma automática.

```php
<?php
$lista = array( 'Pan', 'Leche', 'Azúcar' );

echo $lista[0]; // Imprime "Pan".
echo $lista[1]; // Imprime "Leche".
echo $lista[2]; // Imprime "Azúcar".
?>
```

Las claves pueden especificarse también como cadenas de texto, y luego accederse como tales:

```php
<?php
$lista = array( 'cero' => 'Pan', 'uno' => 'Leche', 'dos' => 'Azúcar' );

echo $lista['cero']; // Imprime "Pan".
echo $lista['uno'];  // Imprime "Leche".
echo $lista['dos'];  // Imprime "Azúcar".
?>
```

Incluso aunque las claves se especifiquen como texto, también siguen siendo accesibles según su posición:

```php
<?php
$lista = array( 'cero' => 'Pan', 'uno' => 'Leche', 'dos' => 'Azúcar' );

echo $lista[0]; // Imprime "Pan".
echo $lista[1]; // Imprime "Leche".
echo $lista[2]; // Imprime "Azúcar".
?>
```
