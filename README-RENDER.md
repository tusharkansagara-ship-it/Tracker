# Course Follow-up Tracker — Free Render Deployment

This package is prepared for a mobile-first volunteer tracker using a free Render Web Service and free Render Postgres database.

## Important free-tier warning
Render's free web service can sleep after inactivity. Render's free Postgres database currently has a 1 GB limit and expires 30 days after creation. Use this setup for testing/piloting, not as the only copy of important lead data. See Render's current free-tier documentation before using it for real operational data.

## Deploy from GitHub

1. Create a free GitHub account if needed.
2. Create a new repository, for example `course-followup-tracker`.
3. Upload the contents of this folder to the repository (keep `render.yaml` in the repository root).
4. Open Render and sign in.
5. Choose **New → Blueprint** and connect the GitHub repository.
6. Render will read `render.yaml` and create:
   - `course-followup-tracker` — Free Node web service
   - `course-tracker-db` — Free PostgreSQL database
7. Confirm the free plans and deploy.
8. Render will provide an `https://...onrender.com` URL.

## First login

The seed step creates these demo accounts:

- Admin: `admin@course.local` / `ChangeMeAdmin123!`
- Volunteer: `volunteer@course.local` / `ChangeMeVol123!`
- Volunteer B: `vol2@course.local` / `ChangeMeVol234!`

Immediately create real volunteer accounts and change/remove the demo accounts before sharing the URL broadly.

## Mobile use

Open the Render URL on Android Chrome or iPhone Safari. The site includes a web app manifest and service worker, so it can be added to the phone's Home Screen.

## Current WhatsApp behavior

The tracker records outbound messages and opens WhatsApp `wa.me` links with prefilled text. It does **not** automate WhatsApp Web clicks. For reliable bulk messaging at scale, connect an approved WhatsApp Business Platform provider and use consent/opt-out and approved templates.

## Render settings

The Blueprint uses:
- Node runtime
- Free compute plan
- Singapore region
- `/health` health check
- generated JWT secret
- secure HTTP-only session cookie
- PostgreSQL connection supplied automatically by the Render database

The app binds to `0.0.0.0` and uses Render's `PORT` environment variable.

## If you want long-term free-ish data storage

Keep the web service on Render Free, but move PostgreSQL to a provider whose current free tier suits your needs. Set `DATABASE_URL` in Render to that provider's connection string. Do not assume a free database tier is permanent; verify its current retention, quotas, backups, and inactivity rules.
