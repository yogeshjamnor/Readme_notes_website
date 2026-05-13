# Next.js Project Setup

Setting up a project with App Router and modern architecture.

## Recommended Folder Structure (App Router)

```text
src/
├── app/              # Routing and Pages
│   ├── layout.tsx    # Root layout
│   ├── page.tsx      # Home page
│   ├── globals.css   # Global styles
│   └── (auth)/       # Route groups (no impact on URL)
├── components/       # UI Components
│   ├── ui/           # Shared UI (Shadcn)
│   └── forms/        # Feature-specific components
├── lib/              # Utility libraries (Prisma, Stripe)
├── hooks/            # Custom React hooks
├── services/         # Server Actions / Data fetching
└── types/            # TS Interfaces
```

## Environment Variables

```env
# .env.local
NEXT_PUBLIC_API_URL=https://api.example.com
DATABASE_URL=postgresql://...
STRIPE_SECRET_KEY=sk_test_...
```

> [!IMPORTANT]
> Variables prefixed with `NEXT_PUBLIC_` are exposed to the browser. Others are only accessible on the server.

## Server Actions Setup

Next.js 15+ has Server Actions enabled by default.

```typescript
// src/services/actions.ts
'use server'

export async function createItem(formData: FormData) {
  // Database logic here
}
```

## Best Practices

1.  **Server Components**: Use them by default for data fetching.
2.  **Client Components**: Use `'use client'` only when necessary (state, effects, events).
3.  **Data Fetching**: Use native `fetch` with Next.js caching.
4.  **SEO**: Use the `Metadata` API in `layout.tsx` or `page.tsx`.


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
