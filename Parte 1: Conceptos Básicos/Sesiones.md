# Sesiones

Durante una solicitud a un servidor web (por ejemplo, la carga de una página), una aplicación construida con PHP regenera su información desde cero. Esto significa que, por cada solicitud o vista de página, por defecto, PHP va a regenerar los valores de variables, constantes, objetos y cualquier tipo de información interna a la aplicación.

Esto puede no ser siempre deseable. Por ejemplo, para aplicaciones en las cuales se necesita mantener algún tipo de información acerca del visitante, como aquellas que cuentan con un área administrativa, es necesario que cierta información acerca del usuario actual se mantenga estable a lo largo de varias solicitudes. De esta manera se le podría permitir o denegar el acceso a ciertas áreas o características determinadas del sistema.

PHP permite hacer esto por medio del uso de sesiones de usuario. Las sesiones de usuario permiten almacenar ciertos datos en la memoria del servidor hasta que el navegador se cierre, y dichos datos pueden mantenerse a lo largo de varias visitas o vistas de página.

Para utilizar sesiones en PHP es indispensable realizar un llamado a la función `session_start()` antes de que se imprima cualquier tipo de contenido. Es recomendable usarla lo antes posible en el proceso de ejecución, y generalmente se la ejecuta entre las primeras líneas del archivo principal.

```php
<?php
session_start();
```

La información de la sesión de un usuario se almacena en la variable superglobal `$_SESSION`, la cual se maneja como un array.

Para ilustrar de qué manera `$_SESSION` mantiene los datos de una sesión de usuario, el siguiente ejemplo imprime un número y le suma una unidad por cada vista de la misma página:

```php
<?php
session_start();

if ( ! isset( $_SESSION['count'] ) ) {
    $_SESSION['count'] = 0;
}

$_SESSION['count']++;

echo $_SESSION['count'];
```