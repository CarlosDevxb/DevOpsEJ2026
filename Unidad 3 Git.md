# Unidad 3: Git y GitHub

El control de versiones es la columna vertebral del desarrollo de software moderno. Sin él, la colaboración es imposible y el riesgo de perder código es altísimo.

## 3.1 Fundamentos de Git
**Git** es un sistema de control de versiones distribuido. Imagínalo como una "máquina del tiempo" para tu código que permite guardar el estado de tu proyecto en diferentes momentos.

*   **Diferencia clave:**
    *   **Git:** Es el software que instalas en tu computadora (la herramienta).
    *   **GitHub:** Es la plataforma en la nube donde alojas tus repositorios (la red social del código).
*   **Objetivo:** Rastrear cambios, coordinar el trabajo entre múltiples personas y asegurar la integridad del código.

## 3.2 Comandos de Git
Estos son los comandos esenciales que usarás el 90% del tiempo en la terminal.

*   **Configuración inicial:**
    *   `git config --global user.name "Tu Nombre"`
    *   `git config --global user.email "tu@email.com"`
*   **Ciclo de vida básico:**
    1.  `git init`: Transforma la carpeta actual en un repositorio de Git.
    2.  `git status`: Muestra qué archivos han cambiado.
    3.  `git add .`: Prepara todos los archivos modificados para ser guardados (Staging Area).
    4.  `git commit -m "mensaje"`: Guarda los cambios permanentemente en el historial local.
    5.  `git log`: Muestra el historial de commits.

## 3.3 Repositorios en GitHub
Un repositorio remoto en GitHub sirve como copia de seguridad y punto central de colaboración.

### 3.3.1 Ramas (Branches)
Las ramas son líneas de tiempo paralelas. Permiten trabajar en nuevas funciones o arreglos sin afectar el código principal que funciona (producción).
*   **Rama `main` (o `master`):** Contiene el código estable y listo para producción.
*   **Comando:** `git checkout -b nombre-rama` (Crea y cambia a una nueva rama).

### 3.3.2 Forks
Un **Fork** es una copia de un repositorio ajeno en tu propia cuenta de GitHub.
*   **Uso:** Es fundamental en el código abierto (Open Source). Copias el proyecto, lo modificas en tu cuenta y luego propones los cambios al dueño original.

### 3.3.3 Commits
Un commit es una "foto" del proyecto en un momento específico.
*   **Buenas prácticas:**
    *   Deben ser atómicos (resolver una sola cosa).
    *   El mensaje debe ser claro y descriptivo (ej: "Agrega validación al formulario de login" en lugar de "arreglos").

### 3.3.4 Push
El comando `git push` envía tus commits locales al repositorio remoto en GitHub.
*   **Sintaxis:** `git push origin nombre-rama`
*   **Importancia:** Hasta que no haces push, tu código solo existe en tu máquina. Si tu disco duro falla, se pierde.

### 3.3.5 Pull Request (PR)
Es el corazón de la colaboración en GitHub. Un PR es una petición para fusionar (merge) los cambios de tu rama (o fork) hacia la rama principal del repositorio original.
*   **Code Review:** Permite que otros desarrolladores revisen tu código, comenten errores y aprueben los cambios antes de integrarlos.

## 3.5 Protección de Ramas
En entornos profesionales, la rama `main` es sagrada. GitHub permite configurar reglas de protección ("Branch Protection Rules") para evitar desastres.

*   **Reglas comunes:**
    1.  **Require pull request reviews:** Nadie puede hacer `push` directo a `main`. Todo cambio debe venir de un PR y ser aprobado por al menos otro desarrollador.
    2.  **Require status checks to pass:** Bloquea la fusión si las pruebas automáticas (CI/CD) fallan.
    3.  **Include administrators:** Las reglas aplican incluso a los jefes o dueños del repo.

> **Nota DevOps:** La protección de ramas es el primer paso para implementar **Integración Continua (CI)**, asegurando que el código "roto" nunca llegue a producción.