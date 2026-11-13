# SchoolPro AI — Complete Feature Inventory

This document lists all implemented modules, workflows, calculations, portals, and integration-ready placeholders inside `index.html`.

---

## 1. Brand, Shell & Navigation
- **Original Identity:** Bespoke inline SVG **SchoolPro AI** academic shield/mortarboard crest in Burgundy (`#7A1C32`), Scholarly Navy (`#0F1E36`), and Academic Gold (`#C89B3C`).
- **Responsive Layout:** Collapsible categorized sidebar, mobile slide-over drawer with backdrop, sticky top navigation bar, light/dark theme toggle, and optional bilingual (`English + اردو`) sidebar labels.
- **Global Search:** Real-time role-aware search across modules, students, staff, and fee challans.
- **Notifications Drawer:** Unread notice counter, low-stock inventory alert banner, mark-all-read action, and direct module jump links.
- **Zero Pricing / Zero Subscriptions:** Open-source edition with **no** paid tiers, package builders, or software billing screens.

---

## 2. Executive Dashboard
- **Period Filters:** `Today`, `This Week`, `This Month`, `This Year` dynamically recalculating financial metrics.
- **15 Live Metrics & Widgets:** Total Students, Active Students, Total Teachers, Total Staff, Today's Attendance %, Absent Students Today, Today's Fee Collection, Monthly Fee Collection, Pending Fees, Period/Total Expenses, Monthly Income, Upcoming Examinations, Recent Admissions, Recent Fee Payments, and Live Activity Audit Feed.
- **5 Interactive Charts (Chart.js + Offline Fallback):**
  1. Income vs. Expenses Comparison
  2. Today's Attendance Doughnut (`Present`, `Absent`, `Late`, `Leave`)
  3. Class-wise Student Distribution
  4. Monthly Fee Collection Trend
  5. Session-wise Student Enrollment Growth

---

## 3. Student Management & 6-Tab Dossier
- **Directory & Filters:** Search by name, Student ID, Admission #, Roll #, or Father's name; filter by Class, Section, Academic Session, and Status.
- **Full CRUD & Lifecycle:** Register student (with optional photo upload, transport route, and discount/scholarship), Edit, Delete with confirmation, Promote, Transfer, Withdraw, Re-admit, Print A4 Student Profile, and Export CSV.
- **6-Tab Student Profile View:**
  1. Personal Information
  2. Academic Progression History
  3. Attendance Percentage & Daily Log
  4. Fee Challans & Balance Summary
  5. Examination Results & 1-Click A4 DMC Print
  6. Verified Admission Documents Manager

---

## 4. Admission Management
- Stage counters & filters (`All`, `Inquiry`, `Pending`, `Approved`, `Enrolled`, `Rejected`).
- Admission inquiry & application form with validation.
- Approval/rejection workflow + **1-Click Confirm Admission & Generate Admission Number** (`ADM-2026-XXX`) that automatically creates an enrolled student record.
- CSV export of admission applications.

---

## 5. Class & Academic Management
- Create, edit, and delete **Classes** (with multiple sections, seat capacity bar, class teacher, and default PKR fee heads).
- Create, edit, and delete **Subjects** (code, assigned subject teacher, total marks, passing marks).
- **Academic Sessions** manager & **Bulk Class Promotion Wizard**.
- **Academic Calendar & School Holidays** manager.

---

## 6. Attendance Management
- **Student Daily Register:** Filter by Class, Section, and Date; mark `Present`, `Absent`, `Late`, `Leave`, or `Unmarked`; **Mark All Present**, **Mark All Absent**, Save/Update, and **Print A4 Attendance Register**.
- **Absentee List & Monthly Summary:** Instant absentee follow-up cards with guardian phone numbers + cumulative student attendance percentages.
- **Staff Attendance:** Daily staff status controls and 1-click **Mark All Staff Present**.
- **Biometric Integration Info:** Honestly labelled webhook schema placeholder for future ZKTeco/RFID bridge services.

---

