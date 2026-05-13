# Firebase CRUD (Firestore)

Common Firestore operations (Web SDK modular).

## 1. CREATE

```javascript
import { doc, setDoc } from "firebase/firestore";

await setDoc(doc(db, "users", userId), {
  name: "Asha",
  createdAt: Date.now(),
});
```

## 2. READ

```javascript
import { doc, getDoc } from "firebase/firestore";

const snap = await getDoc(doc(db, "users", userId));
const data = snap.exists() ? snap.data() : null;
```

## 3. UPDATE (merge)

```javascript
import { doc, setDoc } from "firebase/firestore";

await setDoc(doc(db, "users", userId), { name: "New" }, { merge: true });
```

## 4. DELETE

```javascript
import { doc, deleteDoc } from "firebase/firestore";

await deleteDoc(doc(db, "users", userId));
```



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
