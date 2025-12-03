# How to Run Blogify

## 📋 Prerequisites

Before running the application, ensure you have the following installed on your system:

### Required Software

| Software | Version | Download Link |
|----------|---------|---------------|
| Java JDK | 17+ | [Oracle JDK](https://www.oracle.com/java/technologies/downloads/) or [OpenJDK](https://openjdk.org/) |
| Node.js | 18+ | [Node.js](https://nodejs.org/) |
| MySQL | 8.x | [MySQL](https://dev.mysql.com/downloads/) |
| Maven | 3.8+ | [Maven](https://maven.apache.org/download.cgi) |
| Git | Latest | [Git](https://git-scm.com/) |

### Verify Installations
```bash
# Check Java version
java -version

# Check Node.js version
node -v

# Check npm version
npm -v

# Check Maven version
mvn -v

# Check MySQL
mysql --version
```

---

## 🗄️ Step 1: Database Setup

### 1.1 Start MySQL Server
```bash
# macOS (using Homebrew)
brew services start mysql

# Linux
sudo systemctl start mysql

# Windows - Start MySQL from Services or MySQL Workbench
```

### 1.2 Create Database
```bash
# Login to MySQL
mysql -u root -p

# Create the database
CREATE DATABASE blog_db;

# Verify database creation
SHOW DATABASES;

# Exit MySQL
EXIT;
```

### 1.3 Update Database Credentials (if needed)
Edit the file: `blog-application/src/main/resources/application.properties`

```properties
# Update these with your MySQL credentials
spring.datasource.url=jdbc:mysql://localhost:3306/blog_db
spring.datasource.username=root
spring.datasource.password=YOUR_PASSWORD
```

---

## ⚙️ Step 2: Backend Setup (Spring Boot)

### 2.1 Navigate to Backend Directory
```bash
cd blog-application
```

### 2.2 Install Dependencies & Build
```bash
# Clean and install dependencies
mvn clean install

# Skip tests if you want faster build
mvn clean install -DskipTests
```

### 2.3 Run the Backend Server
```bash
# Using Maven
mvn spring-boot:run

# OR using the JAR file
java -jar target/blog-application-0.0.1-SNAPSHOT.jar
```

### 2.4 Verify Backend is Running
- Open browser and go to: `http://localhost:8080/api/posts/test`
- You should see: `Hello from BlogPostController`

---

## 🎨 Step 3: Frontend Setup (React + Vite)

### 3.1 Open a New Terminal

### 3.2 Navigate to Frontend Directory
```bash
cd blog-frontend
```

### 3.3 Install Dependencies
```bash
npm install
```

### 3.4 Run the Development Server
```bash
npm run dev
```

### 3.5 Access the Application
- Open browser and go to: `http://localhost:5173`
- The application should be running!

---

## 🚀 Quick Start (All Commands)

### Terminal 1 - Backend
```bash
cd blog-application
mvn spring-boot:run
```

### Terminal 2 - Frontend
```bash
cd blog-frontend
npm install
npm run dev
```

---

## 🐳 Running with Docker (Alternative)

### Backend Only (Docker)
```bash
cd blog-application

# Build Docker image
docker build -t blogify-backend .

# Run container
docker run -p 8080:8080 \
  -e SPRING_DATASOURCE_URL=jdbc:mysql://host.docker.internal:3306/blog_db \
  -e SPRING_DATASOURCE_USERNAME=root \
  -e SPRING_DATASOURCE_PASSWORD=your_password \
  blogify-backend
```

---

## 📁 Project URLs

| Service | URL | Description |
|---------|-----|-------------|
| Frontend | http://localhost:5173 | React application |
| Backend API | http://localhost:8080 | Spring Boot API |
| API Test | http://localhost:8080/api/posts/test | API health check |

---

## 👤 Default User Setup

### Create Admin User
After starting the application, register a new user and manually update the role in the database:

```sql
-- Login to MySQL
mysql -u root -p

-- Use the database
USE blog_db;

-- Update user role to ADMIN (replace email with your user's email)
UPDATE users SET role = 'ADMIN' WHERE email = 'admin@example.com';

-- Verify the update
SELECT id, username, email, role FROM users;
```

---

## 🔧 Troubleshooting

### Issue: Port 8080 Already in Use
```bash
# Find process using port 8080
lsof -i :8080

# Kill the process
kill -9 <PID>
```

### Issue: Port 5173 Already in Use
```bash
# Find process using port 5173
lsof -i :5173

# Kill the process
kill -9 <PID>
```

### Issue: MySQL Connection Refused
1. Ensure MySQL is running
2. Check credentials in `application.properties`
3. Verify database `blog_db` exists

### Issue: CORS Error
- Ensure backend is running on port 8080
- Check `SecurityConfig.java` for allowed origins

### Issue: npm install fails
```bash
# Clear npm cache
npm cache clean --force

# Remove node_modules and reinstall
rm -rf node_modules
rm package-lock.json
npm install
```

### Issue: Maven build fails
```bash
# Clear Maven cache
mvn dependency:purge-local-repository

# Rebuild
mvn clean install -DskipTests
```

---

## 📝 Environment Variables (Optional)

### Backend (application.properties)
```properties
# Database
spring.datasource.url=jdbc:mysql://localhost:3306/blog_db
spring.datasource.username=root
spring.datasource.password=YOUR_PASSWORD

# JWT
jwt.secret=your-secret-key-min-64-characters-long-for-security
jwt.expiration=86400000

# File uploads
file.upload-dir=./uploads
```

### Frontend (.env file - create if needed)
```env
VITE_API_URL=http://localhost:8080
```

---

## 🔄 Development Workflow

### Backend Hot Reload
For development, you can use Spring DevTools (already included):
```bash
mvn spring-boot:run
```

### Frontend Hot Reload
Vite provides hot module replacement (HMR) out of the box:
```bash
npm run dev
```

---

## 🏗️ Production Build

### Backend
```bash
cd blog-application
mvn clean package -DskipTests

# Run production JAR
java -jar target/blog-application-0.0.1-SNAPSHOT.jar
```

### Frontend
```bash
cd blog-frontend

# Build for production
npm run build

# Preview production build
npm run preview
```

---

## 📊 Checking Logs

### Backend Logs
Logs appear in the terminal where you ran `mvn spring-boot:run`

### Frontend Logs
Open browser Developer Tools (F12) → Console tab

---

## ✅ Verification Checklist

- [ ] MySQL is running
- [ ] Database `blog_db` is created
- [ ] Backend starts without errors (port 8080)
- [ ] Frontend starts without errors (port 5173)
- [ ] Can access http://localhost:5173
- [ ] Can register a new user
- [ ] Can login with registered user
- [ ] Can create a blog post

---

## 📞 Need Help?

If you encounter any issues:
1. Check the troubleshooting section above
2. Ensure all prerequisites are installed
3. Verify database credentials
4. Check that ports 8080 and 5173 are free

---

*Last Updated: December 2024*
