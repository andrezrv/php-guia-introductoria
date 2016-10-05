# Desafíos

## Inclusión de archivos

Crear un sitio web con 4 páginas diferentes. Cada página debe incluir, como elementos comunes, un encabezado, un área de navegación, un pie y una barra lateral. El HTML correspondiente a los elementos comunes no debe estar incluido en cada archivo, sino imprimirse dinámicamente usando PHP.

## Manipulación de datos

Usando el sitio web construido en el desafío anterior, modificar los enlaces internos para que cada página sea visible pasando el nombre del archivo que la contiene por medio de `GET`. Por ejemplo, un enlace a `http://localhost/misitio/blog.php` debería modificarse por `http://localhost/misitio/index.php?page=blog`.

Luego, usando `$_GET`, debe obtenerse el nombre de la página requerida y cargar el archivo correspondiente. Se recomienda lo siguiente:

1. Guardar los nombres de páginas que se permite ver al usuario en un array y chequear que la página requerida esté en la lista antes de cargarla. Esto permite que el usuario no ejecute archivos no autorizados al modificar la URL.
2. Tener un archivo que maneje mensajes de error para páginas no encontradas.