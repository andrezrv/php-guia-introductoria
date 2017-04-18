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

## Constructores
Las clases admiten la creación de un método llamado `__construct()`, el cual se ejecuta automáticamente al crear un nuevo objeto. Este método suele usarse para asignar propiedades al objeto dependiendo de ciertas condiciones. De esta manera, los parámetros de un constructor pueden usarse al crear un objeto para asignar valores a sus propiedades.

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

$jugador = new Futbolista( 'Lionel', 'Messi' ); // Se crea objeto usando constructor.
// $jugador->nombre es "Lionel".
// $jugador->apellido es "Messi".
// $jugador->energia es 100.

$jugador->correr( 100 ); // $jugador->energia vale 99.
$jugador->correr( 100 ); // $jugador->energia vale 98.
```

Los constructores forman parte del conjunto de métodos mágicos que provee PHP. Llamamos métodos mágicos a un cierto tipo de métodos con nombres reservados, los cuales se ejecutan de manera automática en determinados contextos, sin necesidad de llamarlos desde una instancia. Estos métodos mágicos suelen ser nombrados con el prefijo `__`.

## Destructores
Un método destructor, identificado con el nombre `__destruct()`, es un método mágico que se ejecuta automáticamente cuando el objeto deja de ser utilizado. Por lo general, esto ocurre después de ejecutarse la última línea del programa.

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

	function __destruct() {
		echo 'Hola mundo!';
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

$jugador = new Futbolista( 'Lionel', 'Messi' ); // Se crea objeto usando constructor.
// $jugador->nombre es "Lionel".
// $jugador->apellido es "Messi".
// $jugador->energia es 100.

$jugador->correr( 100 ); // $jugador->energia vale 99.
$jugador->correr( 100 ); // $jugador->energia vale 98.
// Se imprime "Hola mundo!" al ejecutarse el destructor.
```

## Herencia

El paradigma de programación orientada a objetos permite que ciertas clases hereden características de otras. Este principio es llamado _**herencia**_, y PHP lo implementa a través de la palabra clave `extends`.

Cuando una clase extiende a otra, tiene acceso a las propiedades y métodos protegidos de la clase principal, e incluso puede sobreescribirlos.

```php
<?php
class Persona {
	var $nombre;
	var $apellido;
	var $energia = 50; // Valor predeterminado.

	function __construct( $nombre, $apellido ) {
		$this->nombre = $nombre;
		$this->apellido = $apellido;
	}

	/**
	 * Descuenta 5 puntos de energía por cada 100 metros corridos.
	 */
	function correr( $metros ) {
		if ( $metros ) {
			$this->energia = $this->energia - ( ( 5 * $metros ) / 100 );
		}
	}
}

class Futbolista extends Persona {
	var $energia = 100; // Sobreescribe el valor por defecto de la clase Persona.

	/**
	 * Descuenta un punto de energía por cada 100 metros corridos.
	 */
	function correr( $metros ) {
		if ( $metros ) {
			$this->energia = $this->energia - ( $metros / 100 );
		}
	}
}
```

De esta manera, los objetos creados a partir de la clase principal pueden tener un comportamiento diferente de los creados a partir de la clase secundaria.

```php
<?php
$persona = new Persona( 'Juan', 'Pérez' );
$persona->correr( 100 );
echo $persona->energia; // Imprime "45";

$futbolista = new Futbolista( 'Lionel', 'Messi' );
$futbolista->correr( 100 );
echo $persona->energia; // Imprime "99";
```

El principio de herencia también permite crear múltiples subclases a partir de una clase principal, e incluso introducir niveles de herencia adicionales.

```php
<?php
class Persona {}

class Deportista extends Persona {}

class Futbolista extends Deportista {}

class Basquetbolista extends Deportista {}
```

## Visibilidad

PHP permite declarar el tipo de visibilidad de propiedades y métodos de una clase, con lo cual es posible definir en qué contextos pueden ser utilizados. La visibilidad puede ser de tres tipos: pública, protegida o privada.

### Visibilidad pública

Se define con la palabra clave `public`, y permite que propiedades y métodos sean utilizados en cualquier contexto: dentro de la clase, en otras clases, o en un objeto previamente instanciado.

