# Clinic-Appointment-and-Diagnostics-Platform
Overview
This ER diagram represents a modern clinic system designed to manage patients, doctors,
appointments, consultations, diagnostic tests, reports, and payments in a structured and scalable
way.
Patient
Stores details of patients who visit the clinic. A patient can book multiple appointments and have
multiple consultations over time.
Doctor & Specialty
Doctors are associated with one or more specialties. This allows flexibility where a doctor can
practice in multiple domains.
Appointment
Represents a scheduled meeting between a patient and a doctor. Not all appointments result in
consultations due to cancellations or no-shows.
Consultation (Visit)
Represents the actual visit of a patient to a doctor. It may be linked to an appointment or may occur
as a walk-in.
Diagnostic Tests
Doctors can prescribe multiple diagnostic tests during a consultation. These are managed through
a separate structure to handle many-to-many relationships.
Reports
Each prescribed test results in a report that is generated later and linked back to the consultation.
Payment
Payments are associated with consultations and optionally appointments, representing billing for
services provided.
Key Design Decisions- Appointment and consultation are separated to handle real-world scenarios. - Tests are linked to
consultations instead of appointments. - Reports are linked to prescribed tests. - Many-to-many
relationships are resolved using intermediate entities. - The design ensures scalability and avoids
redundancy
