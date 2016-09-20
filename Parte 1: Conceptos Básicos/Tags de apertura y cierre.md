# Tags de apertura y cierre
PHP es un lenguaje de programación orientado a imprimir y procesar texto. Por esto mismo, todo aquello que escribimos de manera directa en un archivo con extensión `.php` puede ser interpretado como texto plano, HTML o XML, dependiendo del formato de marcado con el que lo escribamos. De esta manera, un archivo PHP en el cual solamente tengamos un contenido como el siguiente se va a ver igual que si el archivo tuviera la extensión `.html`:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Mi sitio web</title>
  </head>
  <body>
    <p>Hola Mundo!</p>
  </body>
</html>
```

Sin embargo, con la introducción en este archivo de las etiquetas de apertura y cierre de PHP, `<?php` y `?>` respectivamente, todo lo que escribamos entre esas etiquetas pasa a interpretarse como código PHP:

```php
<!DOCTYPE html>
<html>
  <head>
    <title>Mi sitio web</title>
  </head>
  <body>
    <p>Lista de compras:</p>
    <ul>
      <?php
        $productos = array( 'Pan', 'Azúcar', 'Harina', 'Vino' );

        foreach( $productos as $producto ) {
          echo '<li>' . $producto . '</li>';
        }
      ?>
    </ul>
  </body>
</html>
```

No importa si en este punto el código todavía es incomprensible, pero sí puede notarse, en base al ejemplo, cómo el HTML correspondiente a la lista de compras se genera dinámicamente por medio de PHP.