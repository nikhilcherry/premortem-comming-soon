# Premortem Coming Soon - Secure Setup

This project is configured for a secure "Coming Soon" deployment with Firebase.

## 🔒 Security Measures Implemented

1.  **Strict Firestore Rules**: Located in `firestore.rules`.
    -   `allow create: if true;` -> Anyone can submit an email.
    -   `allow read, update, delete: if false;` -> NO ONE except you (via the Firebase Console) can see or tamper with the email list.
2.  **Honeypot Protection**: Added a hidden field in `interested.html` to auto-reject bot submissions.
3.  **Project Targeting**: Configured `.firebaserc` to target your project `storage-b526f`.

## 🚀 How to Apply Security Settings

If you have the [Firebase CLI](https://firebase.google.com/docs/cli) installed (run `npm install -g firebase-tools` if not), follow these steps to secure your project:

1.  **Login**:
    ```bash
    firebase login
    ```
2.  **Deploy Rules Only**:
    ```bash
    firebase deploy --only firestore:rules
    ```

## 🌐 How to Hosting (GitHub Pages / Vercel)

If you are hosting on GitHub Pages:
1.  Go to your repo **Settings > Pages**.
2.  Select **Deploy from branch** (main).
3.  Add your domain to **Firestore > Project Settings > Authorized Domains** in the Firebase Console.

---
**Note**: The API key in `index.html` is public, but as long as the `firestore.rules` are deployed, your data is safe.
