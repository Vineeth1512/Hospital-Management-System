# 🏥 Hospital Management System
## 📊 Microservices Architecture Diagram

Technology Stack:
- Java 17
- Spring Boot 3
- Spring Security + JWT
- MySQL (Database per service)
- WebClient (Synchronous communication)
- Kafka (Asynchronous communication)
- Docker (Containerization)

---

# 🧱 1️⃣ High-Level Architecture (Current Phase – Without Gateway)

```
                 +-------------------+
                 |      Client       |
                 | (Postman / React) |
                 +---------+---------+
                           |
                           |
        -------------------------------------------------
        |                 |                 |           |
        |                 |                 |           |
+-------v-------+ +-------v-------+ +-------v-------+ +-------v-------+
|  User Service | | Patient Service| | Appointment   | | Notification  |
|   (8081)      | |    (8082)      | | Service (8083)| | Service (8084)|
+-------+-------+ +-------+--------+ +-------+-------+ +-------+-------+
        |                 |                  |                 |
        |                 |                  |                 |
+-------v-------+ +-------v-------+ +--------v--------+        |
|  MySQL DB     | |  MySQL DB     | |   MySQL DB      |        |
| hms_user      | | hms_patient   | | hms_appointment |        |
+---------------+ +---------------+ +------------------+        |
                                                                  |
                                      +---------------------------+
                                      |
                               +------v-------+
                               |   Kafka      |
                               | Event Broker |
                               +--------------+
```

---

# 🔄 2️⃣ Communication Flow

## 🟢 Authentication Flow

1. Client → User Service
2. User logs in
3. JWT token generated
4. Client sends JWT in headers for all secured APIs

---

## 🟢 Synchronous Communication (WebClient)

```
Appointment Service
        |
        |  Validate patient
        v
Patient Service
```

- Used for validation before booking appointment
- Non-blocking WebClient

---

## 🟢 Asynchronous Communication (Kafka)

```
Appointment Service
        |
        |  Publish Event
        v
      Kafka
        |
        v
Notification Service
```

- Loose coupling
- Event-driven
- Scalable

---

# 🗄 3️⃣ Database Architecture

Microservices Rule:
✔ Each service has its own database  
✔ No shared database  
✔ No cross-service foreign keys  
✔ Data consistency via API calls  

| Service              | Database Name     |
|----------------------|------------------|
| user-service         | hms_user         |
| patient-service      | hms_patient      |
| appointment-service  | hms_appointment  |
| notification-service | hms_notification |

---

# 🏗 4️⃣ Future Enterprise Upgrade Architecture

After Phase Completion, Architecture Will Become:

```
                +-------------------+
                |      Client       |
                +---------+---------+
                          |
                          v
                +-------------------+
                |   API Gateway     |
                | (JWT Validation)  |
                +---------+---------+
                          |
                          v
                +-------------------+
                | Service Registry  |
                |     (Eureka)      |
                +---------+---------+
                          |
        -------------------------------------------------
        |                 |                 |           |
+-------v-------+ +-------v-------+ +-------v-------+ +-------v-------+
|  User Service | | Patient Service| | Appointment   | | Notification  |
+---------------+ +---------------+ +---------------+ +---------------+
                          |
                          v
                        Kafka
```

---

# 🔐 5️⃣ Security Architecture

Current Phase:
- JWT validated inside each service

Future Phase:
- JWT validated at API Gateway
- Services trust forwarded authentication

Security Features:
- BCrypt password hashing
- Stateless authentication
- Role-based access control
- Token expiration

---

# 📦 6️⃣ Deployment Architecture (Docker)

```
Docker Network
   |
   |-- user-service container
   |-- patient-service container
   |-- appointment-service container
   |-- notification-service container
   |-- mysql containers (per service)
   |-- kafka container
   |-- zookeeper container
```

---

# 🧠 7️⃣ Design Principles Applied

✔ Clean Architecture  
✔ SOLID principles  
✔ Domain-driven separation  
✔ Database per service  
✔ Event-driven architecture  
✔ Loose coupling  
✔ Centralized logging (future upgrade)  
✔ Independent scaling capability  

---

# 🎯 Final Architecture Summary

This architecture supports:

- Independent deployment
- Horizontal scalability
- Fault isolation
- Clean domain separation
- Event-driven processing
- Enterprise-level extension capability
