# Attendence-Tracker
A local-first, single-file web app for tracking college attendance across the academic year — subjects, timetable, calendar history, and analytics, with zero backend and zero build step.
# 📊 AttendEase — Student Attendance Tracker

A modern, mobile-first student attendance tracking application designed to help college students monitor attendance throughout an academic year.

AttendEase makes it easy to record daily attendance, calculate percentages, track Present/Absent classes, monitor subject-wise performance, plan safe bunking, analyze attendance trends, and export reports.

> **Design inspiration:** The UI/UX is inspired by modern attendance applications such as Bunk Paglu, while using original branding, components, and implementation.

---

## ✨ Features

### 📱 Dashboard
- Overall attendance percentage
- Total classes conducted
- Total classes attended
- Total classes absent
- Today's classes
- Subject-wise attendance cards
- Safe / Risky / Critical status
- Quick attendance marking

### 📚 Subject Management
- Add, edit, and delete subjects
- Subject code and faculty details
- Custom attendance target
- Classes-per-week configuration
- Custom subject colors
- Subject-specific attendance history

### ✅ Attendance Tracking
- Mark classes as **Present**
- Mark classes as **Absent**
- Mark days as **No Class**
- Edit historical attendance
- View attendance history
- Prevent duplicate attendance records
- Attendance updates reflected across the entire application

### 🎯 Smart Target Calculations
The application automatically determines:

- Current attendance percentage
- Classes required to reach the target
- Number of classes that can safely be missed
- Whether attendance is Safe, Risky, or Critical

Example:

```text
Present: 30
Absent: 10
Total: 40

Attendance = 30 / 40 × 100
           = 75.0%
```

### 📅 Attendance Calendar
- Monthly attendance calendar
- Color-coded Present / Absent / No Class days
- Select a date to update attendance
- Historical attendance editing
- Notes for attendance records

### 🗓️ Timetable
- Weekly timetable
- Subject-wise schedule
- Period and time information
- Room number
- Add, edit, and delete timetable entries
- Quick access to today's classes

### 📈 Analytics
- Overall attendance statistics
- Monthly attendance charts
- Subject-wise analysis
- Attendance trends
- Safe / Risky / Critical subject classification
- 1-month, 3-month, 6-month, and academic-year views

### 💡 Attendance Insights
Provides deterministic insights based on attendance calculations.

For example:

> "Your attendance is 84.6%. You are comfortably above your 75% target. You can miss 1 upcoming class."

Or:

> "Your attendance is 62.5%. You are below your 75% target. You need to attend the next 4 classes to recover."

### 📄 Export
Export attendance information as:
- PDF report
- CSV
- Spreadsheet-compatible data

Reports can include:
- Student name
- Academic year
- Subject
- Present classes
- Absent classes
- Total classes
- Attendance percentage
- Target percentage
- Attendance status

### ⚙️ Settings
- Dark / Light / System theme
- Default attendance target
- Academic year
- Attendance reminders
- Low-attendance alerts
- Data export
- Data import
- Reset all data

### 💾 Local-First Storage
- Attendance data persists after refresh
- No account required for the initial version
- Designed so cloud synchronization can be added later

---

## 🎨 UI/UX

AttendEase follows a **dark-mode-first, mobile-first** design approach.

### Design principles

- Clean dark interface
- Rounded cards
- Clear typography
- Minimal visual clutter
- Color-coded attendance states
- Touch-friendly controls
- Responsive layouts
- Subtle animations
- Accessible interactions

### Attendance status colors

| Status | Meaning |
|---|---|
| 🟢 Green | At or above target |
| 🟠 Orange | Near target / Risky |
| 🔴 Red | Below target / Critical |
| ⚪ Gray | No Class |

On mobile, the application uses a bottom navigation bar.

On desktop, the same navigation is presented as a sidebar.

---

## 🧮 Attendance Calculation

Attendance is calculated using:

```text
Attendance % = (Present Classes / Total Conducted Classes) × 100
```

Where:

```text
Total Conducted Classes = Present + Absent
```

**No Class records are excluded from the calculation.**

### Examples

```text
30 Present / 40 Total = 75.0%

50 Present / 60 Total = 83.3%

5 Present / 8 Total = 62.5%

11 Present / 13 Total = 84.6%
```

Percentages are displayed to one decimal place.

---

## 🎯 Target Recovery Calculation

If attendance is below the selected target, AttendEase calculates the minimum number of consecutive classes that must be attended.

For a target `T`, current present classes `P`, and current absent classes `A`:

```text
(P + x) / (P + A + x) >= T
```

where `x` is the minimum number of future classes that must be attended.

Similarly, when attendance is above target, the application calculates how many consecutive classes can be missed while still satisfying:

```text
P / (P + A + x) >= T
```

The calculation engine handles edge cases such as:
- 0 attendance records
- 100% attendance
- 0% attendance
- Attendance exactly at target
- No Class records

---

## 🏗️ Project Structure

A recommended project structure is:

```text
src/
├── components/
│   ├── attendance/
│   ├── analytics/
│   ├── dashboard/
│   ├── timetable/
│   ├── subjects/
│   └── ui/
│
├── pages/
│   ├── Dashboard.tsx
│   ├── Attendance.tsx
│   ├── SubjectDetails.tsx
│   ├── Timetable.tsx
│   ├── Analytics.tsx
│   └── Settings.tsx
│
├── hooks/
│   └── ...
│
├── lib/
│   ├── attendance.ts
│   ├── calculations.ts
│   ├── storage.ts
│   └── utils.ts
│
├── types/
│   └── attendance.ts
│
├── data/
│   └── demoData.ts
│
└── App.tsx
```

