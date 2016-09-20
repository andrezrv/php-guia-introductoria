# Estructuras de control

Las estructuras de control sirven para evaluar datos y, en base a sus resultados, ejecutar alguna acción determinada en la aplicación. Existen diferentes tipos de estructuras de control.

## Condicionales

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

?>
```

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
?>
```

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
?>
```

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
?>
```

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
?>
```

De esta manera, evaluamos si el valor que se le da a `switch()` como parámetro es igual a alguno de los casos especificados en la estructura. Si es igual, se ejecuta el código contenido en el caso correspondiente. De lo contrario, de ejecuta el código contenido en `default`.

## Bucles

### while

Es una de las estructuras de control del tipo bucle, o *loop*. Esto significa que la estructura se repetirá un número dado de veces (o iteraciones), hasta que se le indique que debe dejar de ejecutarse.

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

Es muy importante cortar el ciclo en alguna de sus iteraciones ya que, de lo contrario, el bucle se ejecutará al infinito, lo cual puede llegar a colgar el equipo debido a un alto consumo de memoria.

### for

Es similar a `while`, aunque un poco menos semántico, lo cual puede hacerlo más difícil de entender.

A diferencia de `while`, `for` está exclusivamente pensado para operar con valores numéricos. Además, recibe una tríada de parámetros separados por `;`. El primer parámetro es el estado inicial del bucle, el segundo es la condición de corte, y el tercero es una operación a realizar al final de cada iteración.

El ejemplo anterior con `while` puede reformularse con `for` de esta manera:

```php
<?php
for ( $i = 0; $i <= 5; $i++ ) {
  echo $i; // Se imprime $i.
}

// Se imprime "012345".
?>
```

### foreach

Se utiliza para iterar sobre arrays. Recibe como parámetro el array que se planea iterar y genera una o dos nuevas variables que permiten acceder al contenido de cada elemento iterado.

```php
<?php
$lista = array( 'Pan', 'Leche', 'Azúcar' );

foreach ( $lista as $item ) {
  echo $item; // Imprime cada elemento de la lista.
}
?>
```

También puede accederse por separado a la clave y valor de cada elemento:

```php
<?php
$lista = array( 'Pan', 'Leche', 'Azúcar' );

foreach ( $lista as $clave => $valor ) {
  echo $clave . ': ' . $valor; // Imprime cada elemento de la lista.
}
?>
```
