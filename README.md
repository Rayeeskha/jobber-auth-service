## API Gateway Microservice

### 📌 Overview

The API Gateway Microservice is responsible for handling all incoming requests from the frontend and routing them to appropriate backend services. It acts as a central entry point in the microservices architecture.

---

### ⚙️ Responsibilities

- Handles all client requests before reaching other microservices
- Implements **Request/Response communication pattern**
- Performs **request validation**
- Manages authentication using **JSON Web Token (JWT)**
- Adds JWT to cookie sessions and validates incoming tokens
- Aggregates and forwards client-side errors from downstream services
- Sends server-side errors to Elasticsearch for logging and monitoring

---

### 📊 Logging & Monitoring

- Server-side errors are logged in **Elasticsearch**
- Logs can be visualized and monitored using **Kibana**

---

### 🧰 Tech Stack

- Node.js
- Express.js
- TypeScript
- Axios
- Redis
- Elasticsearch
- JSON Web Token (JWT)
- Socket.IO
- Socket.IO Client
- Shared Library (Custom NPM Package)

---

### 🗄️ Database Management

- This project uses **TablePlus** as a database GUI tool
- It helps in:
  - Managing databases visually
  - Running SQL queries
  - Debugging and inspecting data

- You can also use alternatives like phpMyAdmin , DBeaver or workbench

---

### 📦 Setup Instructions

1. **Shared Library**
   - Ensure your shared library is published
   - Replace all occurrences of `@rayeeskha/jobber-shared` with your own package

2. **NPM Configuration**
   - Copy `.npmrc` file
   - Replace `${NPM_TOKEN}` with your personal access token

3. **Environment Variables**
   - Copy `.env.dev` → `.env`
   - Update:
     - `DATABASE_HOST` → your local IP
     - `GATEWAY_JWT_TOKEN` and `JWT_TOKEN` → generate secure tokens

4. **Install Dependencies**

   ```bash
   npm install
   ```

5. **Run Service**

   ```bash
   npm run dev
   ```

---

### 🐳 Docker Setup

1. Build Image:

   ```bash
   docker build -t <your-dockerhub-username>/jobber-gateway .
   ```

2. Tag Image:

   ```bash
   docker tag <your-dockerhub-username>/jobber-gateway <your-dockerhub-username>/jobber-gateway:stable
   ```

3. Push to Docker Hub:

   ```bash
   docker push <your-dockerhub-username>/jobber-gateway:stable
   ```

---

### 💡 Notes

- Ensure all microservices use the same JWT secret keys
- Update Node.js version in `Dockerfile` if required
- Maintain consistency across environments (dev, staging, production)

---

### 🚀 Summary

This API Gateway serves as the backbone of the microservices architecture, ensuring secure communication, centralized error handling, and efficient request routing across services.
