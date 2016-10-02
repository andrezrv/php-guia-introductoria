# HTML

Dado que PHP es un lenguaje de procesamiento de texto pensado para desarrollo de sitios web, y que los sitios web se escriben usando HTML, es necesario tener al menos un conocimiento básico acerca de cómo opera HTML y cómo usarlo.

HTML significa "HyperText Markup Language" ("lenguaje de marcado de hipertexto", en español), y fue creado en 1993 por Tim Berners-Lee, con la intención de proponer un lenguaje estándar para la creación de sitios web. Tal como su nombre lo indica, está pensado para la creación de hipertexto: texto enriquecido por medio de la aplicación de distintos tipos de formato.

Al contrario de una definición errónea y bastante común, HTML no es un lenguaje de programación, sino puramente descriptivo. No permite tomar decisiones acerca del funcionamiento de un programa o aplicación, como hacen los lenguajes de programación, sino que solo da la posibilidad de declarar la estructura y el contenido de un documento. Esta característica es propia de los lenguajes de marcado, tales como XML, grupo al cual pertenece HTML.

## Sintaxis

La característica principal de HTML como lenguaje es la aplicación de etiquetas o _tags_ a un documento de texto determinado. Estas etiquetas pueden cumplir con dos propósitos: por un lado, darle información al navegador acerca del documento que está procesando,  y por otro, declarar el contenido y la estructura del documento.

Las etiquetas HTML siguen el siguiente formato:

```php
<nombre atributo="valor">Contenido</nombre>
```

El nombre de la etiqueta está relacionado con el propósito que cumple la misma dentro del documento. Por ejemplo, si usamos la etiqueta `<strong>` para envolver texto, estamos indicando que ese texto tiene mayor relevancia, y si usamos `<h1>` estamos indicando un título de primer nivel.

Por ejemplo, el siguiente código mostraría un texto conformado por un título y un párrafo, con parte del texto en negrita:

```php
<h1>Lorem Ipsum</h1>

<p>
    <strong>Lorem ipsum</strong> dolor sit amet.
</p>
```

Un documento HTML válido debe respetar e incluir ciertas etiquetas, más allá de su contenido concreto. Debe incluir el _doctype_ para indicarle al navegador qué versión de HTML debe utilizar, la etiqueta `html` para encerrar el contenido del documento, la etiqueta `head` para proveer información específica para el navegador, y la etiqueta `body` para contener aquello que verá el visitante de la página.

```php
<!DOCTYPE html>
<html>
 <head>
     <meta charset="utf-8">
     <title></title>
 </head>
 <body>
     <h1>Lorem Ipsum</h1>

     <p>
         <strong>Lorem ipsum</strong> dolor sit amet.
    </p>
 </body>
</html>
```

En el [curso de HTML y CSS de Codecademy](https://www.codecademy.com/learn/web) puede encontrarse información más específica acerca de la sintaxis y el uso de HTML, así como varios ejercicios para aprender a usarlo correctamente.