# WEFiX

> A full-stack home-services booking platform built with the MERN stack.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-WEFiX-blue?style=for-the-badge)](https://field-link-project-one.vercel.app)
[![Backend](https://img.shields.io/badge/Backend-Render-46E3B7?style=for-the-badge)](https://wefix-backend-9qm1.onrender.com)
[![Database](https://img.shields.io/badge/Database-MongoDB%20Atlas-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/atlas)

## 🌐 Live Demo

**Frontend:** https://field-link-project-one.vercel.app

**Backend:** https://wefix-backend-9qm1.onrender.com

**Health Check:** https://wefix-backend-9qm1.onrender.com/health

**Source Code:** Use the repository URL shown in the GitHub repository.

---

## 📌 About The Project

WEFiX is a production-deployed full-stack home-services booking platform.

The application connects customers with service providers through a complete booking workflow. Customers can discover services, schedule appointments, manage addresses, make sandbox payments, receive notifications, and review completed services.

The platform also includes dedicated provider and administrator experiences with role-based access control.

This project was built as a **portfolio flagship project** to demonstrate practical full-stack development, security, database design, deployment, and real-world application architecture.

---

## ✨ Features

### 👤 Customer

- Create an account and log in securely
- Persistent authentication
- Browse available services
- Search and filter services
- View detailed service information
- Book future appointments
- Enforce minimum one-hour notice for same-day appointments
- Manage saved service addresses
- View booking history
- Receive a unique booking ID
- Make sandbox payments
- Cancel eligible bookings
- Review completed services
- Receive notifications
- Manage profile information
- Responsive mobile booking experience

### 🧑‍🔧 Provider

- Provider role authentication
- Provider profile management
- Manage offered services
- View matching available bookings
- Accept bookings
- Complete bookings
- Cancel/release confirmed bookings
- Receive booking notifications
- Track completed jobs

### 👑 Administrator

- Secure admin access
- View and manage users
- Change user roles
- Manage provider profiles
- Assign provider services
- View and manage bookings
- Administrative visibility across the platform

---

## 🛠️ Tech Stack

| Area | Technology |
|---|---|
| Frontend | React |
| Build Tool | Vite |
| Routing | React Router |
| Backend | Node.js + Express |
| Database | MongoDB |
| ODM | Mongoose |
| Authentication | JWT + HttpOnly Cookies |
| Password Hashing | bcryptjs |
| Validation | Zod + Mongoose |
| Security | Helmet, CORS, Rate Limiting |
| Frontend Hosting | Vercel |
| Backend Hosting | Render |
| Database Hosting | MongoDB Atlas |
| Source Control | GitHub |

---

## 🏗️ Architecture

```text
┌─────────────────────┐
│     User Browser    │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Vercel               │
│ React + Vite Client  │
└──────────┬──────────┘
           │ /api
           ▼
┌─────────────────────┐
│ Render               │
│ Node + Express API  │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ MongoDB Atlas        │
│ Production Database  │
└─────────────────────┘
```

---

## 🔐 Authentication & Security

Security was treated as part of the application architecture rather than an afterthought.

WEFiX includes:

- JWT authentication using HttpOnly cookies
- Secure cookies in production
- SameSite cookie configuration
- bcrypt password hashing
- Server-side role-based authorization
- Customer/provider ownership checks
- IDOR protection
- Payment ownership validation
- Review ownership validation
- Notification ownership validation
- Provider service authorization
- Zod request validation
- Mongoose validation
- Helmet security headers
- Restricted CORS configuration
- JSON request-size limiting
- API rate limiting
- Login and registration rate limiting
- Disabled `x-powered-by`
- JWT tokens are not stored in localStorage

---

## 📅 Booking System

WEFiX uses a complete booking lifecycle rather than a simple form submission.

Customers can create future appointments and providers can accept and complete them.

### Booking rules

- Past appointments are rejected.
- Same-day appointments require at least **1 hour of advance notice**.
- Future-day appointments are allowed even when they are less than one hour away.
- Appointment validation is enforced on both the frontend and backend.
- Booking ownership is verified server-side.

### Booking IDs

Every booking receives a unique public reference such as:

```text
WEF-20260910-K7M4Q2XA
```

Booking references are immutable and unique.

---

## 💳 Payments

WEFiX includes a **sandbox payment flow** for demonstrating payment-state handling.

> **Important:** Payments are simulated and are not connected to a real payment processor.

The payment system demonstrates:

- Customer ownership validation
- Successful payment state
- Failed payment state
- Prevention of payment on cancelled bookings
- Prevention of duplicate payment

---

## ⭐ Reviews & Notifications

### Reviews

Customers can review completed bookings.

The backend verifies:

- The booking belongs to the customer
- The booking is completed
- A provider exists
- A review has not already been submitted

### Notifications

The application provides notifications for important booking events between customers and providers.

---

## 📱 Responsive UI

WEFiX was tested across desktop and mobile layouts.

The mobile booking experience was specifically refined so the flow is:

```text
View Service
      ↓
Service Details
      ↓
Book Now
      ↓
Booking Form
```

The interface automatically scrolls to the relevant section so customers do not have to search for the next action.

---

## 📂 Project Structure

```text
Field-Link-project/
│
├── client/
│   ├── public/
│   │   └── images/
│   │       └── services/
│   ├── src/
│   │   ├── auth/
│   │   ├── components/
│   │   ├── data/
│   │   └── ...
│   ├── vercel.json
│   ├── vite.config.js
│   └── package.json
│
├── server/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── scripts/
│   ├── services/
│   ├── utils/
│   ├── server.js
│   └── package.json
│
├── README.md
└── .gitignore
```

---

## 🚀 Running The Project Locally

### Prerequisites

You will need:

- Node.js
- npm
- MongoDB local instance or MongoDB Atlas
- Git

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd Field-Link-project
```

### 2. Install backend dependencies

```bash
cd server
npm install
```

### 3. Configure backend environment variables

Create:

```text
server/.env
```

Use the example environment configuration:

```env
NODE_ENV=development
PORT=5000
MONGODB_URI=mongodb://127.0.0.1:27017/wefix
CLIENT_ORIGIN=http://localhost:5173
JWT_SECRET=your-development-secret
JWT_EXPIRES_IN=7d
```

**Never commit `.env` files or real credentials.**

### 4. Start the backend

```bash
npm run dev
```

### 5. Install frontend dependencies

Open another terminal:

```bash
cd client
npm install
```

### 6. Start the frontend

```bash
npm run dev
```

The frontend normally runs at:

```text
http://localhost:5173
```

---

## 🌍 Deployment

WEFiX is deployed using three services.

### Frontend — Vercel

The React/Vite frontend is deployed on Vercel.

**Live:** https://field-link-project-one.vercel.app

### Backend — Render

The Express backend is deployed on Render.

**Live:** https://wefix-backend-9qm1.onrender.com

### Database — MongoDB Atlas

Production data is stored in MongoDB Atlas.

---

## 🧪 QA & Testing

WEFiX went through a structured QA process covering:

- End-to-end customer flows
- End-to-end provider flows
- End-to-end admin flows
- Authentication
- Role-based access control
- Authorization
- IDOR/ownership testing
- Error handling
- Edge cases
- Responsive/mobile UI
- Production deployment
- Production authentication persistence
- Deep-link refresh
- Sandbox payment
- Live booking workflows

### Final QA Status

| Stage | Status |
|---|---|
| Foundation | ✅ PASS |
| Authentication & RBAC | ✅ PASS |
| Customer Features | ✅ PASS |
| Backend / API / Database | ✅ PASS |
| Provider & Admin Features | ✅ PASS |
| Booking / Payments / Reviews / Notifications | ✅ PASS |
| UI / UX | ✅ PASS |
| Responsive / Mobile | ✅ PASS |
| Production Verification | ✅ PASS |

**Overall V1 status: 🟢 Production-ready**

---

## 🎯 What This Project Demonstrates

WEFiX demonstrates practical experience with:

- Full-stack MERN development
- React component architecture
- REST API development
- Express middleware
- MongoDB data modeling
- Mongoose relationships and queries
- JWT authentication
- HttpOnly cookie authentication
- Role-based access control
- Server-side authorization
- IDOR prevention
- Booking and state management
- Scheduling validation
- Payment-state handling
- Notifications
- Reviews
- Responsive UI development
- Production deployment
- Environment and secrets management
- Security hardening
- End-to-end testing

---

## 🔮 Possible V2 Improvements

The current V1 is intentionally focused. Possible future improvements include:

- Real payment gateway integration
- Email and SMS notifications
- Provider location/map matching
- Real-time customer/provider chat
- Calendar integrations
- Automated unit/integration tests
- CI/CD testing
- Advanced monitoring and observability
- Advanced analytics
- AI-powered service discovery or support

---

## 👨‍💻 Portfolio Note

WEFiX was built as a portfolio project to demonstrate the ability to design, develop, secure, test, and deploy a real-world multi-role web application.

The focus was not only on making the UI work, but also on:

**Architecture → Security → Authorization → Data integrity → UX → Testing → Production deployment**

---

## 📄 License

This project is currently presented as a portfolio project.

Add a formal open-source license if you decide to distribute the source code under one.