Adicionalmente, los valores de las propiedades públicas pueden ser redefinidos para los objetos previamente instanciados.

Es importante notar que todo método que no declare explícitamente su visibilidad será tratado como público, y lo mismo sucederá con las propiedades declaradas usando `var`.

```php
<?php
class Futbolista {
	public $nombre;
	public $apellido;
	public $energia = 100; // Valor predeterminado.

	function __construct( $nombre, $apellido ) {
		$this->nombre = $nombre;
		$this->apellido = $apellido;
	}

	/**
	 * Descuenta un punto de energía por cada 100 metros corridos.
	*/
	public function correr( $metros ) {
		if ( $metros ) {
			$this->energia = $this->energia - ( $metros / 100 );
		}
	}
}

$jugador = new Futbolista( 'Lionel', 'Messi' );
// $jugador->nombre es "Lionel".
// $jugador->apellido es "Messi".
// $jugador->energia es 100.

/**
* Uso de propiedades y métodos públicos:
*/
echo $jugador->nombre; // Imprime "Lionel".
$jugador->correr( 100 ); // $jugador->energia vale 99.
echo $jugador->energia; // Imprime "99".

/**
* Redefinición de propiedades públicas:
*/
$jugador->nombre = 'Gonzalo';
$jugador->apellido = 'Higuaín';
$jugador->energia = 50;
echo $jugador->nombre; // Imprime "Gonzalo".
echo $jugador->apellido; // Imprime "Higuaín".
echo $jugador->energia; // Imprime "50".
```

## Visibilidad privada
Se define con la palabra clave `private`, y solo permite utilizar propiedades y métodos privados desde la clase que los define.

```php
<?php
class Futbolista {
	private $nombre;
	private $apellido;
	private $energia = 100; // Valor predeterminado.

	function __construct( $nombre, $apellido ) {
		$this->nombre = $nombre;
		$this->apellido = $apellido;
	}

	/**
	 * Descuenta un punto de energía por cada 100 metros corridos.
	*/
	public function correr( $metros ) {
		if ( $metros ) {
			$energia_actual = $this->energia - ( $metros / 100 );
			$this->redefinir_energia( $energia_actual );
		}
	}

	private function redefinir_energia( $valor ) {
		$this->energia = $valor;
	}

	public function energia_actual() {
		return $this->energia;
	}
}

$jugador = new Futbolista( 'Lionel', 'Messi' );

/**
* Uso de propiedades y métodos privados:
*/
$jugador->correr( 100 ); // $jugador->energia vale 99.
echo $jugador->energia_actual(); // Imprime "99".
echo $jugador->energia; // Error.
```

## Visibilidad protegida
Se define con la palabra clave `protected`. Hace accesibles las propiedades y métodos de una clase principal dentro de una clase secundaria, pero no en un objeto instanciado.

```php
<?php
class Deportista {
	protected $nombre;
	protected $apellido;
	protected $energia = 100; // Valor predeterminado.

	function __construct( $nombre, $apellido ) {
		$this->nombre = $nombre;
		$this->apellido = $apellido;
	}

	/**
	 * Descuenta un punto de energía por cada 100 metros corridos.
	*/
	public function correr( $metros ) {
		if ( $metros ) {
			$energia_actual = $this->energia - ( $metros / 100 );
			$this->redefinir_energia( $energia_actual );
		}
	}

	private function redefinir_energia( $valor ) {
		$this->energia = $valor;
	}

	public function energia_actual() {
		return $this->energia;
	}
}

class Futbolista extends Deportista {
	// Clase vacía.
}

$jugador = new Futbolista( 'Lionel', 'Messi' );

/**
* Uso de propiedades y métodos protegidos:
*/
$jugador->correr( 100 ); // $jugador->energia vale 99.
echo $jugador->energia_actual(); // Imprime "99".
echo $jugador->energia; // Error.
```

## Getters
Los _getters_ son métodos mágicos que se ejecutan cuando un objeto instanciado intenta acceder a una propiedad privada o protegida. Llevan el nombre `__get()` y reciben un único parámetro, correspondiente al nombre de la propiedad a la cual se desea acceder.

