# SchoolPro AI — Complete Open-Source School Management System

> **Tagline:** *Smart Management. Better Education.*
> **Deliverable Type:** Single-File Browser Application (`index.html`) with `localStorage` Persistence

---

## 1. Overview

**SchoolPro AI** is a complete, responsive, browser-based school administration and academic ERP built specifically with Pakistani school workflows, terminology (`Admission No`, `Challan`, `DMC`, `PKR / Rs.`, `English + Urdu notices`), and non-technical clerical ease-of-use in mind.

### Open-Source & Zero-Subscription Philosophy
SchoolPro AI contains **no paid plans, no subscription tiers, no per-student pricing, and no feature paywalls**. Instead, it includes an open-source **Super Admin Demo Access Controller** for managing evaluation environments, demo durations, usage limits, and module visibility. *(Note: School student fee collection and challan management remain 100% available as core school operations.)*

---

## 2. How to Open & Run

No server, database installation, Node.js, PHP, or build step is required:

1. Locate `index.html` in the project folder.
2. Double-click `index.html` (or right-click → **Open With** → Chrome, Edge, Firefox, Safari, or Android Chrome).
3. On the login screen, either:
   - Click any of the **7 Instant 1-Click Role Demo Portal** buttons (`School Admin`, `Super Admin`, `Principal`, `Accountant`, `Teacher`, `Parent`, `Student`), **or**
   - Enter a demo email (e.g., `admin@schoolpro.edu.pk`) and password (`demo123`) and click **Access Portal**.

---

## 3. Role Accounts

Same 7 roles (Super Admin, School Admin, Principal, Accountant, Teacher, Parent, Student) - use the login buttons or the Role Switcher. Teacher / Parent / Student portals ask you to **pick a profile** (teacher or student) the first time, because the database starts empty.

## 4. Clean Start, Backup & Reset

- **No sample data:** the database starts empty. Only **Nursery, Prep, Class 1 to Class 10** and a default **class-wise subject list** are pre-filled.
- Data is saved in `localStorage` under `schoolpro_ai_db_v2` (old v1 sample data is ignored).
- **Getting Started** card on the dashboard guides first setup (school info, fee structure, staff, students).
- **New:** Fee Structure tab (all classes in one table), class-wise subjects, Students CSV import with template, Student ID Cards, School Leaving & Character certificates.
- **JSON Backup / Reset:** Settings or profile menu. Reset now clears everything to the empty database.

## 5. Printing A4 Documents & Exporting CSV

- **A4 Print Layouts:** Clicking any `Print` button (Dual-Copy Fee Challan, Official Fee Receipt, Detailed Marks Certificate [DMC] with QR placeholder, Roll Number Slips, Salary Slip, Student Profile, Staff Profile, Attendance Register, Timetable, or any of the 14 Reports) opens an **A4 Print Preview** modal with a **Print / Save A4 PDF** action styled via `@media print`.
- **CSV Downloads:** Every export button generates a UTF-8 BOM-encoded `.csv` file ready for Microsoft Excel or Google Sheets.
