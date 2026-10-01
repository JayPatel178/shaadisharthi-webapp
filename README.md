# 💍 ShaadiSharthi

**ShaadiSharthi** is a full-stack wedding services platform that connects **Customers, Service Providers, and Admins**. Customers can discover and book wedding services, providers can manage their services and bookings, and admins can manage users, providers, queries, and analytics.

The complete application is containerized using **Docker & Docker Compose** and uses **Nginx** as a reverse proxy.

---

## 🚀 Features

### Customer

* Register/Login
* Search and filter wedding services
* View service details
* Book and manage services
* Reviews and notifications
* Real-time booking notifications

### Service Provider

* Provider registration and authentication
* Manage services (CRUD)
* Upload service media using Cloudinary
* Manage booking requests
* Provider dashboard and statistics

### Admin

* Secure admin authentication
* Role-based access control
* Manage customers and providers
* Approve service providers
* Manage support queries
* Dashboard analytics
* TOTP-based 2FA

---

## 🛠️ Tech Stack

### Frontend

* **Customer:** Next.js, TypeScript, Tailwind CSS
* **Provider:** Angular, TypeScript, Bootstrap
* **Admin:** React, JavaScript, Bootstrap

### Backend

* **Java Servlets & JSP**
* **Apache Tomcat**
* **JDBC**
* **MySQL**
* **HikariCP**
* **JWT Authentication**
* **WebSockets**
* **JavaMail**
* **SLF4J + Logback**

### DevOps & Services

* Docker & Docker Compose
* Nginx
* Cloudinary
* AWS EC2
* Let's Encrypt / Certbot

---

## 🏗️ Architecture

```text
Customer (Next.js) ─┐
Provider (Angular) ─┼──> Nginx ──> Java Servlets ──> MySQL
Admin (React) ──────┘              │
                                   ├── Cloudinary
                                   ├── Email
                                   └── WebSocket
```

---

# ⚙️ Local Setup

## 1. Prerequisites

Install:

* Git
* Docker Desktop
* Node.js & npm
* Angular CLI

```bash
npm install -g @angular/cli
```

---

## 2. Clone Repository

```bash
git clone https://github.com/JayPatel1178/shaadisharthi-webapp.git

cd shaadisharthi-webapp
```

---

## 3. Configure Environment Variables

Create `.env` in the **project root**:

```env
# MySQL
MYSQL_ROOT_PASSWORD=your_root_password
MYSQL_DATABASE=shaadisharthi
MYSQL_USER=appuser
MYSQL_PASSWORD=apppass

# Database
DB_URL=jdbc:mysql://shaadi_mysql:3306/shaadisharthi
DB_USERNAME=appuser
DB_PASSWORD=apppass
DB_NAME=shaadisharthi
DB_DRIVER=com.mysql.cj.jdbc.Driver

# JWT
JWT_SECRET_KEY=your_long_secret_key
JWT_RESET_SECRET_KEY=your_reset_secret_key

# Email
EMAIL_FROM=your_email
EMAIL_PASSWORD=your_email_app_password

# Application
APP_BASE_URL=http://localhost

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# CORS
ADMIN_ALLOWED_ORIGINS=http://localhost
SERVICEPROVIDER_ALLOWED_ORIGINS=http://localhost
CUSTOMER_ALLOWED_ORIGINS=http://localhost
```

Add the required **role-mapping variables** used by the backend to the same `.env` file.

> ⚠️ Never commit real passwords, JWT secrets, email passwords, or Cloudinary secrets to Git.

---

## 4. Customer Environment

Create:

`shaadisharthi-next/.env`

```env
NEXT_PUBLIC_API_URL=http://localhost:8080
NEXT_INTERNAL_API_URL=http://shaadisharthi-backend:8080
NEXT_PUBLIC_WEBSOCKET_API_URL=ws://localhost:8080/CustomerSocket
NODE_ENV=development
```

---

## 5. Admin Environment

Create:

`shaadisharthi-react/.env`

```env
REACT_APP_API_URL=http://localhost:8080
```

---

## 6. Provider Environment

Create:

`shaadisharthi-angular/src/environments/environment.ts`

```typescript
export const environment = {
  production: false,
  apiUrl: "http://localhost:8080",

  cloudinary: {
    cloudName: "your_cloudinary_cloud_name"
  },

  supportEmail: "support@shaadisharthi.com"
};
```

---

## 7. Start Application

Run from the project root:

```bash
docker compose up -d --build
```

Check containers:

```bash
docker compose ps
```

The backend may take some time to initialize on the first startup.

---

## 🌐 Local URLs

| Application | URL                       |
| ----------- | ------------------------- |
| Customer    | http://localhost/customer |
| Provider    | http://localhost/provider |
| Admin       | http://localhost/admin    |

---

## 🗄️ Database

MySQL runs automatically inside Docker.

Access MySQL:

```bash
docker compose exec mysql mysql -u appuser -p
```

Then:

```sql
USE shaadisharthi;
SHOW TABLES;
```

---

## 📋 Useful Commands

### View backend logs

```bash
docker compose logs -f shaadisharthi-backend
```

### Restart application

```bash
docker compose restart
```

### Stop application

```bash
docker compose down
```

### Rebuild

```bash
docker compose up -d --build
```

---

## 📁 Project Structure

```text
shaadisharthi-webapp/
│
├── shaadisharthi-next/       # Customer - Next.js
├── shaadisharthi-angular/   # Provider - Angular
├── shaadisharthi-react/     # Admin - React
├── shaadisharthi-backend/   # Backend - Java Servlets
├── nginx/                   # Nginx configuration
├── docker-compose.yml
├── deploy.sh
└── .env
```
---

## 📦 Individual Repositories

* **Customer:** https://github.com/JayPatel178/shaadisharthi-customer
* **Provider:** https://github.com/JayPatel178/shaadisharthi-provider
* **Admin:** https://github.com/JayPatel178/shaadisharthi-admin
* **Backend:** https://github.com/JayPatel178/shaadisharthi-backend

---

## 👨‍💻 Author

**Jay Patel** — Full-Stack Developer
Java • React • Angular • Next.js • MySQL • Docker

---

> Built for portfolio and educational purposes.