Dado que, por defecto, PHP arroja un error cuando se intenta acceder a propiedades privadas o protegidas, los _getters_ son ideales para restringir qué valores van a ser accesibles desde la instancia y cuáles no.

```php
<?php
class Futbolista {
	private $nombre;
	private $apellido;

	function __construct( $nombre, $apellido ) {
		$this->nombre = $nombre;
		$this->apellido = $apellido;
	}

	function __get( $propiedad ) {
		return $this->$propiedad;
	}
}

$jugador = new Futbolista( 'Lionel', 'Messi' ); 
echo $jugador->nombre; // // Ejecuta __get() e imprime "Lionel".
```

## Setters
Un _setter_, definido con el nombre `__set()`, se ejecuta automáticamente cuando se intenta asignar un valor a una propiedad privada o protegida desde un objeto. Recibe dos parámetros: el primero es el nombre de la propiedad, y el segundo es el valor que se pretende asignar.

De forma similar a cómo funcionan los _setters_, son ideales para restringir qué propiedades pueden ser definidas desde el objeto, y de qué manera.

```php
<?php
class Futbolista {
	private $nombre;
	private $apellido;

	function __construct( $nombre, $apellido ) {
		$this->nombre = $nombre;
		$this->apellido = $apellido;
	}

	function __get( $propiedad ) {
		return $this->$propiedad;
	}

	function __set( $propiedad, $valor ) {
		$this->$propiedad = $valor;
	}
}

$jugador = new Futbolista( 'Lionel', 'Messi' );
$jugador->nombre = 'Lio'; // Ejecuta __set().
echo $jugador->nombre; // Ejecuta __get() e imprime "Lio".
```

## Propiedades estáticas
Las propiedades estáticas, declaradas con la palabra clave `static`, son un tipo especial de propiedad que no considera el contexto particular de cada objeto creado a partir de una clase. No tiene relación directa con las instancias de una clase, sino con la clase misma. Esto significa que su último valor asignado se va a mantener igual, sin importar cuántos objetos se hayan creado a partir de la clase.

Para acceder a propiedades estáticas es necesario cambiar el símbolo  accesor. En lugar de usar `->`, como hacemos con propiedades no estáticas, debe usarse `::`.

Por otra parte, al no ser utilizado en un contexto de objeto, en lugar de usar el nombre de la variable a la cual se asignó una instancia, se usa directamente el nombre de la clase. Por ejemplo, `Clase::$propiedad`.

Dentro de la clase misma, en lugar de usar `$this`, que corresponde a la instancia actual, se usa `self`, una palabra clave que referencia el nombre de la clase actual.

```php
<?php
class Futbolista {
	private $nombre;
	private $apellido;
	public $cantidad_de_futbolistas = 0;

	function __construct( $nombre, $apellido ) {
		$this->nombre = $nombre;
		$this->apellido = $apellido;
		self::$cantidad_de_futbolistas++;
	}
}

$jugador_1 = new Futbolista( 'Lionel', 'Messi' );
$jugador_2 = new Futbolista( 'Gonzalo', 'Higuaín' );

echo Futbolista::$cantidad_de_futbolistas; // Imprime "2".
```

## Métodos estáticos
Al igual que las propiedades estáticas, los métodos estáticos carecen de contexto, y solamente están relacionados con la clase que los contiene. Su uso es similar al de una función auxiliar.

También se declaran con la palabra clave `static`, y su uso del accesor `::` es igual al de las propiedades estáticas.

```php
<?php
class Futbolista {
	private $nombre;
	private $apellido;
	private $cantidad_de_futbolistas = 0;

	function __construct( $nombre, $apellido ) {
		$this->nombre = $nombre;
		$this->apellido = $apellido;
		self::$cantidad_de_futbolistas++;
	}

	static function cantidad_de_futbolistas() {
		return self::$cantidad_de_futbolistas;
	}
}

$jugador_1 = new Futbolista( 'Lionel', 'Messi' );
$jugador_2 = new Futbolista( 'Gonzalo', 'Higuaín' );

echo Futbolista::cantidad_de_futbolistas(); // Imprime "2".
```