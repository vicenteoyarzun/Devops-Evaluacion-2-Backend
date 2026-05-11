# DevOps - Evaluación Parcial N°2 (Innovatech Chile)

[cite_start]Este repositorio contiene el Backend para el proyecto de **Innovatech Chile**, enfocado en la contenedorización y el despliegue automatizado en la nube (AWS).

## 🐳 Contenedorización

El proyecto ha sido dockerizado siguiendo las mejores prácticas exigidas en la evaluación:
* [cite_start]**Multi-stage Build:** El Dockerfile utiliza múltiples etapas para generar una imagen ligera y optimizada[cite: 158, 220].
* [cite_start]**Seguridad:** Se configuró la ejecución con un **usuario no root** para minimizar riesgos de seguridad[cite: 220, 258].
* [cite_start]**Docker Compose:** Se incluye un archivo `docker-compose.yml` que orquesta el backend, la base de datos y sus redes internas[cite: 159, 221, 268].

## 💾 Persistencia de Datos

Para garantizar la continuidad operativa de la empresa, se implementó persistencia de datos:
* [cite_start]**Volúmenes:** Se utilizan volúmenes de Docker para asegurar que la información de la base de datos no se pierda al reiniciar los contenedores[cite: 162, 163].
* [cite_start]**Justificación:** Se prefieren los **Named Volumes** por su facilidad de gestión dentro de la infraestructura de AWS[cite: 164, 228].

## 🚀 Pipeline CI/CD (GitHub Actions)

[cite_start]El repositorio incluye un flujo de automatización completo que se dispara con cada `push` en la rama **deploy**[cite: 143, 173]:

1. [cite_start]**Build & Push:** Construye la imagen de Docker y la publica en el registro de contenedores (Docker Hub o ECR)[cite: 169, 170, 233].
2. [cite_start]**Deploy Automático:** El pipeline despliega la versión actualizada directamente en la instancia **AWS EC2**[cite: 171, 241].
3. [cite_start]**Gestión de Secrets:** Se utilizan **GitHub Secrets** para manejar de forma segura las credenciales de AWS y variables de entorno[cite: 172, 243, 275].

## 🛠️ Instrucciones de Uso Local

1. Clonar este repositorio.
2. Configurar las variables de entorno en un archivo `.env`.
3. Levantar los servicios con el siguiente comando:
   ```bash
   docker-compose up --build
