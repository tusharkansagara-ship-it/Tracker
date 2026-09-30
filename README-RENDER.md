# Course Follow-up Tracker — Render Free Deployment

## Important: repository layout
Upload the **contents of this ZIP** directly into the GitHub repository root. The repository should show `index.html`, `server.js`, `package.json`, `render.yaml`, `schema.sql`, `seed.js`, `manifest.json`, `sw.js`, etc. at the top level.

Do not upload the ZIP file itself as the application.

## Deploy on Render
1. Push the repository to GitHub.
2. In Render, choose **New → Blueprint**.
3. Select the GitHub repository containing `render.yaml`.
4. Render should detect the Blueprint and show a Node web service plus PostgreSQL database.
5. Keep the web service on the **Free** plan.
6. Deploy.
7. Open the generated `https://<service-name>.onrender.com` URL.

The server listens on `0.0.0.0` and uses Render's `PORT` environment variable.

## If you already created the Render service
After replacing the GitHub files with this corrected version, use **Manual Deploy → Deploy latest commit** in Render. You do not need to create a second service.

## Verify before login
Open:
- `https://YOUR-SERVICE.onrender.com/health`

It should return JSON similar to:
`{"ok":true}`

Then open:
- `https://YOUR-SERVICE.onrender.com/`

You should see the Course Follow-up Tracker login screen.

## Demo accounts
Admin: `admin@course.local` / `ChangeMeAdmin123!`
Volunteer: `volunteer@course.local` / `ChangeMeVol123!`
Volunteer B: `vol2@course.local` / `ChangeMeVol234!`

Change demo passwords before real use.

## Mobile
Open the Render URL on Android Chrome and use **Add to Home screen**. The package includes a web app manifest and service worker.

## WhatsApp
The current workflow opens prefilled `wa.me` messages. It does not automate WhatsApp Web clicks. For large-scale/official bulk messaging, integrate the WhatsApp Business Platform with approved templates, consent/opt-out handling, and delivery webhooks.

## Free-tier note
Render free services are suitable for testing/pilot use. Check Render's current free-tier limits and database retention before relying on it for important lead data. Export/backup important data regularly.
