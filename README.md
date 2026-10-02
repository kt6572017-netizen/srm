# 🎓 MBA 2nd Year (3rd Semester) - Attendance Analytics Dashboard

> **Interactive attendance tracking, defaulters monitoring, and 75% eligibility recovery calculator built for SRM Institute of Science & Technology.**

---

## 🌟 Overview

This project automates the extraction, transformation, and interactive visualization of student attendance records from the official consolidated PDF (`ATTENDANCE 290926.pdf`). It features a **SaaS Dark Luxury UI** inspired by modern people management dashboards with vibrant accents, responsive metric cards, and a mathematical **75% Attendance Calculator**.

---

## 🚀 Key Features

* **📄 Automated PDF Parsing & ETL**:
  * Extracts all 174 course registrations across 29 students and 12 distinct subjects without layout truncation errors.
  * Exports clean, structured data to `attendance.csv` with calculated status (`Eligible` vs. `Shortage` based on the 75% requirement).
* **🎨 Modern SaaS Dark Theme**:
  * Deep sapphire canvas (`#0A0E1A`) with glassmorphic cards (`#131B2E`) and luminous neon accents.
  * Pill-style sidebar navigation with active violet-indigo gradient glow (`linear-gradient(135deg, #4F46E5, #7C3AED)`).
* **📊 Visual Executive Dashboard**:
  * **Statistics Donut Chart**: Centered student count with real-time eligibility percentage badge.
  * **6-Card Horizontal Metrics Row**: Instant status counters for *Eligible*, *Shortage*, *Defaulters*, *Students*, *Courses*, and *Class Average*.
  * **Variance vs. 75% Target Chart**: Color-coded deviations from the university requirement.
  * **Subject Performance Benchmarks**: Course ranking bar chart with top-performing subjects highlighted.
  * **2×2 Distribution & Exceptions Grids**: Fast breakdown of core courses, electives, severe shortages (<50%), and borderline cases (50–74%).
* **🧮 75% Attendance Eligibility Calculator**:
  * Calculates the exact number of **upcoming consecutive classes** a student must attend to reach or exceed 75%.
  * Interactive recovery curve plot and step-by-step projection simulation table.
  * Safety margin indicator for eligible students showing allowable missed classes.
* **⚠️ Defaulters Directory**:
  * Filterable table ranking all 20 students having shortage in one or more courses, with progress meters and detailed course codes.
* **👤 Student Report Card**:
  * Student-level lookup showing individual performance, course-by-course status badges, and overall averages.
* **📚 Subject Benchmarks**:
  * Subject-wise rankings from lowest to highest attendance with shortage counts.
* **📋 Master Records with CSV Export**:
  * Search by student name/register number, filter by course and status, and export filtered data in one click.

---

## 🧮 Attendance Recovery Mathematics

### 1. Reaching $\ge 75\%$ from Shortage ($< 75\%$)
Let:
* $A$ = Number of classes attended so far
* $T$ = Number of total classes held so far
* $x$ = Number of upcoming consecutive classes attended without missing any

To achieve an attendance percentage of at least $75\%$ ($0.75$):

$$\frac{A + x}{T + x} \ge 0.75$$

$$A + x \ge 0.75(T + x) = 0.75T + 0.75x$$

$$0.25x \ge 0.75T - A$$

$$x \ge \frac{0.75T - A}{0.25} = 3T - 4A$$

$$\mathbf{x = \max(0, \lceil 3T - 4A \rceil)}$$

### 2. Safety Margin (Allowable Missed Classes for $\ge 75\%$)
If a student is already eligible, the maximum number of classes $m$ they can miss while staying at or above $75\%$ is:

$$\frac{A}{T + m} \ge 0.75 \implies \mathbf{m = \left\lfloor \frac{4A - 3T}{3} \right\rfloor}$$

---

## 📊 Summary of Attendance Data

| Metric | Value |
| :--- | :--- |
| **Total Enrolled Students** | 29 students |
| **Total Course Registrations** | 174 records (6 per student) |
| **Total Unique Subjects** | 12 courses |
| **Class-Wide Average Attendance** | **70.16%** |
| **Eligible Registrations ($\ge 75\%$)** | 94 registrations (54.0%) |
| **Shortage Registrations ($< 75\%$)** | 80 registrations (46.0%) |
| **Total Defaulters (Shortage in $\ge 1$ Course)** | **20 students** (69.0%) |
| **Fully Eligible Students (All Clear)** | **9 students** (31.0%) |

---

## 📁 Repository Structure

```text
├── .streamlit/
│   └── config.toml             # Dark theme & server settings
├── ATTENDANCE 290926.pdf       # Raw source attendance report
├── attendance.csv              # Clean, processed attendance records
├── generate_attendance_csv.py  # Automated PDF parsing and ETL script
├── app.py                      # Main Streamlit dashboard application
├── requirements.txt            # Python dependencies
└── README.md                   # Project documentation & guide
```

---

## 🛠️ Setup & Installation

### 1. Prerequisites
* Python 3.10, 3.11, or newer
* Git (optional)

### 2. Clone or Navigate to the Project Directory
```powershell
cd "c:\Users\Riya\OneDrive\Desktop\srm"
```

### 3. Install Dependencies
```powershell
pip install -r requirements.txt
```

### 4. (Optional) Re-generate the CSV from PDF
If you update or replace `ATTENDANCE 290926.pdf`, run the ETL script:
```powershell
python generate_attendance_csv.py
```

### 5. Launch the Streamlit Dashboard
```powershell
streamlit run app.py
```

The application will start and provide a local URL:
* **Local Browser URL**: `http://localhost:8501`
* **Network URL**: `http://<your-local-ip>:8501`

---

## 🖥️ Navigation Views

1. **Dashboard**: High-level visual telemetry, donut statistics, variance indicators, and category breakdowns.
2. **Attendance**: Live registration cards and summary metrics.
3. **Defaulters List**: Complete directory of students with attendance below 75% in any registered subject.
4. **Attendance Calculator**: Interactive recovery tool with recovery trajectories and customizable percentage goals.
5. **Student Report Card**: Searchable individual student card with course breakdown.
6. **Subject Rankings**: Course-level ranking sorted by average attendance percentage.
7. **Master Records**: Tabular database view with search filters and CSV export.

---

## 📄 License
This project was developed for educational analytics and attendance management for the MBA program at SRM Institute of Science & Technology.
