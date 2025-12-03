# Backend Requirements - Spring Boot (Maven)

## Maven Dependencies (pom.xml)

This file lists all the Java/Maven dependencies required for the backend.
These are automatically installed when you run `mvn install`.

---

## Core Dependencies

### Spring Boot Starter Parent
```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>3.4.2</version>
</parent>
```

### Java Version
```
Java 17 (Required)
```

---

## Dependency List

| Dependency | Group ID | Artifact ID | Version | Purpose |
|------------|----------|-------------|---------|---------|
| Spring Data JPA | org.springframework.boot | spring-boot-starter-data-jpa | (managed) | Database ORM and JPA support |
| Spring Security | org.springframework.boot | spring-boot-starter-security | (managed) | Authentication and Authorization |
| Spring Validation | org.springframework.boot | spring-boot-starter-validation | (managed) | Input validation |
| Spring Web | org.springframework.boot | spring-boot-starter-web | (managed) | REST API support |
| Spring Test | org.springframework.boot | spring-boot-starter-test | (managed) | Testing framework |
| Validation API | javax.validation | validation-api | 2.0.1.Final | Bean validation |
| Logback | ch.qos.logback | logback-classic | (managed) | Logging |
| Jackson Databind | com.fasterxml.jackson.core | jackson-databind | (managed) | JSON processing |
| JWT API | io.jsonwebtoken | jjwt-api | 0.11.5 | JWT token creation |
| JWT Implementation | io.jsonwebtoken | jjwt-impl | 0.11.5 | JWT implementation |
| JWT Jackson | io.jsonwebtoken | jjwt-jackson | 0.11.5 | JWT JSON support |
| MySQL Connector | com.mysql | mysql-connector-j | (managed) | MySQL database driver |
| Lombok | org.projectlombok | lombok | (managed) | Boilerplate code reduction |
| Spring Security Crypto | org.springframework.security | spring-security-crypto | (managed) | Password hashing (BCrypt) |
| Spring Security Test | org.springframework.security | spring-security-test | (managed) | Security testing |

---

## Full pom.xml Dependencies Section

```xml
<dependencies>
    <!-- Spring Data JPA -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>

    <!-- Bean Validation -->
    <dependency>
        <groupId>javax.validation</groupId>
        <artifactId>validation-api</artifactId>
        <version>2.0.1.Final</version>
    </dependency>

    <!-- Spring Security -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-security</artifactId>
    </dependency>

    <!-- Spring Validation -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-validation</artifactId>
    </dependency>

    <!-- Spring Web (REST APIs) -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- Logging -->
    <dependency>
        <groupId>ch.qos.logback</groupId>
        <artifactId>logback-classic</artifactId>
    </dependency>

    <!-- JSON Processing -->
    <dependency>
        <groupId>com.fasterxml.jackson.core</groupId>
        <artifactId>jackson-databind</artifactId>
    </dependency>

    <!-- JWT Libraries -->
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt-api</artifactId>
        <version>0.11.5</version>
    </dependency>
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt-impl</artifactId>
        <version>0.11.5</version>
    </dependency>
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt-jackson</artifactId>
        <version>0.11.5</version>
    </dependency>

    <!-- MySQL Driver -->
    <dependency>
        <groupId>com.mysql</groupId>
        <artifactId>mysql-connector-j</artifactId>
        <scope>runtime</scope>
    </dependency>

    <!-- Lombok -->
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <optional>true</optional>
    </dependency>

    <!-- Password Hashing -->
    <dependency>
        <groupId>org.springframework.security</groupId>
        <artifactId>spring-security-crypto</artifactId>
    </dependency>

    <!-- Testing -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>org.springframework.security</groupId>
        <artifactId>spring-security-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```

---

## Installation Command

```bash
cd blog-application
mvn clean install
```

---

## Build Tool

| Tool | Version | Purpose |
|------|---------|---------|
| Maven | 3.8+ | Dependency management and build |

---

## External Requirements

| Requirement | Version | Purpose |
|-------------|---------|---------|
| MySQL Server | 8.x | Database |
| Java JDK | 17 | Runtime |

---

*Generated for Blogify Backend*
