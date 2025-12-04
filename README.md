# 📝 Blogify - Full Stack Blog Application

<p align="center">
  <img src="https://img.shields.io/badge/Java-17-orange?style=for-the-badge&logo=java" alt="Java">
  <img src="https://img.shields.io/badge/Spring_Boot-3.4.2-green?style=for-the-badge&logo=spring-boot" alt="Spring Boot">
  <img src="https://img.shields.io/badge/React-19.0-blue?style=for-the-badge&logo=react" alt="React">
  <img src="https://img.shields.io/badge/MySQL-8.0-blue?style=for-the-badge&logo=mysql" alt="MySQL">
  <img src="https://img.shields.io/badge/Tailwind_CSS-3.4-38B2AC?style=for-the-badge&logo=tailwind-css" alt="Tailwind">
</p>

<p align="center">
  A modern, full-featured blogging platform with user authentication, admin dashboard, and social features.
</p>

---

## 🌟 Features

### 👤 User Features
- ✅ User Registration & Login (JWT Authentication)
- ✅ Create, Edit, Delete Blog Posts
- ✅ Upload Images for Posts
- ✅ Like & Comment on Posts
- ✅ User Profile Management
- ✅ View Liked Posts

### 🔐 Admin Features
- ✅ Admin Dashboard with Statistics
- ✅ User Management (View, Edit, Delete)
- ✅ Post & Comment Moderation
- ✅ Activity Monitoring

---

## 🛠️ Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Frontend** | React 19, Vite, Tailwind CSS, Axios, Framer Motion |
| **Backend** | Java 17, Spring Boot 3.4, Spring Security, Spring Data JPA |
| **Database** | MySQL 8, Hibernate ORM |
| **Auth** | JWT, BCrypt |
| **Tools** | Maven, Git, Docker |

---

## 📁 Project Structure

```
Blogify/
├── blog-application/          # Spring Boot Backend
│   ├── src/main/java/
│   │   └── com/project/blog_application/
│   │       ├── controllers/   # REST API Controllers
│   │       ├── services/      # Business Logic
│   │       ├── entities/      # JPA Entities
│   │       ├── repository/    # Data Repositories
│   │       ├── DTO/           # Data Transfer Objects
│   │       ├── config/        # Security & App Config
│   │       └── security/      # JWT Utilities
│   └── pom.xml
│
├── blog-frontend/             # React Frontend
│   ├── src/
│   │   ├── components/        # Reusable UI Components
│   │   ├── pages/             # Page Components
│   │   ├── layouts/           # Layout Components
│   │   └── App.jsx
│   └── package.json
│
└── README.md
```

---

## 🚀 Quick Start

### Prerequisites
- Java 17+
- Node.js 18+
- MySQL 8+
- Maven 3.8+

### 1️⃣ Database Setup
```bash
mysql -u root -p
CREATE DATABASE blog_db;
```

### 2️⃣ Backend Setup
```bash
cd blog-application
# Update database credentials in src/main/resources/application.properties
mvn spring-boot:run
```

### 3️⃣ Frontend Setup
```bash
cd blog-frontend
npm install
npm run dev
```

### 4️⃣ Access the App
- **Frontend:** http://localhost:5173
- **Backend API:** http://localhost:8080

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/signup` | Register new user |
| POST | `/api/auth/login` | User login |
| GET | `/api/posts` | Get all posts |
| POST | `/api/posts` | Create post |
| GET | `/api/posts/{id}` | Get post by ID |
| PUT | `/api/posts/{id}` | Update post |
| DELETE | `/api/posts/{id}` | Delete post |
| POST | `/api/comments` | Add comment |
| POST | `/api/likes/toggle` | Like/Unlike post |
| GET | `/api/users/me` | Get current user |
| GET | `/api/dashboard/stats` | Admin statistics |

---

## 🔐 Security

- **JWT Authentication** - Stateless token-based auth
- **BCrypt Password Hashing** - Secure password storage
- **Role-Based Access** - USER and ADMIN roles
- **CORS Configuration** - Frontend origin allowed

---

## ⚡ Performance Optimizations

- 🚀 Consolidated Dashboard API (75% fewer requests)
- 🚀 Database Indexing on foreign keys
- 🚀 GZIP Compression enabled
- 🚀 React Lazy Loading & Code Splitting
- 🚀 Response Caching

---

## 🐳 Docker Support

```bash
# Build backend image
cd blog-application
docker build -t blogify-backend .

# Run container
docker run -p 8080:8080 blogify-backend
```

---

## 📄 Documentation

- [Project Summary](./PROJECT_SUMMARY.md) - Detailed project documentation
- [How to Run](./HOW_TO_RUN.md) - Step-by-step running instructions
- [Backend Requirements](./BACKEND_REQUIREMENTS.md) - Maven dependencies
- [Frontend Requirements](./FRONTEND_REQUIREMENTS.md) - npm packages
- [Performance Optimizations](./PERFORMANCE_OPTIMIZATIONS.md) - Optimization details

---

## 👨‍💻 Author

**Sumanshu Arora**

---

## 📜 License

This project is licensed under the MIT License.

---

<p align="center">
  ⭐ Star this repo if you find it helpful!
</p>