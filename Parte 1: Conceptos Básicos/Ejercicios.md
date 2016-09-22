# Ejercicios

**1. Todo lo que se escribe por fuera de las etiquetas de apertura y cierre de PHP es texto plano.**

1. Verdadero
2. Falso
3. Depende del contexto

**2. ¿Cuál de estas definiciones corresponde a `if`?**

1. Evalúa una condición y, mientras sea verdadera, repite la ejecución de un mismo bloque de código.
2. Evalúa una condición y, si es verdadera, ejecuta un bloque de código.
3. Ejecuta un mismo bloque de código por cada elemento del conjunto dado.

** 3. ¿Cuál de estas definiciones corresponde a `while`?**

1. Ejecuta un mismo bloque de código por cada elemento del conjunto dado.
2. Evalúa una condición y, si es verdadera, ejecuta un bloque de código.
3. Evalúa una condición y, mientras sea verdadera, repite la ejecución de un mismo bloque de código.

** 4. ¿Cuál de estas definiciones corresponde a `foreach`?**

1. Ejecuta un mismo bloque de código por cada elemento del conjunto dado.
2. Evalúa una condición y, mientras sea verdadera, repite la ejecución de un mismo bloque de código.
3. Evalúa una condición y, si es verdadera, ejecuta un bloque de código.

** 5. PHP puede generar dinámicamente código HTML y de cualquier otro lenguaje de marcado.**

0. Falso.
0. Depende del contexto.
0. Verdadero.
	
**6. ¿Qué es una variable?**

0. Una palabra delimitada por comillas.
0. Un tipo de dato numérico.
0. Una referencia a un dato que puede ser usado múltiples veces.
	
**7. ¿Cuál de estas declaraciones de variables es correcta?**

0. `$a: 1;`
0. ```$b = 1;```
0. ```$c = 1```

**8. ¿Cuál de estas variables *no* está correctamente declarada?**

0. ```$a = 1;```
0. ```$b = 1```
0. ```$c = 'Hola';```

**9. ¿En cuál de estos puntos se mencionan estructuras de control?**

0. `if`, `while`, `for`
0. ```include```, ```require```, ```print```
0. ```define```, ```echo```, ```count```

**10. ¿Cuál de estas afirmaciones es falsa?**

0. Las variables no pueden ser redefinidas.
0. Las constantes no pueden ser redefinidas.
0. Los arrays permiten guardar grupos de datos.

**11. ¿En cuál de estos puntos *no* se imprime código HTML?**

0. `<?php echo '<strong>¡Hola Mundo!</strong>'; ?>`
0. `<?php $a = 1; ?><strong>¡Hola Mundo!</strong>`
0. `<?php <strong>¡Hola Mundo!</strong> ?>`

**12. ¿Cuál de estas definiciones corresponde al tipo de dato ```integer```?**

0. Número entero, sin decimales, desde 0 al infinito, positivo o negativo.
0. Cualquier número en el grupo de los números reales, incluyendo decimales.
0. Una cadena de texto delimitada por comillas.

**13. ¿Cuál de estas definiciones corresponde al tipo de dato ```float```?**

0. Número entero, sin decimales, desde 0 al infinito, positivo o negativo.
0. Cualquier número en el grupo de los números reales, incluyendo decimales.
0. Una cadena de texto delimitada por comillas.

**14. ¿Cuál de estas definiciones corresponde al tipo de dato ```string```?**

0. Número entero, sin decimales, desde 0 al infinito, positivo o negativo.
0. Cualquier número en el grupo de los números reales, incluyendo decimales.
0. Una cadena de texto delimitada por comillas.

**15. ¿Cuáles de estos son operadores aritméticos?**

0. ```+```, ```-```, ```*```, ```/```
0. ```==```, ```===```, ```!=```, ```!==```
0. ```=```, ```+=```, ```.=```

**16. ¿Cuáles de estos son operadores lógicos?**

0. ```||```, ```&&```, ```!```
0. ```>```, ```<```, ```<>```
0. ```/=```, ```%=```

**17. ¿Cuáles de estos no son operadores de comparación?**

