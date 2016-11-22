# Programación Orientada a Objetos

La programación orientada a objetos es un paradigma de programación basado en la idea de que un programa está definido por ciertas interacciones entre un usuario y una o más entidades. Dichas entidades se llaman _objetos_ y cuentan, por un lado, con _atributos_, y por otro lado, con _métodos_.

Los atributos (también llamados _propiedades_), son diferentes datos que definen el estado actual o la forma de un objeto. Los métodos son acciones que un objeto puede realizar, y que tienen la capacidad de modificar el estado del objeto al que pertenecen. En PHP, los métodos son similares a las funciones.

Los objetos son tipos de datos complejos, y solamente pueden construirse a partir de un tipo de definición llamado _clase_. En PHP, un objeto puede contruirse de la siguiente manera:

```php
<?php
class Futbolista {
    var $nombre;
    var $apellido;
    var $energia;
}

$jugador = new Futbolista;
```

En PHP, las variables internas de una clase son sus propiedades. Al crear un nuevo objeto a partir de una clase, podemos modificar las propiedades internas del objeto:

```php
<?php
class Futbolista {
 var $nombre;
 var $apellido;
 var $energia;
}

$jugador = new Futbolista;

$jugador->nombre = 'Lionel';
$jugador->apellido = 'Messi';
$jugador->energia = 100;
```

Al introducir métodos en una clase, estos tienen la posibilidad de modificar las propiedades internas del objeto. La variable que se usa para referirse al objeto mismo en el contexto de un método es `$this`.

```php
<?php
class Futbolista {
    var $nombre;
    var $apellido;
    var $energia;

    /**
     * Descuenta un punto de energía por cada 100 metros corridos.
     */
    function correr( $metros ) {
        if ( $metros ) {
            $this->energia = $this->energia - ( $metros / 100 );
        }
    }
}

$jugador = new Futbolista;

$jugador->nombre = 'Lionel';
$jugador->apellido = 'Messi';
$jugador->energia = 100; // $jugador->energia vale 100.

$jugador->correr( 100 ); // $jugador->energia vale 99.
$jugador->correr( 100 ); // $jugador->energia vale 98.
```

También es posible asignar valores predeterminados a un objeto durante la declaración de la clase, con lo cual puede evitarse declarar el valor de la propiedad después de haber creado el objeto.

```php
<?php
class Futbolista {
    var $nombre;
    var $apellido;
    var $energia = 100; // Valor predeterminado.

    /**
     * Descuenta un punto de energía por cada 100 metros corridos.
     */
    function correr( $metros ) {
        if ( $metros ) {
            $this->energia = $this->energia - ( $metros / 100 );
        }
    }
}

$jugador = new Futbolista; // $jugador->energia vale 100.

$jugador->nombre = 'Lionel';
$jugador->apellido = 'Messi';

$jugador->correr( 100 ); // $jugador->energia vale 99.
$jugador->correr( 100 ); // $jugador->energia vale 98.

```

Las clases admiten la creación de un método llamado `__construct()`, el cual se ejecuta automáticamente al crear un nuevo objeto. Este método suele usarse para asignar propiedades al objeto dependiendo de ciertas condiciones.

```php
<?php
class Futbolista {
    var $nombre;
    var $apellido;
    var $energia = 100; // Valor predeterminado.

    function __construct( $nombre, $apellido ) {
        $this->nombre = $nombre;
        $this->apellido = $apellido;
    }

    /**
     * Descuenta un punto de energía por cada 100 metros corridos.
     */
    function correr( $metros ) {
        if ( $metros ) {
            $this->energia = $this->energia - ( $metros / 100 );
        }
    }
}

$jugador = new Futbolista( 'Lionel', 'Messi' );
// $jugador->nombre es "Lionel".
// $jugador->apellido es "Messi".
// $jugador->energia es 100.

$jugador->correr( 100 ); // $jugador->energia vale 99.
$jugador->correr( 100 ); // $jugador->energia vale 98.
```

