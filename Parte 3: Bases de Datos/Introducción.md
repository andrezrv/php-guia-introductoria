# Introducción

En la gran mayoría de los sitios web y aplicaciones que ofrecen algún tipo de interacción con un usuario (ya sea un visitante, un cliente o un administrador), existe la necesidad de guardar cierta información ingresada por dicho usuario para poder utilizarla más tarde. El lugar en donde se guarda dicha información es lo que llamamos base de datos.

Existen muchos tipos diferentes de bases de datos, aunque el más popular, y en el cual nos vamos a centrar, es el relacional. Una base de datos relacional organiza la información contenida en tablas, las cuales contienen una fila para cada entrada ingresada por un usuario. A su vez, las filas se dividen en columnas para separar los diferentes tipos de datos contenidos en una entrada.

El sistema de bases de datos relacionales más utilizado en la actualidad se llama **SQL** (_Structured Query Language_), y en él se basan otros varios sistemas ampliamente usados en desarrollo web, tales como SQLite y **MySQL**. PHP ofrece una amplia integración con MySQL, por lo tanto nos vamos a centrar en este sistema.

Existen muchas aplicaciones, tanto de escritorio como de navegador, para manejar bases de datos de manera sencilla. Al trabajar con PHP, lo más común es usar **phpMyAdmin**, incluido en XAMPP y MAMP.

Ingresando en phpMyAdmin puede verse una lista de bases de datos actualmente creadas en el equipo sobre el cual se está trabajando. Al explorar cualquiera de esas bases de datos podemos ver su estructura. Por ejemplo, sus tablas, las filas y columnas de cada tabla, y los tipos de datos de cada columna.

También podemos crear nuevas bases de datos y nuevas tablas, agregar nuevas entradas, y modificar y eliminar entradas existentes.

MySQL trabaja a través de **_queries_**, a las cuales nos solemos referir en español como _consultas_, _pedidos_ o _peticiones_, siendo estas dos últimas las traducciones más exactas. Algunos desarrolladores las llaman _sentencias_, pero esto es una mala traducción de _sentence_ (que suele usarse en inglés como sinónimo de query), lo cual significa _oración_.

Estas queries son las que indican al motor de base de datos qué operación debe realizar: mostrar resultados, insertar información nueva, o modificar o remover información existente. En phpMyAdmin, las queries pueden escribirse accediendo a la pestaña SQL.

Al interactuar con phpMyAdmin a través de su interfaz gráfica no necesitamos crear los pedidos manualmente, al menos para casos sencillos. Sin embargo, al generarse algún pedido, phpMyAdmin muestra cuál fue el código con el que se ejecutó. Es importante observar cómo se construye ese código, ya que sí vamos a necesitar escribirlo manualmente al conectar MySQL con PHP.
