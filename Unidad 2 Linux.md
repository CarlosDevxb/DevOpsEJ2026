## 2.1 Comandos básicos para administración de sistemas

### 2.1.1 Gestión de archivos y directorios (`ls`, `cp`, `mv`, `rm`)

#### Teoría

| Comando | Parámetro | Descripción                                       |
| ------- | --------- | ------------------------------------------------- |
| `ls`    | `-l`      | Detallado (permisos, propietario, tamaño, fecha)  |
|         | `-a`      | Incluye ocultos                                   |
|         | `-h`      | Tamaño legible (KB, MB…)                          |
|         | `-i`      | Muestra número de inodo                           |
| `cp`    | `-r, -R`  | Recursivo (directorios)                           |
|         | `-p`      | Preserva timestamps, permisos, propietario        |
|         | `-a`      | Archive (recursivo + preserva enlaces y permisos) |
|         | `-v`      | Verbose                                           |
| `mv`    | `-i`      | Interactivo (pregunta antes de sobrescribir)      |
|         | `-n`      | No sobrescribir archivos existentes               |
|         | `-v`      | Verbose                                           |
| `rm`    | `-r`      | Recursivo                                         |
|         | `-f`      | Forzar, sin preguntar                             |
|         | `-v`      | Verbose                                           |

Los archivos y directorios en Linux son **inodos**: estructuras con metadatos (UID, GID, permisos, timestamps) y punteros a los bloques de datos.
