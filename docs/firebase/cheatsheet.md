# Firebase Cheatsheet

Daily-use Firebase features for web development (Auth, Firestore, Storage, Hosting, Functions).

## Products you’ll use most

- **Authentication**: sign-in, sessions, custom claims
- **Firestore**: real-time NoSQL database
- **Storage**: file uploads (images, PDFs)
- **Hosting**: static + SSR hosting (common for web)
- **Cloud Functions**: server-side logic

## Web SDK (modular) import style

```javascript
import { initializeApp } from "firebase/app";
import { getAuth } from "firebase/auth";
import { getFirestore } from "firebase/firestore";
```

## Firestore document model

- Collections contain documents
- Documents contain fields (and can have subcollections)
- Prefer stable ids for documents (user id, slug, etc.)

## Code Examples

### Initialize app + services
```javascript
import { initializeApp } from "firebase/app";
import { getAuth } from "firebase/auth";
import { getFirestore } from "firebase/firestore";

const firebaseConfig = {
  apiKey: "REDACTED",
  authDomain: "REDACTED",
  projectId: "REDACTED",
};

export const app = initializeApp(firebaseConfig);
export const auth = getAuth(app);
export const db = getFirestore(app);
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
