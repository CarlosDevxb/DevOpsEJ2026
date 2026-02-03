# Unidad 4: Docker y Contenedores

Docker revolucionó el desarrollo de software al solucionar el eterno problema: *"En mi máquina funciona, pero en el servidor no"*. Es la herramienta estándar para empaquetar y distribuir aplicaciones modernas.

## 4.1 ¿Qué es un Contenedor?
Un contenedor es una unidad de software estándar que empaqueta el código y todas sus dependencias (librerías, configuraciones) para que la aplicación se ejecute de manera rápida y confiable en cualquier entorno.

*   **Contenedores vs Máquinas Virtuales (VM):**
    *   **VM:** Virtualiza el hardware. Cada VM tiene su propio Sistema Operativo completo (pesado, lento de iniciar, ocupa GBs).
    *   **Contenedor:** Virtualiza el Sistema Operativo. Comparte el núcleo (kernel) del host, pero aísla los procesos. Son ligeros (MBs) y arrancan en milisegundos.

## 4.2 Conceptos Fundamentales
Para entender Docker, hay que distinguir tres elementos clave:

1.  **Imagen (Image):** Es el "plano" o la plantilla de solo lectura. Contiene el código congelado listo para usarse. (Analogía: Una Clase en POO).
2.  **Contenedor (Container):** Es la instancia ejecutable de una imagen. Es lo que realmente "corre". (Analogía: Un Objeto en POO).
3.  **Docker Hub:** Es el registro público en la nube (como GitHub pero para binarios) donde se almacenan y comparten imágenes oficiales (Node, Python, MySQL, etc.).

## 4.3 El Dockerfile
Es un archivo de texto simple (sin extensión) que contiene las instrucciones paso a paso para construir una Imagen Docker. Es la "receta de cocina" de tu infraestructura.

**Ejemplo de Dockerfile para una app Node.js:**
```dockerfile
# 1. Imagen base (el SO mínimo y entorno)
FROM node:18-alpine

# 2. Directorio de trabajo dentro del contenedor
WORKDIR /app

# 3. Copiar archivos de dependencias primero (para aprovechar caché)
COPY package.json .

# 4. Instalar dependencias
RUN npm install

# 5. Copiar el resto del código fuente
COPY . .

# 6. Exponer el puerto donde corre la app
EXPOSE 3000

# 7. Comando para iniciar la app al arrancar el contenedor
CMD ["npm", "start"]
```

## 4.4 Comandos Esenciales
La CLI de Docker es tu herramienta principal para gestionar el ciclo de vida de los contenedores.

*   **Construir:** `docker build -t nombre-app .` (Lee el Dockerfile y crea una imagen).
*   **Ejecutar:** `docker run -p 3000:3000 nombre-app` (Arranca un contenedor mapeando el puerto 3000 de tu PC al 3000 del contenedor).
*   **Listar:** `docker ps` (Muestra los contenedores que están corriendo actualmente).
*   **Detener:** `docker stop [ID_CONTENEDOR]` (Detiene la ejecución de forma segura).
*   **Logs:** `docker logs [ID_CONTENEDOR]` (Muestra la salida de consola de la aplicación dentro del contenedor).

## 4.5 Docker Compose
En el mundo real, las aplicaciones tienen múltiples partes (Frontend + Backend + Base de Datos). Gestionar cada contenedor por separado es tedioso.

*   **Definición:** Herramienta para definir y ejecutar aplicaciones Docker de múltiples contenedores.
*   **Archivo `docker-compose.yml`:** Un archivo YAML donde declaras todos los servicios que tu app necesita.
*   **Comando Mágico:** `docker-compose up`
    *   Este comando descarga las imágenes, crea las redes, configura los volúmenes y levanta toda tu infraestructura con una sola línea.
    *   Ideal para entornos de desarrollo local.