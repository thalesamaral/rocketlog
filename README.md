# 🚀 RocketLog

RESTful API for **package delivery management**, developed with **Node.js, TypeScript and Prisma**, focusing on **clean architecture, authentication, data consistency and scalability**.

This project simulates a real-world delivery system, handling users, deliveries and delivery logs with role-based access and secure authentication.

---

## 📋 Overview

**RocketLog** is a backend application designed to manage package deliveries, allowing:

- user registration and authentication
- creation and tracking of deliveries
- delivery status updates
- detailed delivery logs
- role-based access control (customer / seller)

The project emphasizes **API design**, **business rules**, **database modeling**, and **modern backend practices**.

---

## 🛠️ Technologies Used

- **Node.js** — JavaScript runtime
- **TypeScript** — Static typing and code safety
- **Express.js** — REST API framework
- **Prisma ORM** — Database access and schema management
- **PostgreSQL** — Relational database
- **JWT** — Authentication and authorization
- **bcrypt** — Password hashing
- **Zod** — Request data validation
- **Jest** — Unit testing
- **Docker** — Containerized database environment

---

## 🏗️ Project Structure

The application follows a modular and organized structure, separating responsibilities clearly:

```
rocketlog/
├── src/
│   ├── controllers/          # Request handling and business logic
│   ├── middlewares/          # Authentication and error handling
│   ├── routes/               # API route definitions
│   ├── database/             # Database connection
│   ├── configs/              # Application configurations (auth)
│   ├── utils/                # Shared utilities (AppError)
│   ├── tests/                # Unit tests
│   ├── app.ts                # Express app configuration
│   └── server.ts             # HTTP server bootstrap
├── prisma/
│   ├── schema.prisma         # Database schema
│   └── migrations/           # Database migrations
├── types/                    # Shared TypeScript types
├── docker-compose.yml        # Docker services configuration
└── package.json              # Project dependencies and scripts
```

---

## 🚀 Running the Project

### Prerequisites

- Node.js **18+**
- Docker & Docker Compose
- npm or yarn

---

### 1. Clone the repository

```bash
git clone <repository-url>
cd rocketlog
```

### 2. Install dependencies

```bash
npm install
```

### 3. Environment variables

Create a `.env` file:

```
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/rocketlog"
JWT_SECRET="your-secret-key-here"
PORT=3333
```

### 4. Start PostgreSQL with Docker

```bash
docker-compose up -d
```

### 5. Run database migrations

```bash
npx prisma migrate dev
```

### 6. Start the server

```bash
npm run dev
```

Server available at:

`http://localhost:3333`

---

## 📚 API Endpoints

### 🔐 Authentication

**POST `/sessions`** — Create a user session (login)

```json
{
  "email": "user@example.com",
  "password": "123456"
}
```

---

### 👤 Users

**POST `/users`** — Create a new user

```json
{
  "name": "Bob Silva",
  "email": "bob@example.com",
  "password": "123456"
}
```

---

### 📦 Deliveries

**POST `/deliveries`** — Create a delivery (authenticated)

```json
{
  "description": "Electronics delivery"
}
```

**GET `/deliveries`** — List authenticated user deliveries

**PUT `/deliveries/:id/status`** — Update delivery status

```json
{
  "status": "shipped"
}
```

---

### 📝 Delivery Logs

**POST `/delivery-logs`** — Create a delivery log entry

```json
{
  "description": "Package collected at warehouse",
  "deliveryId": "delivery-uuid"
}
```

**GET `/delivery-logs/:deliveryId`** — List delivery logs

---

## 🧪 Tests

```bash
npm test        # run all tests
npm run test:dev # watch mode
```

---

## 🔧 Useful Scripts

- `npm run dev` — Development server
- `npm run test:dev` — Tests in watch mode
- `npx prisma studio` — Visual database management
- `npx prisma migrate dev` — Run migrations
- `npx prisma generate` — Generate Prisma client

---

## 🐳 Docker

This project uses Docker to provide a local PostgreSQL environment:

```bash
docker-compose up -d
```

---

## 📝 Key Features

- JWT-based authentication
- Secure password hashing
- Role-based access (customer / seller)
- Delivery and delivery log management
- Centralized error handling
- Input validation with Zod
- Database migrations with Prisma
- Unit testing with Jest

---
