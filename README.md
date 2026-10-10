# EventEase Campus 🎓⚡

> **Campus Event Discovery, Ticketing, Turnstile QR Check-In, and Ingress Management SaaS**

EventEase Campus is a full-stack, enterprise-grade event management platform tailored for university campuses, student organizations, and academic institutions. It features zero-friction digital passes, cryptographic HMAC turnstile QR check-in, real-time automated waitlist promotions, multi-campus role-based administration, and organizer analytics.

---

## 🚀 Key Features

### 🎫 Student Digital Pass Vault
- **Zero-Friction Discovery**: Filter events by campus, category, timeframe, pricing, and keywords.
- **Dynamic Digital Passes**: Anti-screenshot animated watermarks, HMAC-SHA256 tamper-proof QR tokens, and offline backup codes.
- **Instant Checkout**: One-click free ticket issuance and mock payment integration with immediate pass delivery.
- **Automated Waitlist Promotion**: First-in, first-out waitlist queue with automatic ticket allocation upon cancellations.
- **Bookmarks & Notifications**: Save upcoming events, receive ingress notifications, and view event status updates.

### 🛡️ Turnstile Ingress Gatekeeper (Organizers & Staff)
- **High-Throughput Camera Scanner**: In-browser QR code scanner using HTML5-QRCode with multi-frame detection.
- **Instant HMAC Signature Verification**: Offline-compatible cryptographic validation preventing pass duplication or ticket reuse.
- **Audio Feedback**: Web Audio API tone synthesis for valid entry (`D5-A5` chord), duplicate alert, and invalid warnings.
- **Manual Fallback Entry**: Rapid keyboard code entry for damaged displays or printed passes.
- **Live Ingress Activity Feed**: Real-time log of scanned passes, timestamps, and operator audit entries.

### 📊 Organizer Management Suite
- **Event Studio**: Rich event builder supporting multi-tier tickets, capacities, check-in windows, and cover uploads.
- **Attendee Roster & Management**: Live attendee list with turnstile check-in flags, registration revoking, and one-click CSV export.
- **Lifecycle Controls**: Publish, unpublish, duplicate, and archive events.
- **Real-Time Analytics**: Conversion rates, attendance throughput percentage, revenue, and no-show metrics.

### 👑 Platform Administration Console
- **Multi-Campus Management**: Support for multiple university campuses and departments.
- **Organizer Verification Queue**: Review and approve student organization organizer applications.
- **Event Moderation**: Force-publish, unlist, or flag events violating campus safety policies.
- **Security Audit Logs**: Comprehensive trail of privileged actions, data exports, and pass revocations.
- **Category Taxonomies**: Dynamic categories, tags, and icon mappings.

---

## 🔑 Demo Accounts & Credentials

The pre-seeded database contains ready-to-test accounts across all roles:

| Role | Email | Password | Access Level |
| :--- | :--- | :--- | :--- |
| **Platform Admin** | `admin@eventease.local` | `AdminPass123!` | Full superadmin console, moderation, logs, users |
| **Event Organizer** | `organizer@eventease.local` | `OrganizerPass123!` | Create events, turnstile scanner, attendee exports |
| **Student Attendee** | `student@eventease.local` | `StudentPass123!` | Pass vault, bookings, waitlist, bookmarks |

---

## 🛠️ Architecture & Tech Stack

### Frontend
- **Framework**: React 18 + TypeScript + Vite
- **Styling**: Tailwind CSS + Lucide Icons
- **Routing & State**: React Router v6 + React Context API
- **QR Engine**: `qrcode.react` (generation) & `html5-qrcode` (camera ingress scanner)
- **Data Visualizations**: Recharts
- **Audio Engine**: Web Audio API Synthesizer

### Backend
- **Framework**: FastAPI (Python 3.12+)
- **ORM & Database**: SQLAlchemy with SQLite (production-ready for PostgreSQL/MySQL)
- **Security & Cryptography**: PyJWT, Passlib (Bcrypt), HMAC-SHA256 dynamic token generation
- **Data Validation**: Pydantic v2
- **Testing**: Pytest test suite with TestClient

---

## 📦 Quick Start & Local Setup

### 1. Backend Setup
```bash
cd backend
python -m venv venv
# Windows:
.\venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

pip install -r requirements.txt

# Initialize and seed database
python -m app.seed

# Run FastAPI server
uvicorn app.main:app --reload --port 8000
```
Backend API will be available at: `http://localhost:8000`  
Swagger API Docs: `http://localhost:8000/docs`

### 2. Frontend Setup
```bash
cd frontend
npm install
npm run dev
```
Frontend Web App will be available at: `http://localhost:5173`

---

## 🧪 Running Tests & Build Verification

### Backend Tests
```bash
python -m pytest -o pythonpath=backend backend/tests
```

### Frontend Production Build
```bash
cd frontend
npm run build
```

---

## 📁 Project Structure

```
EventEase3/
├── backend/
│   ├── app/
│   │   ├── api/             # API v1 routes & dependencies
│   │   ├── core/            # Config, database, security & HMAC utilities
│   │   ├── models/          # SQLAlchemy database models
│   │   ├── schemas/         # Pydantic request/response schemas
│   │   ├── services/        # Business logic (check-in, registration, waitlist, analytics)
│   │   ├── main.py          # FastAPI application entrypoint
│   │   └── seed.py          # Database seeder with realistic campus data
│   ├── tests/               # Pytest test suite
│   └── requirements.txt
├── frontend/
│   ├── src/
│   │   ├── api/             # Axios client & typed API endpoints
│   │   ├── components/      # UI components, layout, scanner, tickets, cards
│   │   ├── context/         # AuthContext with persistent JWT state
│   │   ├── pages/           # Public, Student, Organizer, Admin & Legal pages
│   │   ├── types/           # TypeScript interfaces & enums
│   │   ├── App.tsx          # Router with role-based protected guards
│   │   └── main.tsx         # React application bootstrap
│   ├── package.json
│   └── vite.config.ts
├── docs/                    # Architectural & API specifications
└── scripts/                 # Development runner scripts
```

---

## 📄 License
Released under the MIT License for university and educational event management.
