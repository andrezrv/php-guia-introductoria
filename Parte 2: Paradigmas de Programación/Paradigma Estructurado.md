# Paradigma estructurado

El paradigma de programación estructurada trabaja sobre la idea de que todo programa o aplicación puede escribirse usando tres tipos de instrucciones:

* Secuencias (bloques de declaraciones y ejecuciones)
* Condiciones (`if`, `switch`)
* Bucles (`while`, `for`, `foreach`)

En PHP, un ejemplo simple de programación estructurada sería el siguiente:

```php
<?php
// Secuencia (declaración)
$lista = array( 'Pan', 'Leche', 'Azúcar' );

// Condición
if ( is_array( $lista ) && ! empty( $lista ) ) {
    // Bucle
    foreach ( $lista as $item ) {
        // Secuencia (ejecución)
        echo $item; // Imprime cada elemento de la lista.
    }
}
?>
```

Este paradigma es el que se usa principalmente en PHP y, aunque puede ser combinado con otros, tales como el funcional, el orientado a objetos y el orientado a eventos, estos se usan en combinación con el estructurado.

Una característica del paradigma estructurado es que su tiempo de ejecución es secuencial, inmediato y continuo. Esto significa que cada bloque de código se va a ejecutar en el mismo orden en el que fue ubicado por el programador. Este puede no ocurrir al trabajar con otros paradigmas.
