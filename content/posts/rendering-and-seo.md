---
title: "Exploring Rendering Techniques and SEO with Next.js"
date: 2024-01-06T17:20:52+08:00
description: "A deep dive into various rendering methods in Next.js and their impact on SEO."
draft: false
tags: ["Next.js"]
---
## Overview of Rendering Methods in Next.js

Next.js offers several rendering methods, each with unique characteristics and use cases:

1. **Server-Side Rendering (SSR)**: Renders pages on the server at request time.
2. **Static Generation (Prerendering)**: Generates static HTML at build time.
3. **Incremental Static Regeneration (ISR)**: Updates static content after deployment.
4. **Client-Side Rendering**: Renders in the browser using JavaScript.

### Server-Side Rendering in `page.tsx`
By default, `page.tsx` is server-rendered. To leverage hooks, they must be integrated within client-side components.

## Dynamic Rendering in Next.js

Next.js allows each page to be dynamically rendered:

### Force-Dynamic Option
Setting `dynamic` to `force-dynamic` triggers SSR behavior:
- Pages are server-rendered without caching.

```
export const dynamic = 'force-dynamic'

export default function Home() {
  return (
    <main>

    </main>
  )
}
```

## Force-Static Option

Setting `dynamic` to `force-static` activates Static Generation:

Pages are server-rendered and cached indefinitely.

```
export const dynamic = 'force-static'

export default function Home() {
  return (
    <main>

    </main>
  )
}
```

# Revalidate

every page in nextjs will have revalidate option
- if set to force-dynamic will behave like incremental static regeration(ISR)
- ISR will re-generate the page after the amount of second
```
export const revalidate = 60

export default function Home() {
  return (
    <main>

    </main>
  )
}
```


## Redering Summary
| Data fetching | Dynamic Function | Rendering |
| ------------- |--------------------|-----------|
| Cached | No | Static |
| Cached | Yes | Dynamic |
| Not Cached | No | Dynamic |
| Not Cached | Yes | Dynamic |

- or can just use auto and let nextjs decide

# Metadata

## Static data
```tsx
export const metadata = {
  title: "Never Gonna Give You Up",
  description: "Rickrolled"
}

export default function Home() {
  return (
    <main>

    </main>
  )
}
```

## Dynamic Data
```tsx
export async function  generateMetadata({params}: any){
   return{
    title: params
   }
}

export default function Home() {
  return (
    <main>

    </main>
  )
}
```