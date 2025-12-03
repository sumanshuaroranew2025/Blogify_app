# Blogify - Complete Project Summary

## 📋 Table of Contents
1. [Project Overview](#project-overview)
2. [Technology Stack](#technology-stack)
3. [Project Architecture](#project-architecture)
4. [Backend Details](#backend-details)
5. [Frontend Details](#frontend-details)
6. [Database Schema](#database-schema)
7. [API Endpoints](#api-endpoints)
8. [Security Implementation](#security-implementation)
9. [Features](#features)
10. [Performance Optimizations](#performance-optimizations)

---

## 🎯 Project Overview

**Blogify** is a full-stack blogging platform that allows users to create, read, update, and delete blog posts. It features a modern React frontend with a robust Spring Boot backend, providing a complete blogging experience with user authentication, commenting system, likes functionality, and an admin dashboard for content management.

### What is Blogify?
Blogify is a comprehensive blog application designed for:
- **Content Creators**: Write and publish blog posts with image support
- **Readers**: Browse, read, like, and comment on blog posts
- **Administrators**: Manage users, posts, and comments through a dedicated admin panel

### What Does Blogify Do?
1. **User Management**: Registration, login, profile management with JWT authentication
2. **Blog Post Management**: Create, edit, delete blog posts with image uploads
3. **Social Features**: Like posts, comment on posts
4. **Admin Dashboard**: View statistics, manage users, posts, and comments
5. **Activity Tracking**: Monitor recent activities across the platform

---

## 🛠️ Technology Stack

### Backend (Java/Spring Boot)
| Technology | Version | Purpose |
|------------|---------|---------|
| Java | 17 | Programming Language |
| Spring Boot | 3.4.2 | Application Framework |
| Spring Security | Latest | Authentication & Authorization |
| Spring Data JPA | Latest | Database ORM |
| MySQL | 8.x | Relational Database |
| JWT (jjwt) | 0.11.5 | Token-based Authentication |
| Lombok | Latest | Boilerplate Code Reduction |
| BCrypt | Latest | Password Hashing |
| Logback | Latest | Logging |
| Maven | 3.8+ | Build Tool |

### Frontend (React/JavaScript)
| Technology | Version | Purpose |
|------------|---------|---------|
| React | 19.0.0 | UI Library |
| React Router DOM | 7.9.6 | Client-side Routing |
| Vite | 6.1.0 | Build Tool & Dev Server |
| Axios | 1.13.2 | HTTP Client |
| Tailwind CSS | 3.4.17 | Styling Framework |
| Framer Motion | 12.6.3 | Animations |
| Lucide React | 0.475.0 | Icons |
| React Hot Toast | 2.5.2 | Notifications |
| React Toastify | 11.0.5 | Toast Notifications |
| JWT Decode | 4.0.0 | JWT Token Parsing |
| Radix UI | 1.1.6 | UI Components |
| Google OAuth | 0.12.1 | Social Login |

---

## 🏗️ Project Architecture

```
Blogify-main/
├── blog-application/          # Spring Boot Backend
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/project/blog_application/
│   │   │   │   ├── BlogApplication.java          # Main Application Entry
│   │   │   │   ├── config/                       # Configuration Classes
│   │   │   │   │   ├── CacheConfig.java          # Caching Configuration
│   │   │   │   │   ├── CorsConfig.java           # CORS Settings
│   │   │   │   │   ├── SecurityConfig.java       # Security Configuration
│   │   │   │   │   ├── WebConfig.java            # Web Configuration
│   │   │   │   │   └── JwtAuthenticationFilter.java
│   │   │   │   ├── controllers/                  # REST Controllers
│   │   │   │   ├── DTO/                          # Data Transfer Objects
│   │   │   │   ├── entities/                     # JPA Entities
│   │   │   │   ├── exceptions/                   # Custom Exceptions
│   │   │   │   ├── repository/                   # JPA Repositories
│   │   │   │   ├── security/                     # Security Utilities
│   │   │   │   └── services/                     # Business Logic
│   │   │   └── resources/
│   │   │       └── application.properties        # Application Configuration
│   │   └── test/                                 # Test Classes
│   ├── uploads/                                  # Uploaded Images
│   ├── Dockerfile                                # Docker Configuration
│   └── pom.xml                                   # Maven Dependencies
│
├── blog-frontend/             # React Frontend
│   ├── src/
│   │   ├── components/        # Reusable UI Components
│   │   ├── layouts/           # Page Layouts
│   │   ├── pages/             # Page Components
│   │   ├── routes/            # Route Guards
│   │   ├── App.jsx            # Main App Component
│   │   ├── axios.js           # Axios Configuration
│   │   └── main.jsx           # React Entry Point
│   ├── public/                # Static Assets
│   ├── package.json           # NPM Dependencies
│   ├── vite.config.js         # Vite Configuration
│   └── tailwind.config.js     # Tailwind Configuration
│
├── PERFORMANCE_OPTIMIZATIONS.md
├── PROJECT_SUMMARY.md         # This File
├── HOW_TO_RUN.md             # Running Instructions
└── README.md
```

---

## 🔧 Backend Details

### Entities (Database Models)

#### 1. User Entity
```java
- id (Long) - Primary Key
- username (String) - Unique, Required
- email (String) - Unique, Required, Email Format
- password (String) - BCrypt Hashed
- role (Enum) - USER or ADMIN
- bio (String) - Optional
- profilePicture (String) - Image URL
- createdAt (LocalDateTime) - Auto-generated
- blogPosts (List<BlogPost>) - One-to-Many
- comments (List<Comment>) - One-to-Many
- likes (Set<Like>) - One-to-Many
```

#### 2. BlogPost Entity
```java
- id (Long) - Primary Key
- title (String) - Required
- content (String) - LONGTEXT, Required
- imageUrl (String) - Optional
- user (User) - Many-to-One
- createdAt (LocalDateTime) - Auto-generated
- updatedAt (LocalDateTime) - Auto-updated
- deleted (Boolean) - Soft delete flag
- comments (List<Comment>) - One-to-Many
- likes (Set<Like>) - One-to-Many
```

#### 3. Comment Entity
```java
- id (Long) - Primary Key
- content (String) - Required
- user (User) - Many-to-One
- blogPost (BlogPost) - Many-to-One
- createdAt (LocalDateTime) - Auto-generated
```

#### 4. Like Entity
```java
- id (Long) - Primary Key
- user (User) - Many-to-One
- blogPost (BlogPost) - Many-to-One
- createdAt (LocalDateTime) - Auto-generated
```

#### 5. Role Enum
```java
- USER
- ADMIN
```

### Data Transfer Objects (DTOs)
| DTO | Purpose |
|-----|---------|
| BlogPostDTO | Blog post data for API responses |
| CommentDTO | Comment data for API responses |
| UserDTO | User data (without password) |
| LoginRequest | Login credentials |
| LoginResponse | JWT token response |
| DashboardStatsDTO | Consolidated dashboard statistics |
| RecentActivityDTO | Recent activity information |

### Repositories
| Repository | Entity | Purpose |
|------------|--------|---------|
| UserRepository | User | User CRUD operations |
| BlogPostRepository | BlogPost | Blog post CRUD + custom queries |
| CommentRepository | Comment | Comment CRUD + custom queries |
| LikeRepository | Like | Like operations |

### Services
| Service | Purpose |
|---------|---------|
| AuthService | User registration and login |
| UserService | User management operations |
| BlogPostService | Blog post CRUD operations |
| CommentService | Comment management |
| LikeService | Like/unlike functionality |
| ActivityService | Recent activities tracking |
| AdminStatsService | Admin statistics |
| DashboardService | Consolidated dashboard data |
| FileStorageService | File upload handling |
| CustomUserDetailsService | Spring Security user loading |

---

## 🖥️ Frontend Details

### Pages

#### Public Pages
| Page | Route | Description |
|------|-------|-------------|
| HomePage | `/` | Landing page with blog posts |
| Login | `/login` | User login |
| Signup | `/signup` | User registration |
| PostContent | `/posts/:id` | Individual blog post view |
| About | `/about` | About page |
| Contact | `/contact` | Contact page |
| Privacy | `/privacy` | Privacy policy |

#### User Pages (Protected)
| Page | Route | Description |
|------|-------|-------------|
| Profile | `/profile` | User profile view/edit |
| WriteBlog | `/write` | Create new blog post |
| UpdatePost | `/update/:postId` | Edit existing post |

#### Admin Pages (Protected - Admin Only)
| Page | Route | Description |
|------|-------|-------------|
| AdminLogin | `/admin` | Admin login |
| Dashboard | `/admin/dashboard` | Admin dashboard with stats |
| Users | `/admin/users` | User management list |
| UserDetail | `/admin/users/:id` | View user details |
| EditUser | `/admin/users/edit/:id` | Edit user |
| Posts | `/admin/posts` | Post management list |
| PostDetail | `/admin/posts/:id` | View post details |
| EditPost | `/admin/posts/edit/:id` | Edit post |
| Comments | `/admin/comments` | Comment management |
| CommentDetail | `/admin/comments/:id` | View comment |
| EditComment | `/admin/comments/edit/:id` | Edit comment |
| RecentActivities | `/admin/recent-activities` | Activity log |

### Components
| Component | Purpose |
|-----------|---------|
| BlogCard | Display blog post preview |
| Header | Top navigation bar |
| HomeHeader | Homepage specific header |
| Footer | Site footer |
| Sidebar | Admin panel navigation |
| Navbar | Main navigation |
| Table | Reusable data table |
| Modal | Popup modal component |
| ConfirmDialog | Confirmation dialogs |
| DashboardCard | Statistics cards |
| Button | Styled button component |
| Input | Styled input component |
| Textarea | Styled textarea component |

---

## 🗄️ Database Schema

```sql
-- Users Table
CREATE TABLE users (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(255) NOT NULL UNIQUE,
    email VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    role ENUM('USER', 'ADMIN') NOT NULL,
    bio TEXT,
    profile_picture VARCHAR(255),
    created_at DATETIME NOT NULL
);

-- Blog Posts Table
CREATE TABLE blog_posts (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    content LONGTEXT NOT NULL,
    image_url VARCHAR(255),
    user_id BIGINT NOT NULL,
    created_at DATETIME NOT NULL,
    updated_at DATETIME NOT NULL,
    is_deleted BOOLEAN DEFAULT FALSE,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

-- Comments Table
CREATE TABLE comments (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    content TEXT NOT NULL,
    user_id BIGINT NOT NULL,
    blog_post_id BIGINT NOT NULL,
    created_at DATETIME NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (blog_post_id) REFERENCES blog_posts(id)
);

-- Likes Table
CREATE TABLE likes (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    user_id BIGINT NOT NULL,
    blog_post_id BIGINT NOT NULL,
    created_at DATETIME NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (blog_post_id) REFERENCES blog_posts(id),
    UNIQUE KEY unique_like (user_id, blog_post_id)
);
```

---

## 📡 API Endpoints

### Authentication APIs (`/api/auth`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/signup` | Register new user | No |
| POST | `/api/auth/login` | User login, returns JWT | No |

### User APIs (`/api/users`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/users` | Get all users | Admin |
| GET | `/api/users/me` | Get current logged-in user | Yes |
| GET | `/api/users/{id}` | Get user by ID | Admin |
| GET | `/api/users/me/posts` | Get current user's posts | Yes |
| PUT | `/api/users/{id}` | Update user | Yes |
| DELETE | `/api/users/{id}` | Delete user | Admin |
| POST | `/api/users/{id}/profile-picture` | Upload profile picture | Yes |
| GET | `/api/users/{userId}/statistics` | Get user statistics | Yes |

### Blog Post APIs (`/api/posts`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/posts` | Get all posts (paginated) | No |
| GET | `/api/posts/{id}` | Get post by ID | No |
| POST | `/api/posts` | Create new post | Yes |
| PUT | `/api/posts/{id}` | Update post | Yes |
| DELETE | `/api/posts/{id}` | Delete post | Yes |
| GET | `/api/posts/test` | Test endpoint | No |

### Comment APIs (`/api/comments`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/comments` | Get all comments | No |
| GET | `/api/comments/{id}` | Get comment by ID | No |
| GET | `/api/comments/blog/{blogPostId}` | Get comments for a post | No |
| POST | `/api/comments` | Create comment | Yes |
| PUT | `/api/comments/{id}` | Update comment | Yes |
| DELETE | `/api/comments/{id}` | Delete comment | Yes |

### Like APIs (`/api/likes`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/likes/toggle` | Toggle like on post | Yes |
| GET | `/api/likes/count/{blogPostId}` | Get like count | No |
| GET | `/api/likes/status` | Check if user liked post | Yes |
| GET | `/api/likes/user/{userId}/liked-posts` | Get user's liked posts | Yes |

### Activity APIs (`/api/activities`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/activities/recent` | Get recent activities | Admin |

### Admin Statistics APIs (`/api`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/users/count` | Get total user count | Admin |
| GET | `/api/posts/count` | Get total post count | Admin |
| GET | `/api/comments/count` | Get total comment count | Admin |

### Dashboard APIs (`/api/dashboard`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/dashboard/stats` | Get consolidated dashboard stats | Admin |

### File Upload
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/uploads/**` | Serve uploaded files | No |

---

## 🔐 Security Implementation

### JWT Authentication
- **Token Generation**: On successful login, a JWT token is generated
- **Token Expiration**: 24 hours (86400000 ms)
- **Token Validation**: Every protected request validates the JWT
- **Password Hashing**: BCrypt algorithm with salt

### Security Configuration
```java
- Stateless session management
- CORS enabled for frontend origin (localhost:5173)
- CSRF disabled (using JWT)
- Role-based access control (USER, ADMIN)
```

### Protected Routes
- All `/api/users/**` except public endpoints
- POST/PUT/DELETE on `/api/posts/**`
- POST/PUT/DELETE on `/api/comments/**`
- All `/api/dashboard/**`
- All admin statistics endpoints

---

## ✨ Features

### User Features
1. ✅ User Registration with validation
2. ✅ User Login with JWT authentication
3. ✅ Profile management (bio, profile picture)
4. ✅ Create, edit, delete blog posts
5. ✅ Upload images for blog posts
6. ✅ Like/unlike blog posts
7. ✅ Comment on blog posts
8. ✅ View liked posts
9. ✅ View own posts

### Admin Features
1. ✅ Admin dashboard with statistics
2. ✅ User management (view, edit, delete)
3. ✅ Post management (view, edit, delete)
4. ✅ Comment management (view, edit, delete)
5. ✅ View recent activities
6. ✅ Role-based access control

### Technical Features
1. ✅ JWT-based authentication
2. ✅ Pagination for blog posts
3. ✅ File upload support
4. ✅ GZIP compression
5. ✅ Database indexing
6. ✅ Response caching
7. ✅ Lazy loading (React)
8. ✅ Code splitting
9. ✅ Docker support
10. ✅ CORS configuration

---

## ⚡ Performance Optimizations

| Optimization | Description | Improvement |
|-------------|-------------|-------------|
| Consolidated Dashboard API | Single endpoint for all dashboard stats | 75% fewer API calls |
| N+1 Query Fix | COUNT queries instead of loading collections | ~90% faster |
| Frontend Code Splitting | React.lazy() for route-based splitting | ~17% smaller bundle |
| GZIP Compression | Compress JSON responses | 60-70% payload reduction |
| Database Indexes | Indexes on foreign keys and timestamps | Faster queries |
| Response Caching | Cache statistics endpoints | Reduced DB load |
| Pagination | Default 10 posts per page | 90% less data per request |

---

## 📁 File Upload Configuration

- **Max File Size**: 20MB
- **Max Request Size**: 200MB
- **Upload Directory**: `./uploads`
- **Supported Formats**: All image formats (AVIF, PNG, JPG, etc.)

---

## 🐳 Docker Support

The backend includes a Dockerfile for containerized deployment:
```dockerfile
FROM maven:3.8.3-openjdk-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

FROM openjdk:17.0.1-jdk-slim
WORKDIR /app
COPY --from=build /app/target/blog_application-0.0.1-SNAPSHOT.jar demo.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "demo.jar"]
```

---

## 📝 Configuration Files

### Backend (`application.properties`)
- Database connection (MySQL)
- JWT secret and expiration
- File upload limits
- GZIP compression settings
- Server configuration

### Frontend (`vite.config.js`)
- Vite build configuration
- Dev server proxy settings

### Frontend (`tailwind.config.js`)
- Tailwind CSS customization

---

*Last Updated: December 2024*
