# Firebase Deployment

Common deployment targets: Hosting, Functions, Firestore rules/indexes.

## Hosting deploy

```bash
firebase deploy --only hosting
```

## Functions deploy

```bash
firebase deploy --only functions
```

## Rules deploy

```bash
firebase deploy --only firestore:rules,storage
```



> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
