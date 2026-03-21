# Deployment Guide

## Backend → Render

1. Go to https://render.com → New → Web Service
2. Connect GitHub repo: ACCHU04/swift-dash
3. Settings:
   - Root Directory: backend
   - Runtime: Python 3
   - Build Command: pip install -r requirements.txt
   - Start Command: uvicorn main:app --host 0.0.0.0 --port $PORT
4. Add Environment Variables:
   - FIREBASE_SERVICE_ACCOUNT_JSON = (paste entire JSON)
   - GEMINI_API_KEY = your-key
5. Deploy → copy your URL e.g. https://swift-dash-api.onrender.com

## Frontend → Firebase Hosting

1. Install Firebase CLI:
   npm install -g firebase-tools

2. Login:
   firebase login

3. Build:
   cd frontend
   npm run build

4. Deploy:
   cd ..
   firebase deploy

   Your site: https://e-commerce-ce363.web.app

## After Both Are Deployed

Update frontend/src/lib/api.ts NEXT_PUBLIC_API_URL or set it via
Firebase Hosting environment config to point to your Render backend URL.

Better: hardcode the Render URL in frontend/src/lib/api.ts:
  const API_BASE = "https://swift-dash-api.onrender.com";
