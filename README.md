
# Smart Appointment System

*A full-stack web application for scheduling and managing appointments between patients and doctors.*

## Project Overview

Smart Appointment is designed to streamline the entire process of registering users (patients, doctors, admins), booking appointments, managing availability, and monitoring status – all with a clean and responsive UI plus secure backend services.
It demonstrates a real-world full-stack solution using modern web technologies.

## Architecture

```
 ┌───────────────┐       ┌───────────────────┐       ┌───────────────┐
 │   Frontend    │ ───▶  │   REST API /      │ ───▶  │   Database    │
 │  React + Vite │       │  Backend (Node.js)│       │  MongoDB      │
 └───────────────┘       └───────────────────┘       └───────────────┘
           ▲                        │                       ▲
           │        Authentication │                       │
           └────────────────────────┴───────────────────────┘
```

### Component Details

| Component | Technology         | Purpose                                 |
| --------- | ------------------ | --------------------------------------- |
| Frontend  | React.js (Vite)    | User interface for patients & doctors   |
| Backend   | Node.js + Express  | Business logic, API endpoints           |
| Database  | MongoDB + Mongoose | Data storage: users, appointments, etc. |
| Auth      | JWT                | Secure login & role-based access        |

## Features

* Role-based user accounts: **Admin**, **Doctor**, **Patient**
* Secure registration & login (JWT based)
* Doctor availability scheduling
* Patients can browse doctors and book appointments
* View and manage appointment history (patients & doctors)
* Responsive UI for both desktop and mobile use
* Admin dashboard for user- & appointment- management
* Future scope: Email/SMS notifications, analytics dashboards

## Prerequisites

Before you begin, ensure you have the following installed:

* Node.js (v14 or above)
* npm or yarn
* MongoDB (remote or local)
* Git

## Step-by-Step Setup Guides

### For Developers (Local Development)

#### 1. Clone the repository

```bash
git clone <your-repository-URL>
cd Smart-Appointment
```

#### 2. Setup backend

```bash
cd backend
npm install
```

Create a `.env` file in `backend/` folder with:

```env
PORT=5000
MONGO_URI=<your_mongodb_connection_string>
JWT_SECRET=<your_secret_key>
```

#### 3. Setup frontend

```bash
cd ../frontend
npm install
```

Create a `.env` (or `.env.local`) file in `frontend/` folder with:

```env
VITE_API_URL=http://localhost:5000
```

#### 4. Run both services

In two separate terminals:

```bash
# In backend/
npm start
```

```bash
# In frontend/
npm run dev
```

Open browser: `http://localhost:5173` (or the Vite default port)
Backend API: `http://localhost:5000/api`

### For End Users (Production or Demo)

#### System Requirements

* Linux / macOS / Windows (Docker optional)
* At least 4 GB RAM (8 GB preferred)
* 10 GB free disk space
* Access to MongoDB (cloud or local)

#### Installation & Configuration

1. Clone the repo and configure .env files as above.
2. Optionally build the frontend:

   ```bash
   cd frontend
   npm run build
   ```
3. Start services (manually or via PM2 / Docker in production).
4. Access the application through browser (frontend) and set up admin account first.

## Folder Structure

```
Smart-Appointment/
├── backend/
│   ├── config/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   └── server.js
└── frontend/
    ├── src/
    │   ├── components/
    │   ├── pages/
    │   ├── services/
    │   └── App.jsx
    ├── public/
    └── vite.config.js
```

## Configuration

### Backend

* `config/` – DB setup, middleware, authentication.
* `models/` – Mongoose schemas (User, Appointment, etc).
* `routes/` – API endpoints grouped by role (admin, doctor, patient).
* `controllers/` – Business logic for each route.

### Frontend

* `services/api.js` – Axios instance using `VITE_API_URL`.
* `pages/` – React pages (Login, Dashboard, Book Appointment, etc)
* `components/` – Reusable UI components (Navbar, Form inputs, etc)
* `pages/Admin`, `pages/Doctor`, `pages/Patient` – Role-specific views.

## Usage

* Register as **Patient** or **Doctor** (Admin can create doctor accounts).
* Doctor sets availability schedule.
* Patient selects doctor → picks slot → books appointment.
* Doctor views list of upcoming appointments and manages them.
* Admin views all users, appointments and can moderate or export data.

## Troubleshooting Guide

### 1. Backend won’t start

* Ensure `MONGO_URI` is correct and reachable.
* Check port `5000` isn’t blocked.
* Inspect logs: `npm start` → any errors

### 2. Frontend shows blank or fails to connect API

* Verify `.env` `VITE_API_URL` matches backend address.
* Browser console errors (CORS or 404) may hint misconfigured API base URL.

### 3. Authentication errors

* Ensure `JWT_SECRET` matches what backend expects.
* Cookies / localStorage issues: clear browser storage and retry login.

## Future Enhancements

* Email/SMS notifications for appointments
* Analytics dashboard for appointment trends
* Real-time chat between patients & doctors
* Multi-language / locale support
* Dockerize full stack for easier deployment
* Integrate third-party calendars (Google/Outlook)

---

## About

Smart Appointment System showcases your ability to design and implement a full-stack application with user roles, secure authentication, database interactions, and responsive frontend.
It aligns with your base in Java, IoT, and AI/ML, and can be extended further (e.g., add ML-based appointment prediction) as part of your portfolio.

## License

This project is licensed under the **MIT License** – feel free to use, modify and distribute with attribution.
