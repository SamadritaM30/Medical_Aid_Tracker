# Medical Aid Tracker

## Overview
Medical Aid Tracker is a Java-based system that helps users find and book medical assistance, including doctor appointments, hospital beds, and ambulance services. The system uses MySQL as the backend database and provides functionalities such as searching for doctors, checking hospital bed availability, and booking emergency services.

---

## Features
- **Search Doctors by Specialization**:  
  Find doctors based on their specialization (e.g., Cardiologist, Neurologist). Users can search for a specific field and get a list of available doctors along with their consultation timings and hospital details.

- **Search Emergency Doctors with Available Beds**:  
  Find doctors at hospitals where beds are available. This feature ensures patients in urgent need can quickly locate a doctor along with ICU or general ward availability.

- **Search for Available Ambulance Services**:  
  Search for nearby ambulances along with their current availability and last known location. This ensures quick emergency response.

- **Book a Doctor Appointment**:  
  Allows users to book a doctor appointment by selecting a doctor, date, and time. The system records the appointment details in the database.

- **Add a New Patient**:  
  Patients can be registered in the system by providing details like name, date of birth, and contact information. This helps in maintaining patient history.

- **Exit the System**:  
  Users can safely exit the application when they are done with their activities.

---

## Technologies Used
- **Java** (JDBC for database connectivity)
- **MySQL** (Database management)
- **E/R Model** (Database schema based on entity relationships)

---

## Database Schema
This project follows an ER diagram consisting of the following tables:

### 1. Patients
| Column         | Type        | Description                      |
|---------------|------------|----------------------------------|
| `patient_id`  | INT (PK)    | Unique patient identifier       |
| `name`        | VARCHAR     | Patient name                    |
| `date_of_birth` | DATE      | Patient's date of birth         |
| `contact_number` | VARCHAR  | Contact details                 |

### 2. Doctors
| Column           | Type        | Description                          |
|-----------------|------------|--------------------------------------|
| `doctor_id`     | INT (PK)    | Unique doctor identifier            |
| `name`          | VARCHAR     | Doctor's name                       |
| `specialization` | VARCHAR    | Doctor's field of expertise         |
| `availability_status` | ENUM ('Available', 'Unavailable') | Availability status |
| `timing`        | VARCHAR     | Consultation timings                 |
| `hospital_id`   | INT (FK)    | Associated hospital                  |

### 3. Hospitals
| Column         | Type      | Description                      |
|---------------|----------|----------------------------------|
| `hospital_id` | INT (PK) | Unique hospital identifier       |
| `name`        | VARCHAR  | Hospital name                    |
| `address`     | TEXT     | Hospital address                 |

### 4. Beds
| Column         | Type      | Description                      |
|---------------|----------|----------------------------------|
| `bed_id`      | INT (PK) | Unique bed identifier           |
| `hospital_id` | INT (FK) | Associated hospital             |
| `ward_type`   | ENUM ('ICU', 'General') | Type of ward |
| `availability_status` | ENUM ('Available', 'Occupied') | Bed availability |

### 5. Appointments
| Column             | Type      | Description                          |
|-------------------|----------|--------------------------------------|
| `appointment_id`  | INT (PK) | Unique appointment identifier       |
| `patient_id`      | INT (FK) | Associated patient                  |
| `doctor_id`       | INT (FK) | Assigned doctor                     |
| `hospital_id`     | INT (FK) | Hospital where the appointment is booked |
| `appointment_date`| DATE      | Appointment date                    |
| `appointment_time`| TIME      | Appointment time                    |
| `appointment_status` | ENUM ('Booked', 'Completed', 'Cancelled') | Status of the appointment |

### 6. Ambulance
| Column          | Type      | Description                     |
|----------------|----------|---------------------------------|
| `ambulance_id` | INT (PK) | Unique ambulance identifier    |
| `patient_id`   | INT (FK) | Associated patient             |
| `contact_number` | VARCHAR | Driver's contact              |
| `last_location` | VARCHAR | Last known location           |
| `availability_status` | ENUM ('Available', 'Busy') | Availability of the ambulance |

---

## Setup and Installation

### 1. Prerequisites
- Install **Java 8+**
- Install **MySQL Server**
- Install **JDBC Driver** for MySQL

### 2. Database Configuration
1. Create the database in MySQL:
   ```sql
   CREATE DATABASE medical_aid_tracker;
