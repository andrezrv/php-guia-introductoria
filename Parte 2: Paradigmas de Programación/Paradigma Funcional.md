# Paradigma funcional

El paradigma de programación funcional propone que todo programa o aplicación debe consistir únicamente en definiciones de funciones que se utilizan mutuamente para obtener valores o ejecutar procesos. En sus implementaciones más puras no existen las variables, y las funciones consisten en procedimientos similares a operaciones matemáticas. Prácticamente no es utilizado en su forma más estricta en desarrollo web, pero muchos lenguajes de programación que no son estrictamente funcionales, como JavaScript, Python y PHP, incorporan ciertos conceptos de la programación funcional para facilitar el trabajo del programador.

## Funciones

Las funciones son bloques de código reutilizable, que se definen una única vez y pueden ejecutarse múltiples veces, produciendo siempre un resultado similar. Pueden recibir una serie de parámetros, cuyo valor puede modificar el resultado de una función.

En PHP, las funciones se declaran usando la palabra `function` seguida del nombre que vamos a asignar a nuestra función. El nombre puede escribirse de la misma forma que las variables, pero sin el caracter `$`. A continuación del nombre se usan paréntesis, entre los cuales se colocan los nombres de los parámetros que puede recibir la función.

```php
<?php
function imprimir_lista( $lista ) {
  // Condición
  if ( is_array( $lista ) && ! empty( $lista ) ) {
    // Bucle
    foreach ( $lista as $item ) {
      // Secuencia (ejecución)
      echo $item . "\n" ; // Imprime cada elemento de la lista.
    }
  }
}
?>
```

Al programar utilizando funciones podemos seguir utilizando secuencias, condiciones y bucles. Podemos entender, entonces, que la programación funcional en PHP presupone el uso de la programación estructurada.

Para ejecutar el código contenido en una función, simplemente escribimos su nombre y, entre paréntesis, los valores de los parámetros que queremos enviarle.

```php
<?php
function imprimir_lista( $lista ) {
  if ( is_array( $lista ) && ! empty( $lista ) ) {
    foreach ( $lista as $item ) {
      echo $item . "\n" ; // Imprime cada elemento de la lista.
    }
  }
}

// Se define una variable:
$lista = array( 'Pan', 'Leche', 'Azúcar' );

// Se ejecuta la función:
imprimir_lista( $lista );

// Se imprime:
// Pan
// Leche
// Azúcar
?>
```

Una función también puede recibir más de un parámetro:

```php
<?php
function imprimir_lista( $lista, $titulo ) {
  if ( is_array( $lista ) && ! empty( $lista ) ) {
    echo $titulo . "\n";

    foreach ( $lista as $item ) {
      echo $item . "\n" ; // Imprime cada elemento de la lista.
    }
  }
}

// Se ejecuta la función:
imprimir_lista( array( 'Pan', 'Leche', 'Azúcar' ), 'Lista de compras' );

// Se imprime:
// Lista de compras
// Pan
// Leche
// Azúcar
?>
```

Es importante notar que el llamado a la función debe hacerse una vez que la función ya haya sido declarada. De lo contrario, PHP imprime un error fatal con el mensaje "Call to undefined function".

Una función también puede ser usada para obtener datos. El siguiente ejemplo devuelve una cadena de texto a partir del contenido de un array:

```php
<?php
function lista_en_texto( $lista ) {
  $texto = '';

  if ( is_array( $lista ) && ! empty( $lista ) ) {
    foreach ( $lista as $item ) {
      $texto .= $item . "\n" ;
    }
  }

  return $texto;
}

// Se ejecuta la función:
$lista = lista_en_texto( array( 'Pan', 'Leche', 'Azúcar' ) );

// Valor de $lista:
// Pan
// Leche
// Azúcar
?>
```

La construcción `return` arroja un resultado que puede ser asignado a una variable o constante. Es importante notar que, una vez ejecutada, cierra la ejecución de la función que la contiene.

```php
<?php
function lista_en_texto( $lista ) {
  $texto = '';

  if ( is_array( $lista ) && ! empty( $lista ) ) {
    foreach ( $lista as $item ) {
      $texto .= $item . "\n" ;
    }
  }

  return $texto;

  echo $texto; // No se ejecuta, porque se usó "return" más arriba.
}
?>
```

## Redeclaración de funciones

Al contrario de las variables, las funciones no pueden ser redefinidas. Es decir que, si intentáramos escribir una nueva función con el mismo nombre de una ya existente, PHP arrojaría un error fatal.

```php
<?php
function mi_funcion() {
  echo 'Hello World!';
}

function mi_funcion() {
  echo 'Hola Mundo!';
}

// Error fatal.
?>
```

Sin embargo, existe la posibilidad de que el nombre de una función pueda ser reutilizado, reemplazando a la función original. Para eso, la función original debe haber sido declarada dentro de un bloque condicional que chequea si ya existe.

```php
<?php
// Si no existe una función con el nombre "mi_funcion", se la declara.
if ( ! function_exists( 'mi_funcion' ) ) {
  function mi_funcion() {
    echo 'Hello World!';
  }
}
?>
```

De esta manera, si antes del condicional se declara otra función con el mismo nombre, aquella que se encuentra dentro del condicional no va a ser declarada.

```php
<?php
function mi_funcion() {
  echo 'Hola Mundo!';
}

// Si no existe una función con el nombre "mi_funcion", se la declara.
if ( ! function_exists( 'mi_funcion' ) ) {
  function mi_funcion() {
    echo 'Hello World!';
  }
}

mi_funcion(); // Imprime "Hola Mundo!".
?>
```