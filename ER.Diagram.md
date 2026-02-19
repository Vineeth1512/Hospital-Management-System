# 🏥 Hospital Management System
## 📊 Entity Relationship (ER) Diagram

Architecture Style:
- Microservices
- Database per Service
- Loose coupling
- Event-driven communication

---

# 🗄 1️⃣ User Service Database (hms_user)

## Table: users

| Column Name | Type        | Constraints                |
|------------|------------|----------------------------|
| id         | BIGINT     | PK, Auto Increment         |
| username   | VARCHAR    | UNIQUE, NOT NULL           |
| password   | VARCHAR    | NOT NULL                   |
| role       | VARCHAR    | ADMIN / DOCTOR / PATIENT   |
| created_at | TIMESTAMP  | DEFAULT CURRENT_TIMESTAMP  |

---

# 🗄 2️⃣ Patient Service Database (hms_patient)

## Table: patients

| Column Name | Type      | Constraints        |
|------------|----------|--------------------|
| id         | BIGINT   | PK, Auto Increment |
| first_name | VARCHAR  | NOT NULL           |
| last_name  | VARCHAR  | NOT NULL           |
| age        | INT      | NOT NULL           |
| gender     | VARCHAR  | NOT NULL           |
| phone      | VARCHAR  | UNIQUE             |
| email      | VARCHAR  | UNIQUE             |
| address    | VARCHAR  |                    |
| created_at | TIMESTAMP| DEFAULT CURRENT_TIMESTAMP |

---

# 🗄 3️⃣ Appointment Service Database (hms_appointment)

## Table: appointments

| Column Name      | Type      | Constraints        |
|------------------|----------|--------------------|
| id               | BIGINT   | PK, Auto Increment |
| patient_id       | BIGINT   | NOT NULL           |
| doctor_name      | VARCHAR  | NOT NULL           |
| appointment_time | DATETIME | NOT NULL           |
| status           | VARCHAR  | BOOKED/CANCELLED   |
| created_at       | TIMESTAMP| DEFAULT CURRENT_TIMESTAMP |

Note:
- patient_id is NOT a foreign key.
- Microservices do NOT share foreign keys.
- Validation happens via WebClient call.

---

# 🗄 4️⃣ Notification Service (Optional Persistence)

## Table: notifications (Optional)

| Column Name | Type      | Constraints        |
|------------|----------|--------------------|
| id         | BIGINT   | PK, Auto Increment |
| event_type | VARCHAR  | NOT NULL           |
| payload    | TEXT     | NOT NULL           |
| status     | VARCHAR  | SENT/FAILED        |
| created_at | TIMESTAMP| DEFAULT CURRENT_TIMESTAMP |

---

# 🔗 Logical Relationships (Across Services)

User Service
   |
   | (Role = PATIENT)
   ↓
Patient Service
   |
   | (patient_id reference)
   ↓
Appointment Service
   |
   | (Kafka Event)
   ↓
Notification Service

---

# 🧠 Important Microservices Principle

✔ No shared database  
✔ No foreign key between services  
✔ Communication via:
   - WebClient (synchronous)
   - Kafka (asynchronous)

---

# 📊 ER Relationship Diagram (Text Representation)

USER (hms_user)
  └── id (PK)

PATIENT (hms_patient)
  └── id (PK)

APPOINTMENT (hms_appointment)
  └── id (PK)
  └── patient_id (Logical reference only)

NOTIFICATION (optional)
  └── id (PK)

---

# 🏗 Database Separation Strategy

| Service              | Database Name     |
|----------------------|------------------|
| user-service         | hms_user         |
| patient-service      | hms_patient      |
| appointment-service  | hms_appointment  |
| notification-service | hms_notification |

---

# 🚀 Future Enhancements

- Add doctor-service
- Add billing-service
- Add pharmacy-service
- Add audit-service

---

# 🎯 Final Design Summary

This ER design supports:

- Independent scaling
- Domain isolation
- Event-driven architecture
- Clean service boundaries
- Production-ready microservices