## 7. Fee Management (PKR)
- **Fee Structures & Concessions:** Class-wise Tuition, Admission, Annual, and Exam fees + Transport fees, Custom charges, Sibling Discounts (20%), Merit Scholarships (25%), and Fee Concessions (50%).
- **Challan Generation:** Individual/Custom Challan generator + **Bulk Monthly Class/School Challan Generator** (with duplicate-month guard).
- **Payments & Ledger Sync:** Cash, Bank Deposit, and Cheque/Other payment recording supporting both **Partial** and **Full** payments, automatically posting `Student Fee Income` vouchers into the Accounts Cashbook.
- **Defaulters Desk:** Unpaid, partial, and overdue accounts filterable by class + CSV export.
- **Printable A4 Documents:** Dual-copy A4 School/Student **Fee Challan** and Official A4 **Fee Payment Receipt**.
- **Gateway Note:** Honest placeholder noting future backend requirements for JazzCash, Easypaisa, and 1Bill APIs.

---

## 8. Examination & Result Management
- Create examinations with auto-drafted subject **Date Sheets** and printable **Roll Number Slips**.
- **Marks Entry & Editing Grid:** Class/section matrix across all subjects with max-marks clamping and instant recalculation.
- **Automated Calculations:** Subject pass/fail check, total obtained marks, percentage, letter grade (`A+`, `A`, `B`, `C`, `D`, `F`), class rank/position calculation, top-3 Merit Podium, pass rate %, class average, and subject-wise averages.
- **Printable A4 DMC Result Card:** Official Detailed Marks Certificate featuring an inline SVG **QR Verification Design Placeholder** (clearly labelled offline demo design).

---

## 9. Staff, HR & Payroll Management
- **Staff Directory:** Teaching and non-teaching registration, edit, deactivate/activate, search/filter, and printable A4 HR profile.
- **Leave Workflow:** Submit leave applications (`Casual`, `Medical`, `Earned`, `Emergency`) with date validation and Approve/Reject actions.
- **Payroll Engine:** `Net Salary = Basic Salary + Allowances + Bonus - Deductions - Loan/Advance`, live preview calculator, **Pay Salary** action (auto-syncs `Salary Expenses` to Accounts Ledger), and printable A4 **Employee Payslip**.

---

## 10. Accounts, Inventory, Timetable, Transport & Library
- **Accounts & Finance:** Cash In (`Income`), Cash Out (`Expense`), daily/monthly/yearly filters, ledger head summary, chronological running balance Cashbook, P&L surplus/deficit calculation, and printable A4 Ledger.
- **Inventory & Stationery:** 10 preloaded stationery & campus asset SKUs, Low Stock Alert banner, Purchase (`+`), Issue/Sale (`-` with stock sufficiency guard), Stock Adjustment, movement logs, and CSV export.
- **Timetable Management:** Class and Teacher weekly grids (Mon–Sat × 6 Periods) with **Real-Time Conflict Detection** (blocks teacher, class, and room double-bookings) + printable A4 Timetable.
- **Transport Management:** Fleet vehicles, drivers, route stops, seat capacity enforcement, student route allocation, and vehicle maintenance logs.
- **Library Management:** ISBN book catalog, copy availability counter, Issue Book, Return Book, and automatic Overdue detection.

---

## 11. Role-Scoped Portals, Bilingual Notices, 14 Reports & Super Admin
- **Parent Portal:** Strictly scoped to linked children (`STU-001` & `STU-007`) — profile, attendance, fee challans/receipts, published exam DMCs, timetable, homework, and notices.
- **Teacher Portal:** Strictly scoped to logged-in teacher (`STF-001`) — assigned classes/students, timetable, attendance marking, subject marks entry, homework CRUD, class notices, leave requests, and personal payslips.
- **Student Portal:** Strictly scoped to logged-in student (`STU-001`) — own profile, attendance, exam schedule/DMC, timetable, homework, fee status, and notices.
- **Communication Center:** Targeted announcements + 4 one-click **English & Urdu (`اردو`)** notification templates.
- **Reports Center:** All **14 dedicated reports** with date/class/session/keyword filters, A4 Print, and CSV export.
- **Super Admin Panel:** Open-source demo school accounts table, start/expiry extension (`+30d`), activation toggle, student usage limits, dynamic module ON/OFF switches, RBAC role permission matrix, activity logs, JSON backup, and factory reset.


---

## 12. Latest Update - Clean Start, Nursery to Class 10
- All sample records removed (students, staff, fees, exams, accounts, vehicles, books, notices, demo schools).
- Classes: Nursery, Prep, Class 1-10. Subjects can be limited to chosen classes (exams, marks grid, results and DMC use only that class's subjects).
- Fee Structure setup tab, bulk Students CSV import (+ template), printable Student ID Cards, School Leaving / Character certificates, Getting Started checklist, profile picker for Teacher/Parent/Student portals.
