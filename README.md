# Sistema de Control de Biblioteca

Aplicación web desarrollada en PHP nativo, MySQL, HTML5, CSS3 y JavaScript para la gestión de inventario, registro y préstamo de libros.

- **URL en producción:** http://bibliotecaalex.atwebpages.com/

## Estructura del Proyecto
- `index.php`: Interfaz principal, formulario de registro y tabla dinámica de inventario.
- `guardar.php`: Script backend para procesar el alta de nuevos libros.
- `cambiarEstado.php`: Script backend para alternar el estado Disponible/Prestado.
- `styles.css`: Hoja de estilos responsiva con diseño basado en CSS Grid.
- `script.js`: Validación interactiva de formularios y notificaciones en cliente.

## Instalación y Base de Datos
1. Crear el subdominio en AwardSpace y subir los archivos vía File Manager o FTP.
2. En phpMyAdmin, ejecutar el siguiente script SQL para crear la tabla principal:
####HTML code
```html
CREATE TABLE libros (
    id INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(150) NOT NULL,
    autor VARCHAR(100) NOT NULL,
    isbn VARCHAR(20) NOT NULL,
    disponible INT DEFAULT 1
);

3. Insertar los registros iniciales de prueba:
####HTML code
```html
INSERT INTO libros (titulo, autor, isbn, disponible) VALUES
('Cien años de soledad', 'Gabriel García Márquez', '978-0307474728', 1),
('Don Quijote de la Mancha', 'Miguel de Cervantes', '978-8424937461', 1);
('Y el amor imposible', 'Alexgg', '16／ 11／ 26hb')
('Labios de cereza', 'T3R Elemento', '544877888／8')
