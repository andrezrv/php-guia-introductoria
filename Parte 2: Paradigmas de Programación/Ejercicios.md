# Ejercicios

**1. Las variables `$_POST`, `$_GET` y `$_REQUEST` son creadas automáticamente cuando PHP recibe datos del usuario.**

1. Verdadero
2. Falso

**2. ¿Cuál es el tipo de dato contenido en `$_POST`?**

1. Boolean
2. Array
3. String

**3. ¿Cuál de estas llamadas a funciones se usa para saber si se envió el dato "nombre" por medio de un formulario con método "post"?**

1. `isset( 'nombre' )`
2. `sent( $_POST['nombre'] )`
3. `isset( $_POST['nombre'] )`

**4. La variable `$_REQUEST` agrupa los contenidos de las variables `$_POST` y `$_GET`.**

1. Verdadero
2. Falso

**5. ¿Al valor de qué atributo de un elemento de formulario HTML es igual la clave de un dato recibido por `$_POST`?**

1. `id`
2. `value`
3. `name`

**6. No es posible imprimir contenido a partir de datos ingresados por un usuario.**

1. Verdadero2. Falso

**7. Las funciones permiten repetir procesos de manera automática.**

1. Verdadero
2. Falso

**8. No es posible crear una función que no ejecute ningún proceso.**

1. Verdadero
2. Falso

**9. ¿Cuál de estas declaraciones de función es incorrecta?**

1. `function saludar() {}`2. `function saludar( $valor ) {}`3. `func saludar {}`

**10. Dada la siguiente función, ¿cuál es su uso correcto para imprimir "Hola Kun Agüero!"?**

```php<?phpfunction saludar( $nombre, $apellido ) { echo 'Hola ' . $nombre . ' ' . $apellido . '!';}?>```

1. `saludar()`
2. `saludar( 'Kun', 'Agüero' )`
3. `saludar 'Kun', 'Agüero'`

**11. No es posible contar con valores predefinidos en una función.**

1. Verdadero
2. Falso

**12. Un parámetro es conceptualmente diferente de una variable, pero en la práctica no presentan diferencias.**

1. Verdadero
2. Falso

**13. Dado el siguiente código, ¿qué texto se imprime en la última línea?**

```php
<?php
$foo = 'bar';

function test() {
    echo $foo;
}

test();
?>
```

1. "bar"
2. "Error"
3. No se imprime nada.

**14. ¿Qué tipo de variable es accesible solo en su contexto de declaración?**

1. Global
2. Local
3. Estática

**15. ¿Qué tipo de variable es accesible en todo contexto?**

1. Global
2. Local
3. Estática
