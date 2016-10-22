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

## Valores por defecto

Para los casos en los que algún parámetro no sea obligatorio al momento de llamar a una función, PHP permite asignar valores por defecto en la declaración de la función misma.

```php
<?php
function saludar( $nombre = 'Armando', $apellido = 'Pérez' ) {
    echo 'Hola ' . $nombre . ' ' . $apellido . '!';
}

saludar(); // Imprime "Hola Armando Pérez!".
?>
```

## Tipos de variables

### Parámetros

Los parámetros son los valores asignados a una función al momento de utilizarla. En un sentido conceptual no son variables, ya que no se los declara de manera directa en la función, sino que al ejecutarse la función ya fueron previamente asignados a la misma.

```php
<?php
function mi_funcion( $text /* <-- Valor preasignado en llamada. */ ) {
  echo $text;
}

mi_funcion( 'bar' ); // Imprime "bar".
?>
```

Sin embargo, técnicamente funcionan de la misma manera que las variables normales, ya que se los puede modificar en el código interno a la función.

```php
<?php
function mi_funcion( $text /* <-- Valor preasignado en llamada. */ ) {
  $text .= 'ista'; // Se altera el valor del parámetro.

  echo $text;
}

mi_funcion( 'bar' ); // Imprime "barista".
?>
```

### Globales y locales

Una particularidad de las funciones en PHP es que introducen un contexto o ámbito (_scope_, en inglés) separado de aquel en el cual se ejecuta el código escrito por fuera de ellas. Llamamos a estos contextos **locales**, en oposición al contexto **global**.

```php
<?php
// Contexto local 1.

function mi_funcion() {
  // Contexto local 2.
}

// Contexto local 1.
mi_funcion();
?>
```

Esta diferenciación de contextos impide que los valores declarados en uno de ellos sea directamente accesible al otro. Por ejemplo, una variable declarada en un contexto no puede ser usada de manera directa en otro.

```php
<?php
// Contexto local 1.
$foo = 'bar';

function mi_funcion() {
  // Contexto local 2.
  $num = 1;

  echo $foo;
}

echo $num; // No imprime nada.

// Contexto local 1.
mi_funcion(); // No imprime nada.
?>
```

Una manera de intercambiar información entre diferentes contextos es usar parámetros en nuestras funciones:

```php
<?php
// Contexto local 1.
$foo = 'bar';

function mi_funcion( $text ) {
 // Contexto local 2.
 echo $text;
}

// Contexto local 1.
mi_funcion( $foo ); // Imprime "bar".
?>
```

En este ejemplo, la variable `$foo` se asigna como valor del parámetro `$text` de `mi_funcion()`, lo cual permite reutilizar el valor creado en un contexto diferente.

Por otra parte, también es posible utilizar valores globales por medio de la palabra clave `global`. Esta palabra clave permite que ciertas variables sean accesibles desde cualquier lugar de una aplicación, sin importar el contexto de ejecución actual.

```php
<?php
// Contexto local 1.
global $foo; // Se inicializa una variable global.

$foo = 'bar'; // Se asigna un valor.

function mi_funcion() {
  // Contexto local 2.
  global $foo; // Se inicializa una variable global.

  echo $foo; // Se usa la variable global.
}

// Contexto local 1.
mi_funcion(); // Imprime "bar".
?>
```

De esta manera, si la variable global tiene un valor asignado desde un momento previo a su utilización, podrá accederse a dicho valor sin importar dónde se lo usa.

### Estáticas

Las variables estáticas son un tipo especial de variable que "recuerda" el último valor que se les asignó. Se utilizan con la palabra clave `static`.

```php
<?php
function sum1() {
    static $value = 0; // Se declara una variable estática.

    $value++; // Se altera la variable.

    echo $value; // Se imprime el valor actual.
}

sum1(); // Imprime 1.
sum1(); // Imprime 2. Se ignora "static $value = 0;".
sum1(); // Imprime 3. Se ignora "static $value = 0;".
?>
```

La principal particularidad de estas variables es que solamente se inicializan una vez. Es decir que, a partir de la segunda vez que se llama a una función que usa una variable estática, la declaración inicial de la variable es ignorada por el programa. En cambio, se retiene el último valor asignado, el cual está disponible para ser reutilizado.