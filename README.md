# 🏟️ Court Booking API

## 📖 Overview
A robust backend REST API and internal management system built with **Java 25** and **Spring Boot**, designed specifically for indoor soccer complexes (*canchas de fútbol 5*).

Unlike traditional customer-facing platforms, this system targets **internal staff and administrators**. In Latin America, court reservations are predominantly managed via WhatsApp or phone calls. This software bridges that gap by providing a fast operational tool to manage schedules, track pricing dynamically, monitor active matches in real-time, and feature a built-in **Bootstrap frontend dashboard**.

---

## 👥 Roles & Permissions (RBAC)
Secured using **Spring Security & JWT (JSON Web Tokens)**:

1. **ADMINISTRATOR:**
    - Full CRUD operations for pitches (courts), including pricing and maintenance states.
    - Employee management (create and manage worker accounts).
    - Access to general revenue and occupancy reports.

2. **WORKER / OPERATOR:**
    - Manual reservation entry (recording phone/WhatsApp bookings).
    - Client tracking (Name and Phone number for operational follow-ups).
    - Real-time dashboard monitoring and control.
    - Payment status management (Pending, Deposit Paid, Fully Paid).

---

## 🚀 Core Features

### 1. Pitch Management (Admin)
- Complete management of courts (surface type, lighting, indoor/outdoor status).
- Dynamic hourly rate configuration.

### 2. Flexible Reservation Engine (Worker)
- **Total Time Flexibility:** Allows scheduling blocks of arbitrary duration and custom minutes (e.g., 1.5 hours, 45 minutes, etc.).
- **Automatic Pricing Calculation:** Instantly calculates total cost based on reserved duration and the court's hourly rate.
- **Conflict Prevention:** Strict backend validation logic to prevent double-booking the same court at overlapping times.
- **Client Data Capture:** Stores client name and phone number for operational communication.

### 3. Live Monitoring Dashboard & UI
- Built-in lightweight web interface using **Thymeleaf** and **Bootstrap**.
- **Visual Alerts:** Highlights shifts that are about to end or have concluded.
- **Quick-Action Tick:** Workers can mark a finished slot with a tick, instantly clearing it from active alerts and archiving it in the history.

---

## 💾 Database Schema (PostgreSQL Entities)

- **Users:** `id`, `username`, `password`, `role` (ADMIN, WORKER)
- **Pitches:** `id`, `name`, `description`, `price_per_hour`, `is_active`
- **Reservations:** `id`, `pitch_id`, `client_name`, `client_phone`, `start_time`, `end_time`, `total_price`, `payment_status` (PENDING, DEPOSIT_PAID, PAID), `is_completed` (Boolean flag for the live dashboard)

---

## 🛠️ Technology Stack
- **Java 25**
- **Spring Boot**
- **Spring Security + JWT**
- **Spring Data JPA / Hibernate**
- **PostgreSQL**
- **Thymeleaf & Bootstrap** (Internal UI Dashboard)
- **Springdoc OpenAPI (Swagger)** (API Documentation)
- **Lombok & Spring Validation**
- **Docker & Docker Compose**

---

## ⚙️ Getting Started (Local Setup)

1. Clone the repository:
   ```bash
   git clone [https://github.com/your-username/court-booking-api.git](https://github.com/your-username/court-booking-api.git)