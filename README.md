# CourseMaster — Modern E-Learning Platform

[![React](https://img.shields.io/badge/React-19.2.0-blue.svg?logo=react)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-7.2.6-646CFF.svg?logo=vite)](https://vitejs.dev/)
[![Redux Toolkit](https://img.shields.io/badge/Redux%20Toolkit-2.11.0-764ABC.svg?logo=redux)](https://redux-toolkit.js.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-v4.1.17-38B2AC.svg?logo=tailwind-css)](https://tailwindcss.com/)
[![DaisyUI](https://img.shields.io/badge/DaisyUI-v5.5.8-5A0EF8.svg)](https://daisyui.com/)
[![ESLint](https://img.shields.io/badge/ESLint-Clean%20(0%20errors)-4B32C3.svg?logo=eslint)](https://eslint.org/)

CourseMaster is a full-featured, responsive E-learning web application built with React 19, Vite, Redux Toolkit, and Tailwind CSS. It enables students to explore industry-aligned courses, enroll, stream video lectures, submit assignments, and take quizzes with instant scoring. Platform administrators can manage courses, batches, live video sessions, student submissions, and user accounts through an interactive analytics dashboard.

---

## 📌 Links & Demo Credentials

- **Live Application**: [https://course-master4981.netlify.app/](https://course-master4981.netlify.app/)
- **Demonstration Video**: [Google Drive Video Walkthrough](https://drive.google.com/file/d/1vjMrBxr0-7xqjxMX2EBEBw30D_av1pOu/view)
- **Detailed Bug Report**: [BUG_REPORT.md](./BUG_REPORT.md)

### Test Accounts

| Role | Email | Password | Access Area |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin@coursemaster.com` | `admin123` | Full Admin Portal (`/admin`) |
| **Student** | `student@coursemaster.com` | `student123` | Student Dashboard (`/student`) |

> *Note: Direct dev bypass is also integrated on the Login page for rapid grading and route testing.*

---

## 🛠️ Bug-Bashing & Quality Assurance Summary

During systematic quality assurance and bug-bashing across all 8 architectural domains, **18 bugs** were documented and resolved. For full step-by-step reproduction instructions, root causes, severity metrics, and verification evidence, see [BUG_REPORT.md](./BUG_REPORT.md).

### Resolved Issues Overview

| Bug ID | Title | Category | Severity | Resolution Summary |
| :--- | :--- | :--- | :---: | :--- |
| **BUG-001** | Token Storage Key Mismatch | Auth & Storage | Critical | Synchronized `token` and `user_token` keys in `auth.js` to ensure session persistence across reloads. |
| **BUG-002** | Missing `Bearer ` Scheme in Headers | API Integration | High | Added standard `Bearer <token>` formatting to Axios interceptor. |
| **BUG-003** | Redux `.data` Mutation Crash | Data Handling | Critical | Corrected `action.payload` array handling in `enrollmentSlice` to eliminate white-screen crash. |
| **BUG-004** | Progress Displays `NaN%` | Data Display | High | Replaced division-by-undefined with verified `enrollment.progress.percent` fallback. |
| **BUG-005** | Distorted 300x700px Video Player | UI/UX | High | Restored responsive 16:9 widescreen player (`aspect-video w-full`) in Course Player. |
| **BUG-006** | "Mark as Complete" State Loss | Functional Bug | Medium | Updated comparison logic to evaluate `lesson._id` string instead of object reference. |
| **BUG-007** | Radio Button Mutual Collision in Quizzes | Functional Bug | High | Dynamically scoped radio inputs by question index (`quiz-question-${qIdx}`). |
| **BUG-008** | 100x Course Price Multiplier | Data Display | Medium | Removed artificial `* 100` multiplier in Course Details (`৳ 4,500` instead of `৳ 450,000`). |
| **BUG-009** | Navbar Highlights All Links Simultaneously | UI/UX | Medium | Fixed `navLinkClass` to strictly check `isActive` state. |
| **BUG-010** | Course Card Title Text Overflow | UI/UX | Low | Replaced `whitespace-nowrap` with `line-clamp-2` for multi-line card titles. |
| **BUG-011** | Mobile Navbar Truncated by `max-h-32` | Mobile UI | High | Replaced height restriction with `max-h-[85vh] overflow-y-auto`. |
| **BUG-012** | Inverted Enrollment Logic (Backend Code-9) | Backend | Critical | Corrected `!enrollment` condition in `enrollment.service.js` to allow new student enrollments. |
| **BUG-013** | Plaintext Password Equality (Backend Code-5) | Backend Auth | Critical | Restored `bcrypt.compare` in `auth.service.js` so registered users can log in. |
| **BUG-014** | Quiz Score Formula Multiplies by 10 (Code-4) | Backend Logic | High | Fixed quiz percentage formula to multiply by 100 instead of 10. |
| **BUG-015** | Assignment Filter Queries `courseId` (Code-8) | Backend DB | Medium | Fixed MongoDB query to use schema reference field `course`. |
| **BUG-016** | Dark Mode Unreadable Email Text | UI/UX | Low | Replaced hardcoded `#1e293b` with DaisyUI adaptive token `text-base-content/80`. |
| **BUG-017** | Invalid DOM Nesting (`<div>` inside `<p>`) | React Standards | Low | Replaced outer `<p>` wrapper with `<div>` to eliminate hydration warnings. |
| **BUG-018** | ESLint State-in-Effect & Unused Variables | Code Quality | Low | Resolved all React 19 cascading re-render warnings; achieved 0 lint errors. |

---

## 💻 Tech Stack

- **Framework**: [React 19](https://react.dev/)
- **Build Tool**: [Vite 7](https://vitejs.dev/) with Hot Module Replacement (HMR)
- **State Management**: [@reduxjs/toolkit](https://redux-toolkit.js.org/) & [react-redux](https://react-redux.js.org/)
- **Routing**: [React Router DOM v7](https://reactrouter.com/) (Protected & Nested layouts, Suspense Code-Splitting)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/) & [DaisyUI v5](https://daisyui.com/)
- **Icons**: [Lucide React](https://lucide.dev/)
- **Charts & Visualizations**: [Recharts](https://recharts.org/)
- **HTTP Client**: [Axios](https://axios-http.com/) with centralized interceptors

---

## 🚀 Getting Started Locally

### Prerequisites
- [Node.js](https://nodejs.org/) (version 18 or higher recommended)
- [npm](https://www.npmjs.com/)

### Installation & Run

1. **Clone the repository**:
   ```bash
   git clone <your-repository-url>
   cd courseMaster_frontEnd
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure Environment Variables**:
   Create a `.env` file in the root directory:
   ```env
   VITE_API_BASE_URL=https://course-master-backend-ochre.vercel.app/api
   ```
   *(For local backend development, set `VITE_API_BASE_URL=http://localhost:5000/api`)*

4. **Start Development Server**:
   ```bash
   npm run dev
   ```
   The application will be accessible at `http://localhost:5173/`.

5. **Linting & Code Quality**:
   ```bash
   npm run lint
   ```
   *(Runs ESLint across all files with 0 errors / 0 warnings)*

6. **Production Build**:
   ```bash
   npm run build
   npm run preview
   ```

---

## 📂 Project Architecture

```
courseMaster_frontEnd/
├── public/                 # Static public assets
├── src/
│   ├── assets/             # Brand logos and images
│   ├── components/         # Modular and reusable UI components
│   │   ├── CourseCard/     # Course card, filtering, pagination, and grid
│   │   ├── Home/           # Hero section and course preview components
│   │   └── shared/         # Navbar, Footer, Logo, ThemeToggle
│   ├── contexts/           # ThemeContext (light/dark theme switching)
│   ├── layouts/            # MainLayout (header, main container, footer)
│   ├── pages/              # Application views
│   │   ├── admin/          # Admin pages (Analytics, Courses, Users, Video Classes)
│   │   ├── CoursePlayer/   # Widescreen video lecture player, quizzes, assignments
│   │   ├── CousrseDetails/ # Course curriculum overview, enrollment actions
│   │   ├── Courses/        # Searchable and filterable course catalog
│   │   ├── Home/           # Landing page with hero banner & previews
│   │   ├── Login/          # User authentication with demo helpers
│   │   ├── NotFound/       # 404 error page
│   │   ├── Register/       # Student registration flow
│   │   └── student/        # Student dashboard with enrolled courses & progress
│   ├── routes/             # ProtectedRoute and AdminRoute guards
│   ├── services/           # Axios API services (auth, courses, admin, quiz, etc.)
│   ├── store/              # Redux Toolkit store and slices (auth, courses, enrollment, admin)
│   └── utils/              # LocalStorage auth token utilities
├── BUG_REPORT.md           # Complete QA bug identification & resolution report
├── package.json            # Scripts and dependencies
└── vite.config.js          # Vite build config with vendor chunk code splitting
```

---

## ✨ Key Features

### 🎓 Student Features
- **Course Discovery**: Search by keyword/instructor, filter by category or tag, and sort by price.
- **Widescreen Video Player**: Responsive 16:9 lecture playback integrated with YouTube.
- **Progress Tracking**: Check off lessons, track completion percentages in real time.
- **Interactive Quizzes**: Take lesson quizzes with isolated question controls and instant score feedback.
- **Assignment Submissions**: Submit text or Google Drive project links for instructor grading.
- **Student Dashboard**: View all enrolled courses, jump back into learning, and monitor achievements.

### 👑 Administrator Features
- **Course Management**: Create new courses, define syllabus modules, lessons, video URLs, quizzes, and live classes.
- **User Management**: Inspect registered users, toggle administrative roles, and ban/unban accounts.
- **Assignment Reviewing**: Grade student submissions (0–100) and provide qualitative instructor feedback.
- **Live Video Classes**: Schedule Google Meet sessions and associate meeting links with specific lessons.
- **Interactive Analytics**: Visualize enrollment trends over time (Recharts) and revenue statistics.

---

## 🛡️ License

This project is licensed for educational and academic assessment purposes.
