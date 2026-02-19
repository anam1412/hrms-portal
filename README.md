# HRMS Lite – Human Resource Management System

A full-stack, production-ready **Human Resource Management System** built with **React + TypeScript** (frontend) and **FastAPI + Python** (backend), featuring a professional UI, real-time stats dashboard, employee management, and attendance tracking.

---

## 🚀 Live Demo
| Layer    | URL |
|----------|-----|
| Frontend | *(deploy to Vercel / Netlify)* |
| Backend  | *(deploy to Render / Railway)* |
| API Docs | `<backend-url>/docs` |

---

## ✨ Features

### Core
- **Dashboard** – Live attendance rate, stat cards, recent employees, quick-action shortcuts
- **Employee Management** – Add, search, filter by department, view details, delete (with cascade)
- **Attendance Tracking** – Mark attendance (Present / Absent / Late / Half Day), edit records, date-range filter

### Bonus
- ✅ Total present days shown per employee
- ✅ Filter attendance by date range, employee, and status
- ✅ Mini summary bar on attendance page (counts per status)
- ✅ Attendance rate progress bar on dashboard

### UX
- Toast notifications for all actions
- Confirmation dialogs before destructive actions
- Loading states, error states, and empty states
- Fully responsive (mobile sidebar, card-based mobile tables)

---

## 🛠 Tech Stack

| Layer     | Technology |
|-----------|-----------|
| Frontend  | React 18, TypeScript, Vite, Tailwind CSS |
| Icons     | Lucide React |
| Toast     | react-hot-toast |
| Routing   | React Router v7 |
| Dates     | date-fns |
| HTTP      | Axios |
| Backend   | Python 3.11+, FastAPI, SQLAlchemy |
| Database  | PostgreSQL 17 |
| Validation| Pydantic v2 |

---

## 📁 Project Structure

```
hrms/
├── backend/
│   ├── app/
│   │   ├── main.py          # FastAPI app + CORS + routers
│   │   ├── database.py      # SQLAlchemy engine & session
│   │   ├── models.py        # Employee & Attendance ORM models
│   │   ├── schemas.py       # Pydantic schemas & validation
│   │   └── routers/
│   │       ├── employees.py  # CRUD endpoints
│   │       ├── attendance.py # Mark/update/filter endpoints
│   │       └── dashboard.py  # Stats endpoint
│   ├── requirements.txt
│   └── .env
└── frontend/
    ├── src/
    │   ├── api/             # Axios API services
    │   ├── components/      # Reusable UI components
    │   │   ├── layout/      # Sidebar, Header, Layout
    │   │   ├── ui/          # Modal, Badge, Spinner, etc.
    │   │   ├── employees/   # Employee table & add modal
    │   │   └── attendance/  # Attendance table & mark modal
    │   ├── pages/           # Dashboard, Employees, Attendance
    │   ├── types/           # TypeScript interfaces
    │   └── App.tsx
    ├── tailwind.config.js
    └── package.json
```

---

## ⚡ Running Locally

### Prerequisites
- Python 3.11+
- Node.js 18+

### 1 – Backend

```bash
cd backend

# Create virtual environment
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # macOS/Linux

# Install deps
pip install -r requirements.txt

# Start server
uvicorn app.main:app --reload --port 8000
```

> API will be available at `http://localhost:8000`  
> Interactive docs: `http://localhost:8000/docs`

### 2 – Frontend

```bash
cd frontend

# Install deps
npm install

# Start dev server
npm run dev
```

> App will be available at `http://localhost:5173`

---

## 🌐 Deployment

### Backend → Render

1. Push your repository to GitHub
2. Create a new **Web Service** on [render.com](https://render.com)
3. Root directory: `backend`
4. Build command: `pip install -r requirements.txt`
5. Start command: `uvicorn app.main:app --host 0.0.0.0 --port $PORT`
5. Add environment variable: `DATABASE_URL=postgresql://user:pass@host/dbname`

### Frontend → Vercel / Netlify

1. Set root directory to `frontend`
2. Build command: `npm run build`
3. Output directory: `dist`
4. Add env variable: `VITE_API_URL=<your-render-backend-url>`

---

## 📡 API Endpoints

### Employees
| Method | Path | Description |
|--------|------|-------------|
| GET    | `/api/employees` | List all (with search/dept filter) |
| POST   | `/api/employees` | Create employee |
| PUT    | `/api/employees/{id}` | Update employee |
| DELETE | `/api/employees/{id}` | Delete employee |
| GET    | `/api/employees/departments` | Distinct departments |

### Attendance
| Method | Path | Description |
|--------|------|-------------|
| GET    | `/api/attendance` | List (filter by date, employee, status) |
| POST   | `/api/attendance` | Mark attendance |
| PUT    | `/api/attendance/{id}` | Update record |
| DELETE | `/api/attendance/{id}` | Delete record |

### Dashboard
| Method | Path | Description |
|--------|------|-------------|
| GET    | `/api/dashboard/stats` | Stats summary |

---

## ⚠️ Assumptions & Limitations

- PostgreSQL 17 is required. Create a database named `hrms` before starting the backend.
- SQLite is **no longer used**; the app requires a live PostgreSQL connection.
- Leave management, payroll, and reporting are out of scope
- Attendance statuses: **Present**, **Absent**, **Late**, **Half Day**
- Future dates cannot be marked for attendance

---

## 📄 License
MIT
