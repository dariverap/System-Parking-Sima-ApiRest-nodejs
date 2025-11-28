🇪🇸 Versión en Español: [Leer aquí](./README.es.md)

<div align="center">

# SIMA Parking API

![NodeJS](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-000000?style=flat-square&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Clever Cloud](https://img.shields.io/badge/Clever_Cloud-202020?style=flat-square&logo=clevercloud&logoColor=white)

</div>

<br />

### Created by Diego Rivera

## 📋 Executive Summary

The **SIMA Parking API** is the backend backbone of the SIMA Parking ecosystem. It is a lightweight, high-performance RESTful service designed to handle data persistence, authentication, and business logic for the mobile application.

It manages critical operations such as real-time vehicle entry/exit registration, complex tariff calculations, role-based user authentication, and parking slot availability tracking. It serves as the bridge between the Android client and the cloud-hosted MySQL database.

## 🔗 Related Repositories

*   📱 **Mobile Client:** [SIMA Parking Android App](../app) *(Link to your mobile project)*

## ✨ Key Features

*   **RESTful Architecture:** Provides standard HTTP endpoints (GET, POST, PUT, DELETE) for resource management.
*   **Database Connection Pooling:** Utilizes `mysql.createPool` for efficient and resilient database interactions, handling multiple concurrent connections.
*   **Authentication Service:** Handles user login credentials and returns user objects with role definitions.
*   **Parking Logic:** 
    *   Calculates parking duration and fees based on entry/exit timestamps.
    *   Manages the state of parking spots (Available/Occupied).
*   **CORS Enabled:** Configured to accept requests from various origins, facilitating testing and integration.

## 🏗️ Architecture

The API follows a straightforward **Monolithic MVC-style** structure:

1.  **Server Entry:** `index.js` initializes the Express app and middleware.
2.  **Routing & Logic:** Routes are defined directly mapping HTTP verbs to database queries.
3.  **Data Layer:** Raw SQL queries interact with the MySQL database hosted on Clever Cloud.

## 🛠️ Tech Stack

*   **Runtime:** Node.js
*   **Framework:** Express.js
*   **Database:** MySQL (Cloud Hosted)
*   **Dependencies:** `mysql`, `body-parser`
*   **Dev Tools:** `nodemon` for hot-reloading.

## 🔌 API Endpoints (Snapshot)

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/login` | Authenticate user credentials. |
| `GET` | `/usuarios` | Retrieve all registered users. |
| `POST` | `/registro/add` | Register a vehicle entry (Transactions & User status update). |
| `GET` | `/registro/:patente` | Find active parking records by license plate. |
| `PUT` | `/registro2/update/:id` | Process vehicle exit and calculate costs. |
| `GET` | `/espacios` | List available parking spots. |
| `GET` | `/tarifas` | Retrieve current pricing models. |

## 🚀 Installation & Setup

### Prerequisites
*   Node.js (v14 or higher)
*   npm (Node Package Manager)

### Steps

1.  **Install Dependencies**
    ```bash
    npm install
    ```

2.  **Environment Configuration**
    Ensure the database credentials in `index.js` are valid or move them to a `.env` file for security.

3.  **Run Development Server**
    ```bash
    npm run dev
    ```
    *Server runs on port defined in `PORT` env or defaults to 3306.*

4.  **Production Start**
    ```bash
    npm start
    ```

---
*© 2023 Diego Rivera. All Rights Reserved.*