# Documentación Técnica del Sistema - Biblioteca

## 1. Arquitectura del Sistema
El sistema opera bajo una arquitectura monolítica Cliente-Servidor desplegada en el hosting de AwardSpace (`http://bibliotecaalex.atwebpages.com/`)[cite: 1, 7, 8].
- **Frontend:** HTML5, CSS3 y JavaScript Vanilla para la interacción del usuario y validación del lado del cliente[cite: 13].
- **Backend:** PHP procedural con extensión MySQLi para el procesamiento de solicitudes y lógica de negocio[cite: 8, 10, 14].
- **Base de Datos:** Motor MySQL gestionado mediante phpMyAdmin con la tabla `libros`[cite: 7, 8].

---

## 2. Documentación de Endpoints / Scripts (API Interna)

### Endpoint 1: Vista Principal (`index.php`)
- **Método HTTP:** `GET`[cite: 8]
- **Descripción:** Carga la interfaz gráfica y ejecuta una consulta SQL para listar todo el inventario de libros ordenados del más reciente al más antiguo[cite: 8, 9].
- **Parámetros GET (Opcionales):**
  - `success=1`: Dispara una alerta de registro exitoso.
  - `updated=1`: Indica que se actualizó el estado de un libro.
- **Consulta SQL:** `SELECT * FROM libros ORDER BY id DESC`[cite: 8]

### Endpoint 2: Registro de Libros (`guardar.php`)
- **Método HTTP:** `POST`[cite: 10]
- **Descripción:** Recibe los datos enviados por el formulario de registro, sanitiza las entradas para prevenir inyecciones SQL y realiza la inserción en la base de datos[cite: 10].
- **Parámetros POST (Requeridos):**
  - `titulo` (string): Nombre de la obra[cite: 10].
  - `autor` (string): Nombre del autor[cite: 10].
  - `isbn` (string): Código identificador[cite: 10].
- **Consulta SQL:** `INSERT INTO libros (titulo, autor, isbn) VALUES (...)`[cite: 10]
- **Respuesta:** Redireccionamiento HTTP a `index.php?success=1`[cite: 10].

### Endpoint 3: Cambio de Estado (`cambiarEstado.php`)
- **Método HTTP:** `POST`[cite: 14]
- **Descripción:** Recibe el ID del libro y su estado actual para alternar su disponibilidad entre Disponible (1) y Prestado (0)[cite: 14].
- **Parámetros POST (Requeridos):**
  - `id` (int): Clave primaria del libro[cite: 14].
  - `actual` (int): Estatus actual (1 o 0)[cite: 14].
- **Consulta SQL:** `UPDATE libros SET disponible = $nuevo_estado WHERE id = $id`[cite: 14]
- **Respuesta:** Redireccionamiento HTTP a `index.php?updated=1`[cite: 14].
