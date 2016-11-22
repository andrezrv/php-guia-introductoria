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
