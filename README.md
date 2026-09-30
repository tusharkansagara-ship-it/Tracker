# Course Follow-up Tracker — Multi-user production starter

This version replaces browser localStorage with PostgreSQL and server-side authentication.

## Includes
- Shared PostgreSQL database
- Secure bcrypt password hashing
- HTTP-only JWT session cookie
- Admin/volunteer roles and server-side ownership checks
- Shared lead CRUD and assignments
- Automatic priority scoring
- Follow-up history
- WhatsApp message queue records
- Responsive web UI for phones/laptops

## Fastest local run
Install Docker, then:

    docker compose up --build

Open http://localhost:3000

Demo accounts (change before production):
- Admin: admin@course.local / ChangeMeAdmin123!
- Volunteer: volunteer@course.local / ChangeMeVol123!
- Volunteer B: vol2@course.local / ChangeMeVol234!

## Non-Docker
Create PostgreSQL database `course_tracker`, copy `.env.example` to `.env`, set a strong JWT_SECRET, then run:

    npm install
    npm run seed
    npm start

## Production hardening checklist
Use HTTPS, COOKIE_SECURE=true, a strong secret in deployment secrets, managed PostgreSQL backups/PITR, login/API rate limiting, password reset/invitation flow, audit logs, input validation, monitoring, and restricted CORS if a separate frontend is introduced.

## WhatsApp
The backend records outbound messages and the UI can open prefilled WhatsApp chats. For true bulk messaging, connect an approved WhatsApp Business Platform/API provider, with approved templates, consent/opt-out handling, delivery webhooks and provider message IDs. Do not automate WhatsApp Web browser clicks or use unofficial bulk-sending methods.
