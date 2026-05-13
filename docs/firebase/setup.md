# Firebase Setup (Web)

Minimal setup for a web app.

## 1. Create project

- Create a Firebase project in the console
- Add a Web App to get config keys (safe to be public; do not confuse with secrets)

## 2. Initialize SDK

```javascript
import { initializeApp } from "firebase/app";

export const app = initializeApp({
  apiKey: "REDACTED",
  authDomain: "REDACTED",
  projectId: "REDACTED",
});
```

## 3. Enable products

- Auth provider(s) (Email/Google/etc.)
- Firestore rules
- Storage rules



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
