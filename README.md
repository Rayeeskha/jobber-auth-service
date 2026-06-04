# 🔐 Authentication Microservice Service

A scalable **Authentication Microservice** built with **Node.js**, responsible for user registration, authentication, authorization, and event-driven communication within the Jobber microservices ecosystem.

---

## 🚀 Overview

The Authentication Service manages user accounts and authentication workflows. When a new user registers, the service creates the account and automatically publishes an event to the Users Service to create the corresponding buyer profile.

The service follows an **event-driven architecture** using RabbitMQ and provides centralized error logging through Elasticsearch and Kibana.

---

## ✨ Features

### 👤 User Registration & Authentication

- User account creation and management
- Secure authentication using JWT
- Password hashing and validation
- Session and token management

### 📨 Event-Driven Communication

- Publishes events to RabbitMQ after successful user registration
- Automatically creates buyer records in the Users Service
- Decoupled communication between microservices

### 🗄️ Database Management

- MySQL database integration
- ORM support using Sequelize
- Database migrations and model management

### 📊 Logging & Monitoring

- Application and error logs stored in Elasticsearch
- Log monitoring and visualization through Kibana
- Centralized error tracking across services

### 🌱 Seed Data Generation

- Faker integration for generating test and seed data
- Useful for development and testing environments

---

## 🏗️ Tech Stack

- Node.js
- Express.js
- TypeScript
- RabbitMQ
- Elasticsearch
- Kibana
- MySQL
- Sequelize ORM
- JSON Web Token (JWT)
- Faker
- Docker

---

## 🔄 Service Workflow

1. User submits registration request
2. Authentication Service validates user data
3. User account is created in MySQL
4. JWT token is generated
5. Registration event is published to RabbitMQ
6. Users Service consumes the event
7. Buyer profile is created in MongoDB
8. Logs are stored in Elasticsearch
9. Logs are visualized through Kibana

---

## 📦 Setup Instructions

### 1️⃣ Clone the Repository

```bash
git clone <your-repository-url>
cd 3-auth-service
```

---

### 2️⃣ Configure Shared Library

Ensure your shared library is already published.

Copy the `.npmrc` file from your shared library project and update:

```ini
//npm.pkg.github.com/:_authToken=<YOUR_PERSONAL_ACCESS_TOKEN>
```

Replace all references of:

```text
@rayeeskha/jobber-shared
```

with your own shared library package name if applicable.

---

### 3️⃣ Install Dependencies

```bash
npm install
```

---

### 4️⃣ Configure Environment Variables

Copy:

```text
.env.dev
```

to:

```text
.env
```

Configure the required environment variables.

#### Cloudinary Configuration

Create an account at:

```text
https://cloudinary.com
```

Add the following values to your `.env` file:

```env
CLOUD_NAME=
CLOUD_API_KEY=
CLOUD_API_SECRET=
```

#### JWT Configuration

Generate secure values for:

```env
JWT_TOKEN=
GATEWAY_JWT_TOKEN=
```

> Ensure the same JWT values are used across all services that require authentication.

---

### 5️⃣ Start the Service

```bash
npm run dev
```

---

## ⚙️ Environment Variables

Example configuration:

```env
PORT=4002

CLIENT_URL=http://localhost:3000

MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_USER=root
MYSQL_PASSWORD=password
MYSQL_DATABASE=jobber_auth

RABBITMQ_ENDPOINT=amqp://localhost

ELASTIC_SEARCH_URL=http://localhost:9200

JWT_TOKEN=
GATEWAY_JWT_TOKEN=

CLOUD_NAME=
CLOUD_API_KEY=
CLOUD_API_SECRET=
```

---

## 🐳 Push Docker Image to Docker Hub

This section explains how to build, tag, and publish the Authentication Service Docker image to Docker Hub.

---

### 📋 Prerequisites

Before proceeding, ensure that:

- Docker Desktop is installed and running
- You have access to Docker Hub
- A valid GitHub Packages `NPM_TOKEN` is available
- Docker Hub login credentials are available

---

### 🔐 Step 1: Login to Docker Hub

```bash
docker login
```

---

### 🏗️ Step 2: Build Docker Image

```bash
docker build --build-arg NPM_TOKEN=<YOUR_GITHUB_TOKEN> -t rayeeskhandev/jobber-auth .
```

Example:

```bash
docker build --build-arg NPM_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxx -t rayeeskhandev/jobber-auth .
```

---

### 🏷️ Step 3: Tag Docker Image

```bash
docker tag rayeeskhandev/jobber-auth rayeeskhandev/jobber-auth:stable
```

Verify the image:

```bash
docker images
```

---

### 🚀 Step 4: Push Docker Image

```bash
docker push rayeeskhandev/jobber-auth:stable
```

---

### ⚡ Quick Commands

```bash
# Login
docker login

# Build Image
docker build --build-arg NPM_TOKEN=<YOUR_GITHUB_TOKEN> -t rayeeskhandev/jobber-auth .

# Tag Image
docker tag rayeeskhandev/jobber-auth rayeeskhandev/jobber-auth:stable

# Push Image
docker push rayeeskhandev/jobber-auth:stable
```

---

## 📁 Project Structure

```text
src/
├── controllers/
├── services/
├── routes/
├── queues/
├── database/
├── seeds/
├── helpers/
├── app.ts
└── server.ts
```

---

## 📊 Monitoring Services

| Service             | URL                    | Description          |
| ------------------- | ---------------------- | -------------------- |
| RabbitMQ Management | http://localhost:15672 | Queue Monitoring     |
| Elasticsearch       | http://localhost:9200  | Log Storage & Search |
| Kibana              | http://localhost:5601  | Log Visualization    |
| Cloudinary          | https://cloudinary.com | Image Storage        |

---

## 🧠 Key Highlights

- JWT-based authentication and authorization
- Event-driven architecture with RabbitMQ
- MySQL database integration using Sequelize
- Centralized logging with Elasticsearch
- Real-time monitoring through Kibana
- Cloudinary image management
- Dockerized deployment
- Scalable microservice architecture
