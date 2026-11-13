# SchoolPro AI — Future Backend & Production Architecture Roadmap

The current `index.html` deliverable is a zero-dependency, browser-based open-source prototype using `localStorage`. To deploy **SchoolPro AI** across real Pakistani schools with multi-user concurrency, secure authentication, and live external integrations, follow this engineering roadmap.

---

## 1. Recommended Open-Source Production Stack

- **Backend Runtime & API:** Node.js (Fastify / NestJS) *or* PHP 8.3 (Laravel) — both widely supported on affordable Pakistani VPS and cloud hosting.
- **Relational Database:** PostgreSQL 16 (recommended for strict ACID ledger transactions and JSONB audit logs) or MySQL 8.0.
- **Authentication & Authorization:**
  - Server-side `HttpOnly`, `Secure`, `SameSite=Lax` session cookies or short-lived JWT access tokens + rotating refresh tokens.
  - Password hashing via `Argon2id` or `bcrypt`.
  - Middleware-enforced Role-Based Access Control (RBAC) checking `school_id` (tenant isolation) and `role_permissions` on **every** API route — never relying on frontend role switchers.
- **File & Document Storage:** S3-compatible object storage (MinIO self-hosted or Cloudflare R2) for student photos, B-Form scans, and custom school logos.

---

## 2. Core Relational Database Schema

1. **`schools` & `demo_sandboxes`**: `id`, `name`, `address`, `phone`, `current_session_id`, `is_demo`, `demo_expires_at`, `student_limit`, `enabled_modules_json`.
2. **`users`**: `id`, `school_id`, `email`, `phone`, `password_hash`, `role` (`superadmin`, `admin`, `principal`, `accountant`, `teacher`, `parent`, `student`), `is_active`.
3. **`parent_student_links`**: `parent_user_id`, `student_id`, `relationship` (enforces strict row-level security for Parent Portal queries).
4. **`academic_sessions`, `classes`, `sections`, `subjects`**: Normalized academic hierarchy with foreign keys to `staff(id)` for class and subject teachers.
5. **`students` & `admissions`**: Indexed on `(school_id, admission_no)` with `UNIQUE` constraints preventing duplicate admission numbers under concurrent clerk entry.
6. **`attendance_student` & `attendance_staff`**: Partitioned by academic year; unique constraint on `(student_id, attendance_date)`.
7. **`fee_structures`, `fee_challans`, `fee_challan_items`, `fee_payments`**:
   - Wrap payment insertion + challan balance update + `ledger_transactions` insertion inside a single **SQL `BEGIN ... COMMIT` transaction** so partial failures can never desynchronize the cashbook.
8. **`exams`, `exam_datesheets`, `exam_marks`**: Unique constraint on `(exam_id, student_id, subject_id)` with `CHECK (marks_obtained >= 0 AND marks_obtained <= max_marks)`.
9. **`staff`, `staff_leaves`, `payroll_slips`**: Linked to `ledger_transactions` on salary disbursement.
10. **`timetable_slots`**: Database exclusion/unique indexes on `(school_id, day_of_week, period_no, teacher_id)` and `(school_id, day_of_week, period_no, class_id, section)` to guarantee zero race-condition conflicts.
11. **`inventory_items`, `inventory_movements`, `vehicles`, `vehicle_maintenance`, `library_books`, `library_issues`, `homework`, `notices`, `audit_logs`**.

---

## 3. External Integrations for Pakistani Schools

### A. Pakistani Digital Fee Collection (1Bill / JazzCash / Easypaisa)
- **1Link / 1Bill Aggregator (Kuickpay / PayPro / Swich):** Generate a unique 20-digit 1Bill consumer number per challan so parents can pay from any Pakistani banking app (HBL, Meezan, UBL, Alfalah, SadaPay, NayaPay).
- **Webhook Handler (`POST /api/v1/webhooks/payment`):** Verify HMAC-SHA256 signature from JazzCash/Easypaisa/1Bill, mark the challan `Paid`, insert the ledger entry, and trigger a digital receipt notification.

### B. Online QR Verification for Printed DMCs & Fee Challans
- Replace the offline SVG QR design placeholder on printed DMCs with a signed verification URL:  
  `https://verify.schoolpro.org/dmc/{uuid}?sig={hmac}`
- Scanning the QR opens a read-only public verification page displaying the student's official marks fetched from the school server to prevent forged result cards.

### C. Biometric & RFID Attendance Bridge
- Deploy a lightweight local Windows/Linux agent on the school receptionist PC using `node-zklib` / TCP port `4370` to read ZKTeco fingerprint/RFID punches and push signed batches to `POST /api/v1/attendance/biometric-webhook` (with offline SQLite queuing during campus internet/power outages).

### D. Bilingual SMS & WhatsApp Notifications
- Integrate branded Masking SMS (e.g., Jazz Business / Telenor Corporate SMS gateways in Pakistan) and **WhatsApp Cloud API** using the pre-built English and Urdu (`اردو`) templates already structured inside SchoolPro AI.

---

## 4. Deployment & Operations Checklist

1. Containerize via `Docker Compose` (`app`, `postgres`, `minio`, `caddy/nginx` with automatic Let's Encrypt HTTPS).
2. Configure automated nightly `pg_dump` encrypted backups to off-site object storage.
3. Enable rate limiting on `/api/v1/auth/login` and public admission inquiry endpoints.
4. Keep the core repository 100% open-source (MIT / AGPLv3) with a 1-command demo seeder matching the fictional dataset in `index.html`.