The exact structure may vary depending on the implementation.

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| React | Frontend framework |
| TypeScript | Type-safe development |
| Vite | Development/build tooling |
| Tailwind CSS | Styling |
| shadcn/ui | UI components |
| Lucide React | Icons |
| Recharts | Analytics and charts |
| date-fns | Date manipulation |
| LocalStorage / IndexedDB | Local persistence |

---

## 🚀 Getting Started

### Prerequisites

Make sure you have installed:

- Node.js
- npm

Check your versions:

```bash
node --version
npm --version
```

---

### Installation

Clone the repository:

```bash
git clone <YOUR_REPOSITORY_URL>
```

Move into the project directory:

```bash
cd attendance-tracker
```

Install dependencies:

```bash
npm install
```

---

### Run Development Server

```bash
npm run dev
```

Vite will provide a local URL similar to:

```text
http://localhost:5173
```

Open the URL in your browser.

---

## 🏭 Production Build

Create a production build:

```bash
npm run build
```

Preview the production build locally:

```bash
npm run preview
```

---

## 🧪 Testing

Before deployment, verify:

- [ ] Subject creation
- [ ] Subject editing
- [ ] Subject deletion
- [ ] Present marking
- [ ] Absent marking
- [ ] No Class handling
- [ ] Historical attendance editing
- [ ] Attendance percentage calculation
- [ ] Target calculation
- [ ] Safe bunk calculation
- [ ] Recovery calculation
- [ ] Overall analytics
- [ ] Monthly analytics
- [ ] Academic-year analytics
- [ ] Timetable creation
- [ ] Timetable editing
- [ ] Data persistence
- [ ] Export functionality
- [ ] Theme switching
- [ ] Mobile responsiveness
- [ ] Desktop responsiveness

---

## 🗃️ Data Model

### Subject

```typescript
interface Subject {
  id: string;
  name: string;
  code?: string;
  faculty?: string;
  color?: string;
  targetPercentage: number;
  classesPerWeek?: number;
  createdAt: string;
}
```

### Attendance Record

```typescript
interface AttendanceRecord {
  id: string;
  subjectId: string;
  date: string;
  status: "present" | "absent" | "no-class";
  notes?: string;
}
```

### Timetable Entry

```typescript
interface TimetableEntry {
  id: string;
  subjectId: string;
  day: string;
  startTime: string;
  endTime: string;
  room?: string;
}
```

### Academic Year

```typescript
interface AcademicYear {
  id: string;
  name: string;
  startDate: string;
  endDate: string;
}
```

---

## 📊 Example Workflow

A typical student workflow:

```text
Open Dashboard
      ↓
View Today's Classes
      ↓
Mark Present / Absent
      ↓
Attendance automatically recalculates
      ↓
Subject status updates
      ↓
Overall attendance updates
      ↓
Analytics update
      ↓
Target calculator updates
```

---

## 📱 Mobile Experience

The application is designed primarily for smartphones.

The mobile experience includes:

- Bottom navigation
- Floating Add Subject button
- One-tap attendance marking
- Touch-friendly cards
- Compact analytics
- Swipe-friendly interactions
- Responsive calendar
- Responsive timetable

---

## 🖥️ Desktop Experience

On larger screens:

- Sidebar navigation
- Multi-column dashboard
- Larger analytics charts
- Expanded timetable
- More information visible simultaneously

---

## 🔐 Privacy

The initial version is designed as a local-first application.

Attendance records can remain stored locally in the browser without requiring an account.

If cloud synchronization is added in the future, authentication, data encryption, permissions, and secure storage should be implemented appropriately.

---

## 🔮 Future Enhancements

Potential future features include:

- 🔐 User authentication
- ☁️ Cloud synchronization
- 📲 Push notifications
- 🔔 Smart attendance reminders
- 📆 Calendar integration
- 🏫 College timetable import
- 🤖 Predictive attendance analytics
- 📊 Advanced semester comparison
- 👨‍🏫 Faculty mode
- 👥 Shared/class attendance
- 💾 Backup and restore
- 📱 Installable PWA
- 🌐 Multi-device synchronization
- 📥 Import attendance from spreadsheets

---

## 🎯 Product Vision

AttendEase aims to make attendance management simple enough that a student can answer these questions instantly:

> **What is my attendance?**

> **How many classes have I attended?**

> **How many have I missed?**

> **Which subjects are below 75%?**

> **How many classes do I need to attend to recover?**

> **How many classes can I safely miss?**

> **What classes do I have today?**

> **Is my attendance improving or getting worse?**

---

## 📌 Design Reference

The application takes visual and UX inspiration from:

**Bunk Paglu – Track Attendance**

https://play.google.com/store/apps/details?id=com.jagadish.attendance&hl=en_IN

The implementation should remain independently branded and designed.

---

## 👩‍💻 Development

Built as a student-focused attendance management project with emphasis on:

- Clean UI/UX
- Accurate calculations
- Responsive design
- Maintainable React architecture
- Local-first data management
- Practical everyday usability

---

## 📄 License

Add the appropriate license for your project here.

For example:

```text
MIT License
```

if the project is intended to be open source under MIT.
