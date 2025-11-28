🇺🇸 English Version: [Read here](./README.md)

<div align="center">

# API SIMA Parking

![NodeJS](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-000000?style=flat-square&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Clever Cloud](https://img.shields.io/badge/Clever_Cloud-202020?style=flat-square&logo=clevercloud&logoColor=white)

</div>

<br />

### Creado por Diego Rivera

## 📋 Resumen Ejecutivo

La **API SIMA Parking** es el núcleo backend del ecosistema SIMA Parking. Es un servicio RESTful ligero y de alto rendimiento diseñado para manejar la persistencia de datos, la autenticación y la lógica de negocio para la aplicación móvil.

Gestiona operaciones críticas como el registro de entrada/salida de vehículos en tiempo real, cálculos complejos de tarifas, autenticación de usuarios basada en roles y el seguimiento de la disponibilidad de plazas de aparcamiento. Actúa como el puente entre el cliente Android y la base de datos MySQL alojada en la nube.

## 🔗 Repositorios Relacionados

*   📱 **Cliente Móvil:** [App Android SIMA Parking](../app) *(Enlace a tu proyecto móvil)*

## ✨ Características Principales

*   **Arquitectura RESTful:** Proporciona endpoints HTTP estándar (GET, POST, PUT, DELETE) para la gestión de recursos.
*   **Pooling de Conexiones:** Utiliza `mysql.createPool` para interacciones eficientes y resilientes con la base de datos, manejando múltiples conexiones concurrentes.
*   **Servicio de Autenticación:** Gestiona credenciales de inicio de sesión y retorna objetos de usuario con definiciones de roles.
*   **Lógica de Estacionamiento:**
    *   Calcula la duración y tarifas del estacionamiento basándose en marcas de tiempo de entrada/salida.
    *   Gestiona el estado de los espacios (Disponible/Ocupado).
*   **CORS Habilitado:** Configurado para aceptar solicitudes desde varios orígenes, facilitando pruebas e integración.

## 🏗️ Arquitectura

La API sigue una estructura sencilla de estilo **Monolítico MVC**:

1.  **Entrada del Servidor:** `index.js` inicializa la app Express y los middleware.
2.  **Enrutamiento y Lógica:** Las rutas se definen mapeando directamente los verbos HTTP a consultas de base de datos.
3.  **Capa de Datos:** Consultas SQL nativas interactúan con la base de datos MySQL alojada en Clever Cloud.

## 🛠️ Stack Tecnológico

*   **Runtime:** Node.js
*   **Framework:** Express.js
*   **Base de Datos:** MySQL (Alojada en la Nube)
*   **Dependencias:** `mysql`, `body-parser`
*   **Herramientas Dev:** `nodemon` para recarga en caliente.

## 🔌 Endpoints de la API (Resumen)

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `POST` | `/login` | Autenticar credenciales de usuario. |
| `GET` | `/usuarios` | Obtener todos los usuarios registrados. |
| `POST` | `/registro/add` | Registrar entrada de vehículo (Transacción y actualización de estado). |
| `GET` | `/registro/:patente` | Buscar registros activos por placa. |
| `PUT` | `/registro2/update/:id` | Procesar salida de vehículo y calcular costos. |
| `GET` | `/espacios` | Listar espacios de estacionamiento disponibles. |
| `GET` | `/tarifas` | Obtener modelos de precios actuales. |

## 🚀 Instalación y Configuración

### Prerrequisitos
*   Node.js (v14 o superior)
*   npm (Node Package Manager)

### Pasos

1.  **Instalar Dependencias**
    ```bash
    npm install
    ```

2.  **Configuración de Entorno**
    Asegúrese de que las credenciales de la base de datos en `index.js` sean válidas o muévalas a un archivo `.env` para mayor seguridad.

3.  **Ejecutar Servidor de Desarrollo**
    ```bash
    npm run dev
    ```
    *El servidor corre en el puerto definido en la variable `PORT` o por defecto en 3306.*

4.  **Inicio en Producción**
    ```bash
    npm start
    ```

---
*© 2023 Diego Rivera. Todos los derechos reservados.*