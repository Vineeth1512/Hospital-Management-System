# 🏥 Hospital Management System
## 📁 Microservices Project Structure

Architecture Style:
- Microservices
- Clean Architecture
- SOLID principles
- Database per service
- JWT Security
- Event-driven (Kafka)
- Dockerized deployment

---

# 🗂 Root Folder Structure
```
hospital-management-system/
│
├── user-service/
├── patient-service/
├── appointment-service/
├── notification-service/
│
├── docker-compose.yml
├── README.md
└── .gitignore
```
---

# 🟢 1️⃣ user-service
```
user-service/
│
├── src/main/java/com/hms/userservice/
│   │
│   ├── config/
│   │   ├── SecurityConfig.java
│   │   └── PasswordConfig.java
│   │
│   ├── security/
│   │   ├── JwtAuthenticationFilter.java
│   │   ├── JwtUtil.java
│   │   └── CustomUserDetailsService.java
│   │
│   ├── exception/
│   │   ├── GlobalExceptionHandler.java
│   │   ├── ResourceNotFoundException.java
│   │   └── BusinessException.java
│   │
│   ├── common/
│   │   └── ApiResponse.java
│   │
│   ├── user/
│   │   ├── controller/
│   │   │   └── AuthController.java
│   │   │
│   │   ├── service/
│   │   │   ├── AuthService.java
│   │   │   └── AuthServiceImpl.java
│   │   │
│   │   ├── repository/
│   │   │   └── UserRepository.java
│   │   │
│   │   ├── entity/
│   │   │   ├── User.java
│   │   │   └── Role.java
│   │   │
│   │   └── dto/
│   │       ├── RegisterRequest.java
│   │       ├── LoginRequest.java
│   │       └── AuthResponse.java
│   │
│   └── UserServiceApplication.java
│
├── src/main/resources/
│   ├── application.yml
│   └── logback-spring.xml
│
├── src/test/java/
│   └── (JUnit tests)
│
├── Dockerfile
└── pom.xml
```
---

# 🟢 2️⃣ patient-service
```
patient-service/
│
├── src/main/java/com/hms/patientservice/
│   │
│   ├── config/
│   │   └── SecurityConfig.java
│   │
│   ├── security/
│   │   ├── JwtAuthenticationFilter.java
│   │   └── JwtUtil.java
│   │
│   ├── exception/
│   │   ├── GlobalExceptionHandler.java
│   │   └── ResourceNotFoundException.java
│   │
│   ├── common/
│   │   └── ApiResponse.java
│   │
│   ├── patient/
│   │   ├── controller/
│   │   │   └── PatientController.java
│   │   │
│   │   ├── service/
│   │   │   ├── PatientService.java
│   │   │   └── PatientServiceImpl.java
│   │   │
│   │   ├── repository/
│   │   │   └── PatientRepository.java
│   │   │
│   │   ├── entity/
│   │   │   └── Patient.java
│   │   │
│   │   └── dto/
│   │       ├── PatientRequest.java
│   │       └── PatientResponse.java
│   │
│   └── PatientServiceApplication.java
│
├── src/main/resources/
│   ├── application.yml
│   └── logback-spring.xml
│
├── src/test/java/
│   └── (JUnit tests)
│
├── Dockerfile
└── pom.xml
```
---

# 🟢 3️⃣ appointment-service
```
appointment-service/
│
├── src/main/java/com/hms/appointmentservice/
│   │
│   ├── config/
│   │   └── WebClientConfig.java
│   │
│   ├── security/
│   │   ├── JwtAuthenticationFilter.java
│   │   └── JwtUtil.java
│   │
│   ├── exception/
│   │   ├── GlobalExceptionHandler.java
│   │   └── BusinessException.java
│   │
│   ├── kafka/
│   │   ├── AppointmentProducer.java
│   │   └── AppointmentEvent.java
│   │
│   ├── appointment/
│   │   ├── controller/
│   │   │   └── AppointmentController.java
│   │   │
│   │   ├── service/
│   │   │   ├── AppointmentService.java
│   │   │   └── AppointmentServiceImpl.java
│   │   │
│   │   ├── repository/
│   │   │   └── AppointmentRepository.java
│   │   │
│   │   ├── entity/
│   │   │   └── Appointment.java
│   │   │
│   │   └── dto/
│   │       ├── AppointmentRequest.java
│   │       └── AppointmentResponse.java
│   │
│   └── AppointmentServiceApplication.java
│
├── src/main/resources/
│   ├── application.yml
│   └── logback-spring.xml
│
├── src/test/java/
│   └── (JUnit tests)
│
├── Dockerfile
└── pom.xml
```
---

# 🟢 4️⃣ notification-service
```
notification-service/
│
├── src/main/java/com/hms/notificationservice/
│   │
│   ├── kafka/
│   │   └── AppointmentConsumer.java
│   │
│   ├── service/
│   │   └── NotificationService.java
│   │
│   └── NotificationServiceApplication.java
│
├── src/main/resources/
│   └── application.yml
│
├── Dockerfile
└── pom.xml
```
---

# 🐳 Docker Layer

Each service contains:

- Dockerfile
- application.yml
- logback configuration

Root folder contains:

docker-compose.yml
- MySQL containers (per service)
- Kafka
- Zookeeper
- All services

---

# 🧠 Design Principles Followed

✔ Clean Architecture  
✔ SOLID principles  
✔ Constructor Injection  
✔ DTO pattern  
✔ Global exception handling  
✔ Structured logging  
✔ Testable services  
✔ Database per service  
✔ Event-driven communication  

---

# 🚀 Future Upgrade Structure (Optional)

Add:
- api-gateway/
- service-registry/
- config-server/
- monitoring-service/

---

# 🎯 Final Result

This structure supports:

- Independent deployments
- Independent scaling
- Loose coupling
- Clear domain boundaries
- Production-level code organization
