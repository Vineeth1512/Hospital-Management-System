# Hospital-Management-System


---

```markdown
# 🏥 Hospital Management System (Microservices Architecture)

A production-ready microservices-based Hospital Management System built using **Spring Boot 3**, **Java 17**, **MySQL**, **JWT Security**, **Kafka**, and **Docker**.

---

## 📌 Project Overview

This project demonstrates:

- Microservices architecture
- Database per service
- JWT-based authentication
- Role-based authorization
- Service-to-service communication using WebClient
- Event-driven architecture using Kafka
- Clean Architecture principles
- SOLID design principles
- Proper exception handling
- Logging strategy
- Unit testing with JUnit & Mockito
- Dockerized deployment

---

## 🏗 Architecture Overview

```

Client
↓
User Service (JWT Auth)
Patient Service
Appointment Service
Notification Service
↓
Kafka (Event Bus)
↓
MySQL (One DB per service)

````

Each service runs independently on a different port.

---

## 🧱 Microservices

### 1️⃣ user-service (Port: 8081)
- User Registration
- Login
- JWT Token Generation
- Role-based access (ADMIN, DOCTOR, PATIENT)
- Password encryption using BCrypt

Database: `hms_user`

---

### 2️⃣ patient-service (Port: 8082)
- CRUD operations for patients
- Java 8 Streams usage
- Secure endpoints using JWT

Database: `hms_patient`

---

### 3️⃣ appointment-service (Port: 8083)
- Book appointment
- Validate patient via WebClient
- Publish Kafka event when appointment booked

Database: `hms_appointment`

---

### 4️⃣ notification-service (Port: 8084)
- Kafka Consumer
- Listens to appointment events
- Sends/logs notifications

---

## 🗄 Database Design

Each microservice has its own database.

### hms_user
- users

### hms_patient
- patients

### hms_appointment
- appointments

---

## 🔐 Security

- Stateless JWT authentication
- Token-based authorization
- Role-based endpoint access
- BCrypt password hashing
- Custom JWT filter per service

---

## 📡 Event-Driven Communication

- Appointment Service publishes `AppointmentBookedEvent`
- Notification Service consumes event from Kafka

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|------------|
| Language | Java 17 |
| Framework | Spring Boot 3 |
| Security | Spring Security + JWT |
| Database | MySQL |
| ORM | Spring Data JPA |
| Messaging | Apache Kafka |
| Communication | WebClient |
| Testing | JUnit 5, Mockito |
| Containerization | Docker |
| Build Tool | Maven |

---

## 🚀 How to Run the Project

### 1️⃣ Clone Repository

```bash
git clone <your-repo-url>
cd hospital-management-system
````

---

### 2️⃣ Setup MySQL

Create databases:

```sql
CREATE DATABASE hms_user;
CREATE DATABASE hms_patient;
CREATE DATABASE hms_appointment;
```

Update database credentials in `application.yml` if needed.

---

### 3️⃣ Start Kafka (Docker)

```bash
docker-compose up kafka
```

Or run full stack:

```bash
docker-compose up --build
```

---

### 4️⃣ Run Services Individually

Start in this order:

1. user-service
2. patient-service
3. appointment-service
4. notification-service

---

## 🔑 API Endpoints

### User Service

| Method | Endpoint           | Description       |
| ------ | ------------------ | ----------------- |
| POST   | /api/auth/register | Register new user |
| POST   | /api/auth/login    | Login and get JWT |

---

### Patient Service

| Method | Endpoint           | Description       |
| ------ | ------------------ | ----------------- |
| POST   | /api/patients      | Create patient    |
| GET    | /api/patients      | Get all patients  |
| GET    | /api/patients/{id} | Get patient by ID |
| PUT    | /api/patients/{id} | Update patient    |
| DELETE | /api/patients/{id} | Delete patient    |

---

### Appointment Service

| Method | Endpoint               | Description        |
| ------ | ---------------------- | ------------------ |
| POST   | /api/appointments      | Book appointment   |
| DELETE | /api/appointments/{id} | Cancel appointment |

---

## 🧪 Running Tests

```bash
mvn test
```

Unit tests include:

* Service layer tests
* Controller tests
* Mocked WebClient calls
* Kafka producer/consumer tests

---

## 🐳 Docker Setup

Each microservice includes:

```
Dockerfile
```

Run entire system:

```bash
docker-compose up --build
```

---

## 📊 Logging Strategy

* SLF4J + Logback
* Structured logging
* Error logging with stack trace
* Request/Response logging (optional)

---

## 🧠 Key Design Decisions

* Database per service (Microservices best practice)
* JWT-based stateless authentication
* Event-driven architecture for loose coupling
* Clean architecture for maintainability
* Constructor injection for testability
* Global exception handling strategy

---

## 📈 Future Enhancements

* API Gateway
* Service Registry (Eureka)
* Centralized Configuration Server
* Distributed Tracing
* Monitoring with Prometheus & Grafana
* CI/CD Pipeline

---

## 👨‍💻 Author

Your Name

---

## 📜 License

This project is for learning and demonstration purposes.

```

---

If you want next, I can generate:

- 🐳 `docker-compose.yml` template  
- 📂 Full folder structure template  
- 🧠 Interview explanation script  
- 📊 ER diagram markdown  
- 🛡 Security architecture explanation  

Tell me what you want next. 🚀
```
