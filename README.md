# Workspace & Project Management Platform

A comprehensive, full-stack collaborative platform designed for managing workspaces, projects, tasks, and team members. Built with a robust **Node.js/Express/TypeScript** backend and a modern **React 19/Vite/Tailwind CSS** frontend.

---

## 🌟 Key Features

### 🔐 Authentication & Authorization
- **Multi-Strategy Auth**: Supports both traditional Local Authentication (Email/Password with bcrypt hashing) and Google OAuth 2.0 via Passport.js.
- **Session Management**: Secure session handling using HTTP-only cookies (`cookie-session`).
- **Role-Based Access Control (RBAC)**: Fine-grained permissions for workspace owners, admins, and members.

### 🏢 Workspace Management
- **Workspaces**: Create isolated workspaces for different organizations, teams, or departments.
- **Member Invitations**: Invite team members to workspaces with specific roles and permission levels.

### 📁 Project & Task Tracking
- **Projects**: Organize initiatives within workspaces.
- **Tasks**: Create, assign, and track tasks within projects.
- **Status & Workflow**: Real-time tracking of task progress and member assignments.

---

## 🛠️ Technology Stack

### Backend (`/backend`)
- **Runtime & Framework**: Node.js, Express 5.x, TypeScript
- **Database & ODM**: MongoDB, Mongoose 9.x
- **Authentication**: Passport.js (Local & Google OAuth 2.0), JSON Web Tokens (JWT)
- **Security & Middleware**: CORS, Cookie-Session, Dotenv, Bcryptjs

### Frontend (`/client`)
- **Framework**: React 19, TypeScript, Vite
- **Styling**: Tailwind CSS 4.x
- **Linting & Code Quality**: ESLint 9, TypeScript ESLint

---

## 📂 Project Structure

```
group-projects/
│
├── backend/                  # Express & TypeScript API Server
│   ├── src/
│   │   ├── config/           # App, Database, HTTP, and Passport configurations
│   │   ├── controllers/      # Route controllers (Auth, Workspace, Project, Task, etc.)
│   │   ├── enums/            # Error codes and system enums
│   │   ├── middlewares/      # Authentication, error handling, and async handlers
│   │   ├── models/           # Mongoose schemas (User, Workspace, Project, Task, Member, etc.)
│   │   ├── routes/           # Express route definitions
│   │   ├── services/         # Business logic layer
│   │   ├── utils/            # Custom error classes and helper utilities
│   │   └── validation/       # Request validation schemas
│   ├── .env                  # Backend environment variables
│   └── package.json          # Backend dependencies and scripts
│
└── client/                   # React 19 & Vite Frontend Client
    ├── src/
    │   ├── assets/           # Static assets and images
    │   ├── components/       # Reusable UI components
    │   ├── context/          # React context providers (Auth, Theme, etc.)
    │   ├── hooks/            # Custom React hooks
    │   ├── layout/           # Page layouts (Sidebar, Navbar, Dashboard, etc.)
    │   ├── lib/              # Utility libraries and API client configurations
    │   ├── page/             # Main application pages (Auth, Workspace, Invite, Errors)
    │   ├── routes/           # Application routing configuration
    │   └── types/            # TypeScript type definitions
    ├── .env.example          # Example frontend environment variables
    └── package.json          # Frontend dependencies and scripts
```

---

## 🚀 Getting Started

### 1. Prerequisites
Ensure you have the following installed:
- **Node.js** (v20+ recommended)
- **MongoDB** (Local instance or MongoDB Atlas connection string)
- **Git**

---

### 2. Installation

Clone the repository and install dependencies for both the backend and frontend.

```powershell
# Install Backend Dependencies
cd backend
npm install

# Install Frontend Dependencies
cd ../client
npm install
```

---

### 3. Environment Configuration

#### Backend Configuration (`backend/.env`)
Ensure your `backend/.env` file is properly configured with the following parameters:
```env
PORT=5000
NODE_ENV=development
MONGO_URI=mongodb://localhost:27017/your-database-name
SESSION_SECRET=your_super_secret_session_key
FRONTEND_ORIGIN=http://localhost:5173

# Google OAuth (Optional)
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_CALLBACK_URL=http://localhost:5000/api/auth/google/callback
```

#### Frontend Configuration (`client/.env`)
Copy `client/.env.example` to `client/.env` and verify your API base URL:
```env
VITE_API_BASE_URL=http://localhost:5000/api
```

---

### 4. Running the Application Locally

You will need two separate terminal windows/tabs to run the client and server concurrently.

#### Start the Backend Server
Open a terminal from the project root:
```powershell
cd backend
npm run dev
```
*The server will start on `http://localhost:5000`.*

#### Start the Frontend Client
Open a second terminal from the project root:
```powershell
cd client
npm run dev
```
*The client will start on `http://localhost:5173`.*

---

## 📡 API Endpoints Overview

The backend exposes a structured RESTful API under the configured base path (e.g., `/api`):

| Endpoint Prefix | Authentication Required | Description |
| :--- | :---: | :--- |
| `/api/auth` | No | User registration, login, logout, and Google OAuth flows. |
| `/api/user` | Yes | Get current authenticated user profile and account details. |
| `/api/workspace` | Yes | Create, update, delete, and list user workspaces. |
| `/api/member` | Yes | Manage workspace members, invitations, and role assignments. |
| `/api/project` | Yes | Create and manage projects within a specific workspace. |
| `/api/task` | Yes | Create, assign, update status, and track project tasks. |

---

## 🛡️ License
This project is licensed under the ISC License.
