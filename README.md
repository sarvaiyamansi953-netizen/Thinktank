# EventEase

EventEase is a futuristic college event registration and smart check-in system built with FastAPI and a Neon Campus design system.

## Features
- Registration flow for event participants
- Dynamic QR generation and validation using JWT + HMAC-style signing via PyJWT
- Live dashboard and security alerts
- Offline-first scanner interactions via browser cache patterns
- Demo-friendly event discovery and leaderboard pages

## Local setup

1. cd eventease/backend
2. python -m pip install -r requirements.txt
3. Copy .env.example to .env and set GOOGLE_CLIENT_ID / GOOGLE_CLIENT_SECRET / GOOGLE_REDIRECT_URI
4. python -m uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
5. Open http://localhost:8000/

## Google OAuth setup

1. In Google Cloud Console, create an OAuth 2.0 Client ID.
2. Add the redirect URI: http://127.0.0.1:8000/api/auth/google/callback
3. Fill in the values in backend/.env.
4. Sign in with the Google button on the login page.

## Demo flow
1. Register participant
2. Generate ticket and QR token
3. Open scanner page and verify entry
4. Scan same QR again to trigger duplicate blocked state
5. Dashboard and security center update in real time

## Notes
- PostgreSQL is supported via DATABASE_URL and environment configuration.
- SQLite is used by default for quick local demos if PostgreSQL is not available.
