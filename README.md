# 🏥 Medical Aid Tracker

## 📌 Overview
**Medical Aid Tracker** is a Java-based application that streamlines the process of accessing medical services such as doctor consultations, ambulance bookings, and hospital bed availability. The system interacts with a MySQL database and offers distinct roles for **Patients** and **Medical Representatives**, with tailored functionalities for each.

---

## 🚀 Features

### 👤 Patient Login
- 🔍 Search Doctors by Specialization
- 🚑 Search Emergency Doctors with Available Beds
- 🚐 Search for Available Ambulance Services
- 📅 Book a Doctor Appointment
- ➕ Add a New Patient
- 📋 Show Appointment Details
- 🗑️ Delete Patient Record (and its Appointments)
- ❌ Cancel Appointment by Appointment ID
- 🧾 Show Patient Details

### 🏥 Medical Representative Login
- 🩺 Update Doctor Availability Status
- 🛏️ Update Bed Availability Status
- ❌ Cancel Appointments by Doctor ID
- 🗑️ Delete Patient Record (and its Appointments)
- 📋 Show Appointment Details
- 🧾 Show Patient Details

### 🔐 Login Options
- 1️⃣ Patient Login
- 2️⃣ Medical Representative Login
- 3️⃣ Exit Application

---

## 🧰 Technologies Used
- **Java** – Core programming language
- **JDBC** – For MySQL connectivity
- **MySQL** – Backend database
- **E/R Modeling** – For logical database schema

---

## 🧠 Database Schema

## 📌 Entity-Relationship Diagram

<a href="https://github.com/SamadritaM30/Medical_Aid_Tracker/blob/main/NEW_ER.drawio.pdf" target="_blank">📄 Click here to view the ER Diagram (PDF)</a>

---

## 📂 Tables & Fields

### 1. `patient`
| Field | Type | Description |
|-------|------|-------------|
| `patient_id` | INT (PK) | Unique identifier |
| `name` | VARCHAR | Patient name |
| `dob` | DATE | Date of birth |
| `contact_number` | VARCHAR | Contact details |
| `blood_group` | VARCHAR | Blood group |

### 2. `doctors`
| Field | Type | Description |
|-------|------|-------------|
| `doctor_id` | INT (PK) | Unique doctor ID |
| `name` | VARCHAR | Doctor's name |
| `specialization` | VARCHAR | Area of expertise |
| `availability_status` | ENUM | 'Available', 'Unavailable' |
| `from_time` | TIME | Start of consultation |
| `to_time` | TIME | End of consultation |
| `hospital_id` | INT (FK) | Linked hospital |

### 3. `hospitals`
| Field | Type | Description |
|-------|------|-------------|
| `hospital_id` | INT (PK) | Unique hospital ID |
| `hospital_name` | VARCHAR | Name of the hospital |
| `address` | TEXT | Location details |
| `contact_number` | VARCHAR | Hospital phone |

### 4. `beds`
| Field | Type | Description |
|-------|------|-------------|
| `bed_id` | INT (PK) | Bed ID |
| `hospital_id` | INT (FK) | Hospital linkage |
| `ward_type` | ENUM | 'ICU', 'General' |
| `status` | ENUM | 'Available', 'Occupied' |

### 5. `appointments`
| Field | Type | Description |
|-------|------|-------------|
| `id` | INT (PK) | Appointment ID |
| `patient` | INT (FK) | Linked patient |
| `doctor_id` | INT (FK) | Assigned doctor |
| `hospital` | INT (FK) | Hospital location |
| `date` | DATE | Appointment date |
| `time` | TIME | Time of appointment |
| `status` | ENUM | 'Booked', 'Completed', 'Cancelled' |

### 6. `ambulance`
| Field | Type | Description |
|-------|------|-------------|
| `id` | INT (PK) | Ambulance ID |
| `driver` | VARCHAR | Driver name |
| `location` | VARCHAR | Current/last known location |
| `status` | ENUM | 'Available', 'Busy' |

### 7. `ambulance_phone`
| Field | Type | Description |
|-------|------|-------------|
| `phone` | VARCHAR | Driver contact |
| `id` | INT (FK) | Ambulance reference |

---

## ⚙️ Setup & Installation

### 📋 Prerequisites
- Java 8+
- MySQL Server
- JDBC MySQL Driver

### 🏗️ Steps
1. Clone this repository.
2. Create a MySQL database:
   ```sql
   CREATE DATABASE medical_aid_tracker;
