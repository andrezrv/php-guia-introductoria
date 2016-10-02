# CSS

CSS (por "Cascading Style Sheets", u "hojas de estilo en cascada") es un lenguaje creado y utilizado para describir la presentación o el diseño visual de un documento escrito usando un lenguaje de marcado, tal como HTML o XML. Fue creado en 1997 por Håkon Wium Lie  y Bert Bos, mientras trabajaban junto a Tim Berners-Lee (el creador de HTML) en el W3C.

## Enlace

La manera más recomendada de trabajar con CSS consiste en crear un archivo separado con extensión `.css` (por ejemplo, `style.css`), y enlazarlo desde un archivo HTML usando la etiqueta `link`, dentro de `head`.

```php
<!DOCTYPE html>
<html>
 <head>
    <link rel="stylesheet" href="style.css">
    <meta charset="utf-8">
    <title></title>
 </head>
 <body>
     ...    
 </body>
</html>
```

De esta manera, todos los estilos declarados dentro de `style.css`  se aplican al documento HTML desde el cual se lo enlaza.

## Sintaxis

CSS permite aplicar un determinado diseño a un documento por medio de bloques como el siguiente:

```css
selector {
    atributo: valor;
    otro-atributo: valor;
}
```

El selector es el identificador de un elemento o grupo de elementos HTML. Los atributos, con sus respectivos valores, definen qué estilos se le aplicarán a los elementos seleccionados.

Por ejemplo, para aplicarle un texto de color rojo a todos los elementos con la etiqueta `<p>`, debería usarse el siguiente bloque:

```css
p {
 color: red;
}
```

También pueden identificarse elementos HTML por sus IDs, con el caracter `#`, y clases, usando `.`.

Por ejemplo, suponiendo el siguiente código HTML:

```php
<div class="post">
    Lorem ipsum dolor sit amet.
</div>
```

Podríamos aplicarle estilos al elemento con clase `post` de la siguiente manera:

```css
.post {
 color: red;
}
```

Podemos operar de manera similar con IDs.

HTML:

```php
<header id="site-header">
    Lorem ipsum dolor sit amet.
</header>
```

CSS:


```css
#site-header {
 color: red;
}
```

## Más información

En el [curso de HTML y CSS de Codecademy](https://www.codecademy.com/learn/web) puede encontrarse información más específica acerca de la sintaxis y el uso de CSS, así como varios ejercicios para aprender a usarlo correctamente.