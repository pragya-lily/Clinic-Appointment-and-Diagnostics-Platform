# Clinic-Appointment-and-Diagnostics-Platform

##  Overview
This project represents the **Entity-Relationship (ER) Diagram** for a modern clinic management system. The system is designed to handle core operations such as managing patients, doctors, appointments, consultations, diagnostic tests, reports, and payments in a structured and scalable way.

---

##  Objectives
The ER diagram is designed to answer key operational questions:

- Who are the doctors and what are their specialties?
- Which patient booked which appointment?
- What is the status of appointments?
- Does an appointment always result in a consultation?
- Were diagnostic tests prescribed during a visit?
- What reports were generated?
- How are payments managed?

---

##  Entities and Attributes

###  Patient
- `patient_id` (PK)
- `full_name`
- `email`
- `phone`
- `date_of_birth`
- `sex`
- `created_at`

---

###  Doctor
- `doctor_id` (PK)
- `full_name`
- `email`
- `phone`
- `license_no`
- `department`
- `is_active`
- `created_at`

---

###  Specialty
- `specialty_id` (PK)
- `name`
- `description`

---

###  Doctor_Specialty
- `doctor_specialty_id` (PK)
- `doctor_id` (FK)
- `specialty_id` (FK)

---

###  Appointment
- `appointment_id` (PK)
- `patient_id` (FK)
- `doctor_id` (FK)
- `scheduled_start`
- `scheduled_end`
- `status`
- `reason_for_visit`
- `booked_at`

---

###  Consultation
- `consultation_id` (PK)
- `appointment_id` (FK, optional)
- `patient_id` (FK)
- `doctor_id` (FK)
- `check_in_time`
- `start_time`
- `end_time`
- `diagnosis_summary`
- `notes`
- `status`

---

###  Diagnostic_Test
- `test_id` (PK)
- `name`
- `category`
- `description`
- `base_price_amount`
- `base_price_currency`
- `is_active`

---

###  Test_Order
- `test_order_id` (PK)
- `consultation_id` (FK)
- `test_id` (FK)
- `ordered_at`
- `priority`
- `status`
- `instructions`

---

###  Test_Report
- `report_id` (PK)
- `test_order_id` (FK)
- `generated_at`
- `report_status`
- `result_summary`
- `report_url`

---

###  Payment
- `payment_id` (PK)
- `consultation_id` (FK)
- `appointment_id` (FK, optional)
- `amount`
- `currency`
- `provider`
- `provider_ref`
- `paid_at`
- `status`

---

##  Relationships

- A **Patient** can book multiple **Appointments**
- A **Doctor** can attend multiple **Appointments**
- An **Appointment** may result in **zero or one Consultation**
- A **Patient** can have multiple **Consultations**
- A **Doctor** can conduct multiple **Consultations**
- A **Consultation** can have multiple **Test Orders**
- A **Diagnostic Test** can be used in multiple **Test Orders**
- Each **Test Order** generates one **Test Report**
- A **Consultation** can have associated **Payments**
- A **Doctor** can have multiple **Specialties** (via Doctor_Specialty)

---

##  Key Design Decisions

- **Appointment vs Consultation Separation**  
  Not every appointment results in a consultation (e.g., cancellations, no-shows).

- **Support for Walk-in Patients**  
  Consultations can exist without a linked appointment.

- **Many-to-Many Relationship Handling**  
  Between Consultation and Diagnostic Tests using `Test_Order`.

- **Flexible Payment Structure**  
  Payments can be linked to either consultations or appointments.

- **Normalized Specialty Structure**  
  Doctors can have multiple specialties using a junction table.

---

##  ER Diagram

![Clinic ER Diagram](https://github.com/pragya-lily/Clinic-Appointment-and-Diagnostics-Platform/blob/main/Clinic%20ER%20Diagram.pdf)

---

##  Conclusion
This ER diagram provides a clean and scalable structure for managing clinic operations, ensuring flexibility, data integrity, and efficient handling of patient workflows from appointment booking to diagnostic reporting and payments.
