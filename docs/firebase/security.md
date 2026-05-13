# Firebase Security

Security basics for Firebase: rules, auth, and least privilege.

## 1. Don’t trust the client
- Always enforce access control in **Firestore/Storage rules** (and/or server).

## 2. Firestore rules pattern

```js
// firestore.rules (conceptual)
match /users/{userId} {
  allow read, write: if request.auth != null && request.auth.uid == userId;
}
```

## 3. Storage rules pattern

```js
// storage.rules (conceptual)
match /users/{userId}/{allPaths=**} {
  allow read, write: if request.auth != null && request.auth.uid == userId;
}
```

## 4. Secrets
- Firebase config keys are not “secrets”, but server keys and service accounts are.
- Never ship service account JSON to the browser.

## Code Examples

### Client-side auth state guard
```javascript
import { onAuthStateChanged } from "firebase/auth";

export function waitForUser(auth) {
  return new Promise(resolve => {
    const unsub = onAuthStateChanged(auth, user => {
      unsub();
      resolve(user);
    });
  });
}
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
