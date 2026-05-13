# Next.js Cheatsheet

Quick reference for Next.js App Router features.

## Routing

| File | Purpose |
| :--- | :--- |
| `page.tsx` | Unique UI for a route |
| `layout.tsx` | Shared UI for a segment and its children |
| `loading.tsx` | Loading UI for a segment |
| `error.tsx` | Error UI for a segment |
| `not-found.tsx`| 404 UI for a segment |

## Data Fetching (Server Components)

```tsx
async function Page() {
  const res = await fetch('https://api.example.com/data', {
    next: { revalidate: 3600 } // Cache for 1 hour
  });
  const data = await res.json();
  
  return <div>{data.title}</div>;
}
```

## Server Actions

```tsx
// actions.ts
'use server'

export async function submitForm(formData: FormData) {
  const name = formData.get('name');
  // Process data
}
```

## Metadata API

```tsx
import type { Metadata } from 'next';

export const metadata: Metadata = {
  title: 'Page Title',
  description: 'Page description',
};
```

## Built-in Components

- `<Link href="/path">`: Pre-fetching and fast navigation.
- `<Image src="..." alt="..." width={500} height={300} />`: Automatic image optimization.
- `<Script src="..." />`: Optimized script loading.


## Code Examples

### Environment variables
```bash
# .env.local
NEXT_PUBLIC_API_BASE=https://api.example.com
```

```javascript
// Use NEXT_PUBLIC_* only in the browser.
console.log(process.env.NEXT_PUBLIC_API_BASE);
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
