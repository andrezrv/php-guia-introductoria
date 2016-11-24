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

```php
<?php
function saludar( $nombre, $apellido ) {
  echo 'Hola ' . $nombre . ' ' . $apellido . '!';
}
?>
```

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

**16. Es posible enviar un objeto a PHP por medio del método “post”.**

1. Verdadero
2. Falso

**17. El tipo de dato de un objeto depende de la clase con la que se lo crea.**

1. Verdadero
2. Falso

**18. ¿Qué nombre de variable se usa para referirse a la instancia actual de una clase?**

1. `$object`
2. `$instance`
3. `$this`

**19. ¿Cuál de estas líneas crea correctamente un objeto con la clase `Futbolista`?**

1. `$jugador = create Futbolista;`
2. `$jugador = new Futbolista;`
3. `$jugador = Futbolista();`

**20. ¿Cuál de estas palabras clave permite chequear si un objeto pertenece a una clase determinada?**

1. `instanceof`
2. `istype`
3. `hasclass`

**21. ¿Cuál de estas definiciones acerca de un objeto es correcta?**

1. Es un conjunto de datos ordenados.
2. Es una entidad con atributos y comportamiento.
3. Es un grupo de funciones sin relación entre sí.

**22. Los métodos no permiten modificar el estado actual de un objeto.**

1. Verdadero
2. False

**23. Si el valor predeterminado para la propiedad `$energia` de un objeto del tipo `Futbolista` es 100, y el método `function correr( $metros ) {}` descuenta 1 unidad de energía por cada 100 metros recorridos, ¿cuál será el valor de `$futbolista->energia` luego de ejecutar `$futbolista->correr( 300 )`?**

1. 100
2. 97
3. 0

**24. ¿Qué tipo de dato contiene la variable `$_SESSION`?**

1. Array
2. Objeto
3. String

**25. Para operar con sesiones, es indispensable utilizar la función `session_start()`.**

1. Verdadero
2. Falso

**26. ¿En qué se diferencia un valor de sesión de una variable estática?**

1. Un valor de sesión se almacena a través de varias ejecuciones, mientras que el valor de una variable estática se almacena a través de una misma ejecución.
2. El valor de una variable estática se almacena a través de varias ejecuciones, mientras que un valor de sesión se almacena a través de una misma ejecución.
3. No hay diferencia.

**27. Es posible guardar objetos dentro de sesiones.**

1. Verdadero
2. Falso