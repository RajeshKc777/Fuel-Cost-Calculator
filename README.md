# Fuel Claim Distance Tracker — Setup Guide

## 1. Create the shared database (Firebase, free tier)
1. Go to https://console.firebase.google.com → **Add project** (any name, e.g. `digischool-fuel-tracker`). You can skip Google Analytics.
2. In the left sidebar, go to **Build → Firestore Database → Create database**. Choose a location close to you (e.g. `asia-south1`), and start in **test mode** for now.
3. Go to **Build → Firestore Database → Rules**, replace the contents with what's in `firestore.rules` in this folder, and click **Publish**.
4. Go to **Project settings** (gear icon) → scroll to **Your apps** → click the **Web** icon (`</>`) → register an app (any nickname, no need for hosting).
5. Firebase will show you a `firebaseConfig` object with your keys — copy it.

## 2. Connect the site to the database
Open `index.html`, find this near the top of the `<script>` section:

\`\`\`js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
\`\`\`

Replace it with the real `firebaseConfig` object Firebase gave you, then save.

## 3. Put it on GitHub Pages
1. Push/upload `index.html` to your repo (root of the repo).
2. Go to the repo's **Settings → Pages**.
3. Under **Build and deployment**, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
4. GitHub gives you a URL like `https://rajeshkc777.github.io/Fuel-Cost-Calculator/` within a minute or two — share that with colleagues.

## Notes
- **Distance lookup** uses free OpenStreetMap services (Nominatim + OSRM) — no API key needed, but it's an estimate. Always check it against your odometer before saving, especially off the main highways.
- **Everyone who opens the link shares the same trip log** and can see/delete any entry — there's no login. Fine for a small trusted office team, but not if you need per-person access control.
- Firebase's free (Spark) tier gives plenty of reads/writes for a small office tool like this — you won't need to add a billing account unless usage gets very heavy.
- To change the fuel rate later, just edit the "Fuel rate (Rs/km)" field on a trip before saving — it's not hardcoded.
