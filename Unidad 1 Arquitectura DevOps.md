# Unidad 1: Arquitectura DevOps

## 1.1 Fundamentos de Frameworks
Un **Framework** (marco de trabajo) es una estructura conceptual y tecnológica que sirve de base para la organización y desarrollo de software. A diferencia de una simple librería, un framework impone una forma de trabajar, concepto conocido como **Inversión de Control** (el framework te llama a ti, no tú al framework).

*   **Objetivo:** Proveer un esquema o esqueleto con herramientas y reglas predefinidas.
*   **Importancia:**
    *   **Estandarización:** Define una arquitectura común, facilitando que nuevos desarrolladores se integren rápidamente.
    *   **Velocidad:** Evita escribir código repetitivo (*boilerplate*) para tareas comunes (autenticación, conexión a BD).
    *   **Seguridad:** Implementa protecciones por defecto contra vulnerabilidades comunes.

## 1.2 Frameworks y Lenguajes de Programación
Es fundamental distinguir entre el lenguaje (la sintaxis) y el framework (la herramienta).

| Característica | Lenguaje de Programación | Framework |
| :--- | :--- | :--- |
| **Definición** | La materia prima (sintaxis, lógica). | La fábrica (herramientas, reglas). |
| **Ejemplos** | JavaScript, Java, Python, C#. | React, Angular, Spring Boot, Django. |
| **Flexibilidad** | Total (puedes hacer lo que quieras). | Limitada (sigues las reglas del framework). |

**Importancia:** El lenguaje provee la capacidad de cómputo, pero el framework provee la capacidad de **escalar** y mantener el software en un entorno profesional.

## 1.3 JavaScript y TypeScript

### JavaScript (JS)
Es el lenguaje estándar de la web. Dinámico y flexible, permite interactividad en el navegador y lógica en el servidor (Node.js).

### TypeScript (TS)
Es un superconjunto de JavaScript que añade **tipado estático**.
*   **Importancia:** En proyectos grandes (DevOps/Enterprise), TypeScript es vital porque detecta errores antes de ejecutar el código (en tiempo de compilación), mejorando la calidad y mantenibilidad del software.

### 1.3.1 React
Biblioteca de JavaScript desarrollada por Meta (Facebook) para construir interfaces de usuario.
*   **Características:** Basado en componentes reutilizables y el Virtual DOM. Es "no opinado" (unopinionated), lo que significa que no impone una forma de manejar rutas o datos.
*   **Enfoque Empresarial:** React ofrece libertad y un ecosistema gigante. Es ideal si la empresa busca flexibilidad o tiene necesidades muy específicas de UI. Sin embargo, requiere que el equipo de arquitectura defina estándares claros, ya que React por sí solo no impone reglas estrictas de estructura de carpetas o flujo de datos.

### 1.3.2 Angular
Framework de desarrollo plataforma desarrollado por Google.
*   **Características:** Utiliza TypeScript por defecto. Es un framework "todo incluido" (baterías incluidas) con una arquitectura MVC estricta, inyección de dependencias y herramientas de testing integradas.
*   **Enfoque Empresarial:** Preferido en entornos corporativos (Banca, Seguros) por su **robustez y estandarización**. Al imponer una estructura rígida, facilita que equipos grandes colaboren sin que el código se vuelva caótico. Si un desarrollador conoce Angular, puede trabajar en cualquier proyecto Angular de la empresa sin curva de aprendizaje sobre la estructura.

### 1.3.3 APIs (Interfaz de Programación de Aplicaciones)
Mecanismo que permite que dos componentes de software se comuniquen entre sí mediante un conjunto de definiciones y protocolos. En el contexto DevOps, las APIs (generalmente **REST**) son el pegamento que une microservicios, frontends y herramientas de automatización.

*   **Funcionamiento:** Se basa en un ciclo de **Petición (Request)** y **Respuesta (Response)**, generalmente intercambiando datos en formato **JSON**.
*   **Verbos HTTP Clave:**
    *   `GET`: Obtener datos (Lectura).
    *   `POST`: Crear nuevos datos (Escritura).
    *   `PUT/PATCH`: Actualizar datos (Modificación).
    *   `DELETE`: Eliminar datos (Borrado).
*   **Códigos de Estado (Status Codes):**
    *   `200 OK`: Éxito.
    *   `400 Bad Request`: Error del cliente (datos mal enviados).
    *   `500 Internal Server Error`: Error del servidor (código roto).
*   **Importancia en DevOps:**
    *   **Desacoplamiento:** El equipo de Frontend y Backend pueden trabajar independientemente.
    *   **Automatización:** Las herramientas modernas (Docker, AWS, Jenkins) se controlan programáticamente mediante APIs.

## 1.4 Habilidades DevOps

### 1.4.1 IDEs vs Editores de Código
Un entorno de desarrollo es la herramienta principal del ingeniero. Es crucial entender la diferencia entre un IDE completo y un editor de código moderno.

| Característica | IDE (Entorno de Desarrollo Integrado) | Editor de Código |
| :--- | :--- | :--- |
| **Definición** | Suite completa que incluye compilador, depurador y herramientas de construcción integradas profundamente. | Editor de texto avanzado, ligero y altamente extensible mediante plugins. |
| **Rendimiento** | Pesado, consume muchos recursos (RAM/CPU). | Ligero, inicio rápido y bajo consumo. |
| **Configuración** | "Baterías incluidas", listo para compilar lenguajes complejos. | Modular, tú instalas solo lo que necesitas. |
| **Ejemplos** | IntelliJ IDEA, Eclipse, Visual Studio (Enterprise). | **Visual Studio Code**, Sublime Text, Vim. |
| **Mejor uso** | Java, C#, Desarrollo Android/iOS nativo. | Web (JS/TS), Python, Scripting, **DevOps**. |

### 1.4.2 Visual Studio Code (VS Code)
Es actualmente el estándar de la industria para desarrollo Web y DevOps. Creado por Microsoft, es gratuito, de código abierto y corre en Windows, Linux y Mac.
*   **¿Por qué usarlo?**
    *   **Terminal Integrada:** Permite ejecutar comandos de Linux/Git sin salir del editor.
    *   **Ecosistema:** Tiene la tienda de extensiones más grande del mundo.
    *   **Soporte Nativo:** Excelente integración con TypeScript, Node.js y Git.

### 1.4.3 Extensiones de VS Code
Para trabajar profesionalmente, transformamos VS Code en un entorno potente usando extensiones. Las esenciales para este curso son:

1.  **Prettier:** Formatea el código automáticamente para que siempre se vea limpio y ordenado.
2.  **ESLint:** Encuentra errores en el código JavaScript/TypeScript antes de ejecutarlo.
3.  **Docker:** Facilita la gestión de contenedores e imágenes desde el editor.
4.  **GitLens:** Superpoderes para Git (ver quién editó cada línea de código y cuándo).
5.  **Thunder Client / Postman:** Para probar APIs directamente desde VS Code sin salir de la ventana.

## 1.5 Proyecto Integrador
El objetivo final es construir una aplicación **Full Stack** que integre todos los conceptos:
*   **Frontend:** React/Angular consumiendo datos.
*   **Backend:** API REST Node.js/Express sirviendo datos.
*   **Base de Datos:** Persistencia real.
*   **DevOps:** Todo el código versionado en GitHub y listo para desplegarse.
