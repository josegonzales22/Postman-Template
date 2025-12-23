# 🚀 Postman Template - Script-Based Architecture

Este repositorio contiene una colección de Postman diseñada como un framework de demostración para pruebas de API automatizadas. Esta colección utiliza una arquitectura basada íntegramente en Scripts (Pre-request y Post-response) para gestionar el flujo de datos y las validaciones de forma autónoma.


## 🏗️ Arquitectura de la Colección

La colección está diseñada para ser independiente, gestionando su propio ciclo de vida de datos mediante scripts de JavaScript:

* 🔐 Autenticación Dinámica: El script de "Auth" extrae automáticamente el `accessToken` y lo guarda en variables de colección para las siguientes peticiones.
* 💉 Inyección Automática de Headers: Mediante scripts de Pre-request, se inyecta el header `Authorization: Bearer` dinámicamente, asegurando que el token esté siempre actualizado.
* 🔗 Encadenamiento de Peticiones (Chaining): Uso de `pm.sendRequest` para realizar consultas intermedias y obtener IDs aleatorios, permitiendo que las pruebas de PUT y DELETE sean dinámicas y no dependan de datos estáticos.
* 🧪 Suite de Pruebas Integrada: Cada petición cuenta con validaciones de:
    - Status Code (200/201).
    - Performance (Response time < 1000ms).
    - Validación de estructura JSON y Content-Type.
    - Verificación de body no vacío.


## 📦 Características Principales

* ✔️ Zero Configuration: No requiere archivos de "Environment". Todo se autogestiona en las variables de la colección.
* ✔️ Altamente Compatible con Newman: Diseñado para funcionar perfectamente en CLI y entornos de CI/CD.
* ✔️ Lógica Inteligente: Selección aleatoria de recursos para pruebas más realistas.
* ✔️ Feedback en Consola: Incluye logs detallados (`console.log`) para monitorear el flujo de datos y posibles errores de procesamiento.


## 🛠️ Tecnologías Usadas

| Herramienta | Uso |
|-----------|-----|
| Postman | Automatización y diseño de peticiones |
| Newman | Ejecución vía comandos (CLI) |
| JavaScript | Lógica de scripts (Pre-request/Tests) |
| DummyJSON API | API de pruebas para la demostración |


## ▶️ Ejecución con Newman

Para ejecutar esta colección de forma automatizada:

1. Instalar Newman:
   npm install -g newman

2. Ejecutar la colección:
````bash
   newman run <nombre>.postman_collection.json
````


## 📄 Flujo de Endpoints

1. Login (POST): Obtención de credenciales.
2. Get User (GET): Validación de sesión activa.
3. CRUD de Productos:
    - Listar con filtros.
    - Crear nuevo producto.
    - Actualizar producto (seleccionado aleatoriamente vía script).
    - Eliminar producto (usando el ID obtenido dinámicamente).


## ⭐ Conclusión

Este template demuestra cómo crear una suite de pruebas de API que sea portátil, inteligente y capaz de manejar flujos complejos de datos sin intervención manual.


## Licencia
Este proyecto utiliza la [Licencia MIT](https://opensource.org/licenses/MIT).