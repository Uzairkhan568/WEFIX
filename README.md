WEFiX

WEFiX is a full-stack MERN home-services booking platform built as a portfolio flagship project.

Customers can discover services, manage their profile and saved addresses, book appointments, make sandbox payments, receive notifications, and review completed services. Providers can manage their profile, offered services, available bookings, and booking lifecycle. Administrators can manage users, roles, provider services, and bookings.

Live Application

Frontend: https://field-link-project-one.vercel.app

Backend: https://wefix-backend-9qm1.onrender.com

Backend health check: https://wefix-backend-9qm1.onrender.com/health

Tech Stack

Frontend

React

Vite

React Router

Fetch API / Axios where applicable

Responsive dark UI

Backend

Node.js

Express

MongoDB

Mongoose

JWT authentication

HttpOnly cookie authentication

bcryptjs

Zod validation

Helmet

CORS

express-rate-limit

Deployment

Vercel — frontend

Render — backend

MongoDB Atlas — production database

GitHub — source control

Core Features

Customer

Register / login / logout

Persistent authentication

Browse active services

Search and filter services

View service details

Book future appointments

Same-day minimum one-hour lead time

Saved service addresses

Booking history

Booking reference IDs

Sandbox payment

Cancel eligible bookings

Review completed bookings

Notifications

Profile management

Responsive/mobile booking flow

Provider

Provider authentication and role-based access

Provider profile

Manage provider information

Provider service eligibility

View available matching bookings

Accept bookings

Complete bookings

Cancel/release confirmed bookings

Booking notifications

Completed-job count

Admin

Admin authentication

User management

Customer/provider/admin role management

Provider management

Provider service assignment

Booking management

Admin booking visibility

Role synchronization safeguards

Booking Rules

WEFiX enforces appointment timing on both the frontend and backend.

Appointments cannot be scheduled in the past.

Same-day appointments require at least one hour of advance notice.

Future-day appointments are allowed even when they are less than one hour away.

Booking ownership and provider authorization are enforced server-side.

Booking IDs

Each booking has a public booking reference in the format:

WEF-YYYYMMDD-XXXXXXXX

The reference is immutable and unique and is displayed in customer, provider, and admin booking views.

Security

The application includes:

JWT authentication through HttpOnly cookies

Secure cookies in production

SameSite cookie configuration

bcrypt password hashing

Server-side role-based authorization

Ownership checks for bookings, payments, reviews, and notifications

Provider service authorization

Zod input validation

MongoDB/Mongoose validation

Helmet security headers

Exact CORS origin configuration

JSON request-size limiting

General API rate limiting

Login/registration rate limiting

x-powered-by disabled

No JWT stored in localStorage

No dangerouslySetInnerHTML

No eval

No shell execution

No file-upload attack surface

No AI endpoint in the current V1

Project Structure

WEFiX/
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
└── README.md

Local Development

Requirements

Node.js

npm

MongoDB local instance or MongoDB Atlas

Git

1. Clone the repository

git clone <your-github-repository-url>
cd Field-Link-project

2. Install backend dependencies

cd server
npm install

Create server/.env from server/.env.example.

Example development configuration:

NODE_ENV=development
PORT=5000
MONGODB_URI=mongodb://127.0.0.1:27017/wefix
CLIENT_ORIGIN=http://localhost:5173
JWT_SECRET=replace-with-a-long-random-secret
JWT_EXPIRES_IN=7d

3. Seed services

From the server directory:

npm run seed:services

If service image URLs need to be assigned, use the existing service-image migration/setup script in server/scripts/ as appropriate for the current database.

4. Start the backend

Development:

npm run dev

Production-style local start:

npm start

5. Install and run the frontend

Open another terminal:

cd client
npm install
npm run dev

The Vite development server normally runs on:

http://localhost:5173

The Vite development proxy forwards /api requests to the configured backend target.

Environment Variables

Server

NODE_ENV=development
PORT=5000
MONGODB_URI=...
CLIENT_ORIGIN=http://localhost:5173
JWT_SECRET=...
JWT_EXPIRES_IN=7d

Client

The current client uses relative /api/... requests. Local development can optionally use:

VITE_API_PROXY_TARGET=http://localhost:5000

Never commit real secrets.

Production Deployment

Frontend — Vercel

Root directory: client

Framework/preset: Vite

Build command: npm run build

Output directory: dist

The project includes a Vercel rewrite configuration for:

/api/* → production Render backend

SPA routes → /index.html

Backend — Render

Root directory: server

Build command: npm install

Start command: node server.js

Production environment variables must be configured in Render rather than committed to Git.

Database — MongoDB Atlas

Production uses the WEFiX production Atlas cluster.

Atlas network access must allow the production backend to connect while avoiding unnecessary public access.

Testing / QA Status

WEFiX V1 completed the planned development and QA stages.

Completed

Foundation

Authentication and RBAC

Customer functionality

Backend/API/database functionality

Provider functionality

Admin functionality

Booking and provider matching

Payments

Reviews

Notifications

Profiles

Search/filtering

UI/UX audit

Responsive/mobile QA

End-to-end flow testing

Cross-role authorization / IDOR testing

Error and edge-case testing

Production deployment

Live customer flow

Live provider flow

Live admin flow

Production authentication

Deep-link refresh

Sandbox payment

Mobile booking UX

Important Production Notes

Sandbox payments

Payments in V1 are intentionally sandbox/demo payments. They are not connected to a real payment processor and must not be represented as real financial processing.

Secrets

Never commit:

.env

production MongoDB credentials

JWT secrets

API keys

passwords

Use .env.example files for documentation only.

Production secret rotation

If any production credential or database password has ever been exposed outside the intended secret manager, rotate it before treating the deployment as fully secured.

Known V1 Scope Limitations

The current V1 does not include:

Real payment processing

Real-time chat

AI-powered features

File-upload workflows

Advanced provider location/routing

Production-grade observability/alerting infrastructure

Automated CI/CD test pipelines

These are potential future improvements rather than blockers for the current portfolio V1.

Future Improvements

Potential V2 work:

Real payment provider integration

Email/SMS notifications

Provider location and map matching

Real-time messaging

Calendar integrations

Automated tests and CI

Structured logging and monitoring

Provider availability calendars

Advanced search and sorting

Customer/provider analytics

AI-assisted service discovery or support, with dedicated AI security controls

Portfolio Positioning

WEFiX demonstrates practical full-stack engineering across:

React frontend architecture

REST API design

Express middleware

MongoDB/Mongoose data modeling

Authentication and authorization

Role-based access control

Ownership/IDOR protection

Booking state management

Scheduling validation

Payment-state handling

Notifications

Reviews

Responsive UI

Production deployment

Environment/secrets management

Security hardening

End-to-end QA

License

This project is a portfolio project. Add a formal license here if you decide to distribute the source under one.
