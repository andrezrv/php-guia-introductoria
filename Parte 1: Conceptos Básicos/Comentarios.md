## Comentarios

En todos los lenguajes de programación existe alguna manera de dejar comentarios de texto para uso propio o de otros desarrolladores, a manera de documentación interna. Estos comentarios pueden escribirse dentro de los mismos archivos donde se escribe el código, sin tener ningún tipo de impacto en la aplicación.

En PHP pueden escribirse comentarios de dos maneras:

### Comentarios de línea única

Con `//` y `#` pueden iniciarse comentarios que solamente se extienden por una línea del código:

```php
<?php
// Imprimo texto:
echo '¡Hola Mundo!';
# Se imprime "¡Hola Mundo!"
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