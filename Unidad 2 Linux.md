## 2.1 Comandos básicos para administración de sistemas

### Gestión de archivos y directorios (`ls`, `cp`, `mv`, `rm`)

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


### Verificación de estado de servicios (`systemctl`, `service`)

#### Teoría Básica

* **¿Qué es systemd?**
  systemd es el sistema de inicialización (init) y gestor de servicios predominante en la mayoría de distribuciones Linux modernas. Se encarga de:

  * Arrancar el sistema y sus servicios (daemons) en paralelo.
  * Gestionar dependencias y orden de arranque.
  * Supervisar procesos, reiniciarlos si fallan, y reunir sus logs.

* **¿Qué es una unidad (.service)?**
  Una unidad de tipo `service` describe cómo arrancar, parar y supervisar un demonio. Cada archivo `.service` es un contenedor de metadatos y acciones a ejecutar.

* **Ubicación de archivos de servicio**

  * `/usr/lib/systemd/system/` (servicios provistos por paquetes del sistema)
  * `/etc/systemd/system/` (servicios administrados o personalizados)
  * `/run/systemd/system/` (servicios generados en tiempo de ejecución)

* **Listar servicios**

  ```bash
  # Todas las unidades service (cargadas en memoria)
  systemctl list-units --type=service

  # Todas las posibles unidades service (disponibles en disco)
  systemctl list-unit-files --type=service

  # Sólo las habilitadas (se iniciarán al arranque)
  systemctl list-unit-files --type=service | grep enabled
  ```

* **Targets vs viejos runlevels**
  systemd utiliza “targets” en lugar de runlevels SysV. Ejemplos:

  * `multi-user.target` ≈ runlevel 3 (modo texto multiusuario)
  * `graphical.target` ≈ runlevel 5 (modo texto + GUI)
    Cambiar target:

  ```bash
  systemctl isolate multi-user.target
  ```
