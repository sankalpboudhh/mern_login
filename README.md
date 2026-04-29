# Auth System — MERN Stack

A full-stack authentication system built with the MERN stack. Supports user registration and login with JWT-based authentication, password hashing, and persistent session state managed via Redux.

---

## Features

- User Registration with first name, last name, email, and password
- Secure Login with JWT token generation
- Password hashing using bcrypt (salt rounds: 10)
- Passport.js Local Strategy for login authentication
- Passport.js JWT Strategy for protected route access
- Redux Toolkit for global auth state management
- Persistent session via localStorage
- Material UI components for clean, responsive forms
- React Router v6 for client-side navigation

---

## Tech Stack

**Frontend**
- React.js 18
- Redux Toolkit + React Redux
- Material UI (MUI) v5
- React Router DOM v6
- Axios

**Backend**
- Node.js + Express.js
- MongoDB + Mongoose
- Passport.js (Local + JWT Strategy)
- JSON Web Token (jsonwebtoken)
- bcryptjs
- dotenv

---

## Project Structure

```
mern_login/
├── frontend/
│   └── src/
│       ├── Components/
│       │   ├── Login.js        # Login form with Redux dispatch
│       │   ├── Register.js     # Registration form
│       │   ├── HomePage.js     # Public landing page
│       │   └── Hello.js        # Protected page after login
│       ├── user/
│       │   └── userSlice.js    # Redux slice for auth state
│       ├── store.js            # Redux store setup
│       └── App.js              # Routes configuration
└── backend/
    ├── auth/
    │   └── auth.js             # Passport Local + JWT strategies
    ├── model/
    │   └── model.js            # Mongoose User schema + bcrypt hooks
    ├── routes/
    │   └── routes.js           # /signup and /login API endpoints
    └── app.js                  # Express server entry point
```

---

## Getting Started

### Prerequisites
- Node.js v16+
- MongoDB (local or Atlas)

### 1. Clone the repo
```bash
git clone https://github.com/sankalpboudhh/mern_login.git
cd mern_login
```

### 2. Setup Backend
```bash
cd backend
npm install
```

Create a `.env` file in the `/backend` directory:
```env
DATABASE_URL=mongodb://localhost:27017/mern_auth
PORT=1337
```

Start the backend server:
```bash
npm start
```

### 3. Setup Frontend
```bash
cd frontend
npm install
npm start
```

The app will run at `http://localhost:3000`

---

## API Endpoints

| Method | Endpoint  | Description              |
|--------|-----------|--------------------------|
| POST   | /signup   | Register a new user      |
| POST   | /login    | Authenticate and get JWT |

### Sample Request — `/signup`
```json
{
  "firstname": "Sankalp",
  "lastname": "Boudhh",
  "email": "sankalp@example.com",
  "password": "yourpassword"
}
```

### Sample Request — `/login`
```json
{
  "username": "sankalp@example.com",
  "password": "yourpassword"
}
```

### Sample Response — `/login`
```json
{
  "firstname": "Sankalp",
  "lastname": "Boudhh",
  "token": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }
}
```

---

## How It Works

1. User registers via `/signup` — password is hashed with bcrypt before saving to MongoDB
2. User logs in via `/login` — Passport Local Strategy validates credentials
3. On success, a JWT token is signed and returned to the frontend
4. Frontend dispatches user data to Redux store and persists it in localStorage
5. User is redirected to a protected route (`/Hello`)

---

## Key Concepts Demonstrated

- Separation of concerns — auth logic, routes, and models are in separate files
- Mongoose `pre('save')` hook for automatic password hashing
- Stateless authentication using JWT
- Redux Toolkit slice pattern for clean state management
- Environment variable management with dotenv

---

## Author

**Sankalp Boudhh**
- GitHub: [@sankalpboudhh](https://github.com/sankalpboudhh)
- LinkedIn: [linkedin.com/in/sankalpboudhh](https://linkedin.com/in/sankalpboudhh)
