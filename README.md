# DevSecOps Pipeline

Este proyecto documenta mi primer pipeline enfocado en DevSecOps, integrando herramientas como Docker, GitHub Actions, SonarQube y Trivy.

Utiliza la metodología "Shift-Left", la cual establece que la búsqueda de vulnerabilidades y las pruebas de seguridad deben iniciar desde el momento en que se escribe el código y se envía a Git, mucho antes de llegar a producción.

Siguiendo esta metodología, la secuencia de ejecución del pipeline es:
* **Git:** Descarga el código fuente al detectar un nuevo cambio.
* **SonarQube:** Analiza el código buscando vulnerabilidades antes de compilar.
* **Docker:** Construye la imagen de la aplicación solo si el código aprueba el análisis.
* **Trivy:** Escanea el sistema operativo y las dependencias del contenedor en busca de fallos de seguridad.
* **Docker Hub:** Publica la imagen final en el registro únicamente si Trivy certifica que es segura.

[![GitHub Actions](https://img.shields.io/github/actions/workflow/status/aleBarajasFlores/devsecops_pipeline/pipeline.yml)](https://github.com/aleBarajasFlores/devsecops_pipeline/actions)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=aleBarajasFlores_devsecops_pipeline&metric=bugs)](https://sonarcloud.io/summary/new_code?id=aleBarajasFlores_devsecops_pipeline)
[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=aleBarajasFlores_devsecops_pipeline&metric=vulnerabilities)](https://sonarcloud.io/summary/new_code?id=aleBarajasFlores_devsecops_pipeline)

Para prevenir la exposición de credenciales en texto plano, el proyecto utiliza las bóvedas criptográficas de GitHub Secrets para inyectar de forma segura los tokens de SonarCloud y Docker Hub. Asimismo, la infraestructura implementa el Principio del Menor Privilegio, garantizando que cada token cuente estrictamente con los accesos mínimos requeridos para ejecutar su fase correspondiente dentro de la automatización.