0. ```==```, ```===```, ```!=```, ```!==```
0. ```>```, ```<```, ```<=```, ```>==```
0. ```++```, ```--```
	
**18. ¿Cuáles de estos son operadores de asignación?**

0. ```=```, ```+=```, ```.=```
0. ```++```, ```--```
0. ```+```, ```-```, ```*```, ```/```

**19. Si ```$a = 1```, ¿cuál de estas declaraciones no aumenta el valor de ```$a```?**

0. ```$a++;```
0. ```$a += 1;```
0. ```$a = 2;```

**20. ¿Cuál de estas construcciones no carga el contenido de un archivo?**

0. ```require 'archivo.php';```
0. ```include_once 'archivo.php';```
0. ```echo 'archivo.php';```

**21. Si `$a = 1` y `$b = 1`, ¿cuál de estas comparaciones no devuelve true?**

0. ```$a == $b```
0. ```$a === $b```
0. ```$a > $b```

**22. Si ```$a = 1``` y ```$b = 1.0```, ¿cuál de estas comparaciones devuelve ```true```?**

0. ```$a === $b```
0. ```$a == $b```
0. ```$a < $b```

**23. Si `$a = 1` y `$b = '1'`, ¿cuál de estas comparaciones no devuelve false?**

0. ```$a == $b```
0. ```$a === $b```
0. ```$a != $b```

**24. Teniendo en cuenta el siguiente código, ¿en cuál de estos casos se imprime "¡Hola mundo!"?**
```php
<?php
if ( $a === 1 ) {
	echo "¡Hola Mundo!"
}
?>
```

0. Si `$a = '1'`
0. Si `$a = 1`
0. Si `$a = 1.0`

**25. Teniendo en cuenta el siguiente código, ¿cuál va a ser el texto que se imprima?**

```php
<?php
$i = 1;

while ( $i < 5 ) {
  echo $i;
  $i++;
}
?>
```
0. No se imprime texto.
0. Se imprime "1234".
0. Se imprime "12345".

**26. Teniendo en cuenta el siguiente código, ¿cuántas veces va a imprimirse el caracter "@"?**

```php
<?php
$i = 1;

while ( $i ) {
  echo '@';
}
?>
```

0. 10.
0. 5.
0. Infinitas veces.

**27. Teniendo en cuenta el siguiente código, ¿cuál es la solución correcta para prevenir un loop infinito?**

```php
<?php
$i = 1;

while ( $i < 5 ) {
  echo $i;
}
?>
```

0. Modificar la definición de `$i` por `$i = 5`.
0. Aumentar el valor de `$i` antes del cierre del bucle con `$i++`.
0. Modificar la condición del bucle por `$i <= 5`.

**28. Dado `$lista = array( 'Pan', 'Leche', 'Azúcar' )`, ¿cuál de estas lineas imprime correctamente "Pan"?**

0. `echo $lista[0];`
0. `echo $lista[Pan];`
0. `echo $lista['pan'];`

**29. ¿Cuál de estas operaciones carga correctamente el contenido del archivo `funciones.php`?**

0. `include funciones.php;`
0. `load 'funciones.php';`
0. `include 'funciones.php';`

**30. ¿Cuál de estas operaciones carga correctamente el contenido del archivo `funciones.php` solo en el caso de que no se haya cargado previamente?**

0. `include 'funciones.php';`
0. `include_once 'funciones.php';`
0. `load_once 'funciones.php';`

**31. Si `$a = 3` y `$b = $a + 2`, ¿qué número imprime `echo $b * $a`?**

0. 8
0. 15
0. 5

**32. ¿Cuál de estos operadores evalúa si un número es mayor o igual a otro?**

0. ```>```
0. ```<```
0. ```>=```

**33. ¿Cuál de estos operadores no evalúa si un número es menor a otro?**

0. ```>=```
0. ```<```
0. ```<=```

**34. ¿Cuál es el tipo de dato del resultado de ```1 + 1.1```?**

0. Integer
0. Float
0. String

**35. ¿Cuál es el tipo de dato del resultado de ```1 + 2```?**

0. Integer
0. Float
0. String