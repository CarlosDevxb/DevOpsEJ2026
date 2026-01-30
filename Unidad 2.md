# Unidad 2: Linux

El sistema operativo Linux es la base de la infraestructura moderna de Internet y la nube. Como ingeniero DevOps, la terminal no es una opción, es tu panel de control principal.

## 2.1 Comandos Básicos de terminal
La terminal (o shell) permite interactuar con el sistema operativo mediante comandos de texto, lo cual es mucho más rápido y potente que una interfaz gráfica para tareas de administración.

*   **Navegación:**
    *   `pwd`: Muestra la ruta actual (*Print Working Directory*).
    *   `ls`: Lista los archivos (`ls -la` muestra ocultos y detalles).
    *   `cd`: Cambia de directorio (`cd ..` para subir un nivel).
*   **Gestión de Archivos:**
    *   `mkdir`: Crea una carpeta nueva.
    *   `touch`: Crea un archivo vacío.
    *   `cp`: Copia archivos (`cp origen destino`).
    *   `mv`: Mueve o renombra archivos.
    *   `rm`: Elimina archivos (`rm -rf` elimina carpetas y contenido, ¡usar con precaución!).
*   **Visualización:**
    *   `cat`: Muestra todo el contenido de un archivo.
    *   `grep`: Busca texto específico dentro de archivos o salidas de comandos.

## 2.2 Instalación de paquetes
A diferencia de Windows donde descargas `.exe` de internet, en Linux el software se gestiona mediante **Repositorios** oficiales y seguros.

*   **APT (Advanced Package Tool):** Estándar en Debian, Ubuntu y Mint.
    *   `sudo apt update`: Actualiza la lista de paquetes disponibles (el catálogo).
    *   `sudo apt install [nombre]`: Descarga e instala un programa (ej. `sudo apt install git`).
    *   `sudo apt upgrade`: Actualiza todos los programas instalados a su última versión.
*   **Nota sobre `sudo`:** Significa "SuperUser DO". Otorga permisos de administrador temporalmente para ejecutar comandos sensibles.

## 2.3 Permisos de ejecución
Linux es un sistema multiusuario estricto. Cada archivo tiene tres tipos de permisos para tres tipos de usuarios (Dueño, Grupo, Otros).

*   **Tipos de Permiso:**
    *   **r (Read):** Leer el archivo.
    *   **w (Write):** Modificar el archivo.
    *   **x (Execute):** Ejecutar el archivo como un programa.
*   **Comando `chmod` (Change Mode):**
    *   **Simbólico:** `chmod +x script.sh` (Agrega permiso de ejecución).
    *   **Numérico (Octal):** `chmod 755 archivo` (Dueño tiene todo [7], otros solo lectura/ejecución [5]).

## 2.4 Secure Shell (SSH)
Es el protocolo estándar para conectarse y administrar servidores de forma remota y segura (encriptada).

*   **Uso básico:** `ssh usuario@direccion_ip_servidor`
*   **Autenticación por Llaves (SSH Keys):** Método profesional que reemplaza las contraseñas.
    1.  Creas un par de llaves (Pública/Privada) en tu máquina.
    2.  Colocas tu **Llave Pública** en el servidor.
    3.  El servidor te reconoce y permite el acceso sin escribir contraseña, ideal para automatización.

## 2.5 Scripting y automatización
Un **Shell Script** es un archivo de texto que contiene una secuencia de comandos que el sistema ejecuta en orden. Es la base de la automatización en DevOps.

*   **Shebang (`#!/bin/bash`):** Es la primera línea obligatoria que indica al sistema que el archivo debe ejecutarse con Bash.
*   **Ejemplo de Script de Mantenimiento:**
    ```bash
    #!/bin/bash
    echo "Iniciando actualización automática..."
    sudo apt update && sudo apt upgrade -y
    echo "Limpiando paquetes innecesarios..."
    sudo apt autoremove -y
    echo "¡Mantenimiento completado!"
    ```