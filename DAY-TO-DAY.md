# 🏥 Hospital Management System
## 📅 Microservices Development Plan (Day-Wise Execution)

**Tech Stack**
- Java 17
- Spring Boot 3
- Spring Security + JWT
- MySQL (One DB per service)
- WebClient
- Kafka
- JUnit + Mockito
- Docker

**Architecture Style**
- Separate microservices
- Database per service
- Event-driven communication
- Clean Architecture + SOLID principles

---

# 🟢 WEEK 1 — User Service (Security Foundation)

## 🗓 Day 1
- Create `user-service`
- Setup MySQL database (`hms_user`)
- Configure JPA
- Create:
  - User Entity
  - Role Enum
  - UserRepository
- Verify DB tables creation

✅ Outcome: Application runs and connects to DB

---

## 🗓 Day 2
- Implement Register API
- Encrypt password using BCrypt
- Create DTOs
- Add validation annotations
- Add structured logging

✅ Outcome: Users can register successfully

---

## 🗓 Day 3
- Implement JWT Utility
- Implement Login API
- Generate JWT token
- Test via Postman

✅ Outcome: Login returns JWT token

---

## 🗓 Day 4
- Implement SecurityConfig
- Implement JWT Filter
- Add Role-based authorization
- Secure endpoints

✅ Outcome: Protected APIs working with JWT

---

## 🗓 Day 5
- Implement Global Exception Handling
- Create Custom Exceptions
- Create Standard API Response wrapper
- Improve logging strategy

✅ Outcome: Clean and consistent error handling

---

## 🗓 Day 6
- Write JUnit tests (Service layer)
- Use Mockito for mocking
- Add basic Controller tests

✅ Outcome: Test coverage started

---

## 🗓 Day 7
- Refactor code
- Improve package structure
- Add Spring Boot Actuator
- Code cleanup and review

✅ Sprint 1 Complete  
User Service Production-Ready ✅

---

# 🟢 WEEK 2 — Patient Service

## 🗓 Day 8
- Create `patient-service`
- Setup MySQL (`hms_patient`)
- Create:
  - Patient Entity
  - Repository
- Verify DB connection

---

## 🗓 Day 9
- Implement CRUD APIs
- Add DTOs
- Add validation

---

## 🗓 Day 10
- Implement Java 8 Streams:
  - Filter patients by age
  - Sort by name
  - Use Collectors
- Use Optional properly

---

## 🗓 Day 11
- Add JWT validation to patient-service
- Secure endpoints

---

## 🗓 Day 12
- Add Global Exception Handling
- Custom exception hierarchy

---

## 🗓 Day 13
- Write JUnit tests
- Improve logging

---

## 🗓 Day 14
- Refactor
- Code review
- Improve documentation

✅ Sprint 2 Complete  
Two Independent Secured Services ✅

---

# 🟢 WEEK 3 — Appointment Service + Communication

## 🗓 Day 15
- Create `appointment-service`
- Setup MySQL (`hms_appointment`)
- Create Entity + Repository

---

## 🗓 Day 16
- Implement Book Appointment API
- Add business validation

---

## 🗓 Day 17
- Add WebClient
- Call patient-service to validate patient existence

---

## 🗓 Day 18
- Add proper exception handling
- Improve business rules

---

## 🗓 Day 19
- Add JWT validation
- Secure endpoints

---

## 🗓 Day 20
- Write JUnit tests
- Mock WebClient calls

---

## 🗓 Day 21
- Refactor
- Improve logging
- Code cleanup

✅ Sprint 3 Complete  
Service-to-Service Communication Working ✅

---

# 🟢 WEEK 4 — Kafka + Production Hardening

## 🗓 Day 22
- Setup Kafka using Docker
- Add Kafka dependency

---

## 🗓 Day 23
- Publish event when appointment is booked

---

## 🗓 Day 24
- Create `notification-service`
- Add Kafka consumer

---

## 🗓 Day 25
- Test event-driven communication
- Add retry handling and logging

---

## 🗓 Day 26
- Create Dockerfile for each service

---

## 🗓 Day 27
- Create docker-compose.yml
- Run entire system via Docker

---

## 🗓 Day 28
- Final refactor
- Improve logging format
- Add README documentation
- Prepare interview explanation

✅ Sprint 4 Complete  
Full Microservices + Kafka + Docker Setup ✅

---

# 🏁 Optional Enterprise Upgrade (Advanced)

After 28 Days, Upgrade Architecture:

- Add API Gateway
- Add Service Registry
- Move JWT validation to Gateway
- Add Centralized Configuration Server
- Add Monitoring & Metrics

---

# 🎯 Final Outcome

You will have:

- Microservices-based architecture
- Secure JWT authentication
- Database per service
- Service-to-service communication
- Event-driven Kafka integration
- Dockerized deployment
- Production-level code structure
- Unit testing and logging

---

# 📌 How To Continue Later

When resuming development:

- Say: “Day 1” → Start user-service
- Say: “Continue from Day 10”
- Say: “Start Sprint 3”

And continue step-by-step.
