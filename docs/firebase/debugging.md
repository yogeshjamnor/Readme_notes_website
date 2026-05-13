# Firebase Debugging

Practical debugging tips for Firebase apps.

## Use emulators first (recommended)

```bash
firebase emulators:start
```

## Common issues checklist

- Wrong project selected (`firebase use`)
- Missing env config in the frontend
- Firestore/Storage rules blocking requests
- CORS when calling Functions/HTTP endpoints

## Logging (Functions)

- Use structured logs and avoid logging secrets.



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
