# 🌱 Code-to-Nature

**Touch grass. Write code. Find balance.**

Code-to-Nature is a gamified platform that bridges coding productivity with outdoor activity. Developers earn **eco-credits** by logging coding sessions — but those credits stay locked until they verify real-world outdoor activity. Once unlocked, credits can be redeemed for rewards, and a leaderboard keeps the community engaged.

---

## 📌 The Problem

Developers spend long hours in front of screens, leading to:

- 🪑 Sedentary habits and low physical activity
- 🧠 Burnout and declining mental well-being
- 🌍 Disconnection from nature and ecological balance

---

## 💡 How It Works

1. **Code** → Log coding sessions (manual entry or via GitHub integration)
2. **Earn Locked Credits** → Every 30 minutes of coding earns 5 locked eco-credits
3. **Go Outside** → Verify outdoor activities (walking, hiking, cycling, gardening, etc.)
4. **Unlock Eco-Credits** → Outdoor activities release your locked credits
5. **Redeem Rewards** → Spend eco-credits on environmental goods, merchandise, or digital perks
6. **Compete** → Climb the leaderboard and challenge friends

---

## ✨ Features

- 👤 User profiles with eco-credit balances, streaks, and friend connections
- 💻 Coding session logging (manual or GitHub-synced)
- 🌿 Outdoor activity tracking and verification
- 🎁 Rewards store with environmental, merchandise, and digital categories
- 🏆 Leaderboard
- 🔐 JWT-based authentication

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Django 5.2, Django REST Framework, SimpleJWT |
| **Database** | SQLite (development) |
| **Frontend** | React 19 + TypeScript, Vite |
| **Styling** | Tailwind CSS, Radix UI, shadcn/ui |
| **State / Data** | TanStack React Query, React Hook Form, Zod |
| **Routing** | React Router v7 |
| **Charts** | Recharts |
| **Deployment** | Vercel (frontend) |

---

## 📁 Project Structure

```
Code_to_nature/
├── backend/                  # Django REST API
│   ├── apps/
│   │   ├── users/            # Authentication, profiles, eco-credits, streaks
│   │   ├── coding/           # Coding session logging & credit calculation
│   │   ├── activities/       # Outdoor activity verification
│   │   ├── rewards/          # Reward catalog & redemptions
│   │   ├── leaderboard/      # Leaderboard logic
│   │   └── common/           # Shared utilities
│   ├── codetonature_project/ # Django project settings & URLs
│   ├── docs/                 # API documentation
│   ├── manage.py
│   └── requirements.txt
└── frontend/                 # React + TypeScript SPA
    └── src/
        ├── pages/            # Dashboard, CodingSessions, OutdoorActivities,
        │                     #   RewardsStore, Leaderboard, Login, Signup
        ├── components/       # Reusable UI components
        ├── contexts/         # AuthContext
        ├── hooks/            # Custom React hooks
        └── data/             # Static / mock data
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.11+
- Node.js 18+

### Backend Setup

```bash
cd backend
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

The API will be available at `http://localhost:8000`.

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

The app will be available at `http://localhost:5173`.

---

## 📡 API Reference

All authenticated endpoints require a **Bearer Token** in the `Authorization` header.

### Authentication

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/users/` | Register a new user |
| `POST` | `/api/token/` | Login — returns access & refresh tokens |
| `POST` | `/api/token/refresh/` | Refresh access token |

#### Register

```http
POST /api/users/
Content-Type: application/json

{
  "email": "johndoe@example.com",
  "password": "test12345"
}
```

#### Login

```http
POST /api/token/
Content-Type: application/json

{
  "email": "johndoe@example.com",
  "password": "test12345"
}
```

### Users & Profiles

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/users/{id}/` | Get user details |
| `GET` | `/api/profiles/{id}/` | Get user profile |
| `PUT` | `/api/profiles/{id}/` | Update all profile fields |
| `PATCH` | `/api/profiles/{id}/` | Update select profile fields |

#### Profile fields

| Field | Type | Description |
|-------|------|-------------|
| `eco_credits` | int | Unlocked eco-credits available to spend |
| `locked_credits` | int | Credits earned from coding, awaiting unlock |
| `github_username` | string | Linked GitHub account |
| `current_streak` | int | Current outdoor activity streak |
| `longest_streak` | int | All-time longest streak |
| `friends` | array | Linked friend profiles |

---

## 💳 Credit System

Credits are awarded for coding sessions at a rate of **5 credits per 30 minutes** of coding. Credits remain **locked** until an outdoor activity is submitted and verified, at which point they become spendable eco-credits.

---

## 🌍 Vision

Code-to-Nature is more than an app — it's a movement toward **digital wellness and ecological balance**.

> *Code more → Go outside → Get rewards.*
