TAIF'S CLASS ATTENDANCE TRACKER — GOOGLE CLOUD SYNC EDITION

Included:
- Google sign-in via Firebase Authentication
- Firestore cloud sync, per-user data path
- Firestore IndexedDB offline persistence (browser support required)
- Recent activity list (last 5 displayed, up to 30 retained)
- Existing localStorage attendance migration: when a signed-in user has no cloud record, local records are uploaded; when cloud data exists, cloud values win for matching dates and local-only dates are merged.
- Existing monthly calendar, monthly summary, multi-month report, Telegram support, and developer credit.

IMPORTANT SETUP BEFORE DEPLOYING:
1. In Firebase Console > Authentication > Sign-in method, enable Google.
2. Authentication > Settings > Authorized domains: add your deployed domain (for example, your-project.vercel.app). Keep localhost only for local testing.
3. Create Cloud Firestore database.
4. Firestore > Rules: paste the contents of firestore.rules and Publish.
5. Deploy the whole folder to your hosting provider over HTTPS (Vercel is fine). Do not open index.html as a file:// URL.

Data model:
users/{Firebase Auth UID}/attendance/main
Only the signed-in UID can read/write its own attendance document under the included rules.

Offline:
Firestore IndexedDB persistence queues writes while offline and syncs them when connectivity returns, subject to browser support and the user having signed in online at least once. Do not clear browser site data if there are unsynced offline changes.

SECURITY:
Firebase web apiKey is a public client identifier, not a server secret. Never put service-account private keys in this website. Protect data using Firestore Security Rules as supplied. Firebase billing/quotas may apply depending on usage and project plan.

If sign-in redirect does not return to the app, check Firebase Authentication > Settings > Authorized domains and use the exact deployed domain.
