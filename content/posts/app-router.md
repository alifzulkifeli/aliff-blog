---
title: "App Routing in Next.js 13: Dynamic Routes Simplified"
date: 2023-12-20T22:22:24+08:00
description: "A deep dive into implementing dynamic routes in Next.js 13, both server-side and client-side, with practical examples."
draft: false
tags: ["Next.js"]
---

Next.js, a popular React framework, is well-known for its efficiency in building server-rendered applications. One of its powerful features is the file system-based routing mechanism. In this blog post, we'll explore how to implement dynamic routing in Next.js 13, covering both server-side and client-side approaches.

## Dynamic Routing in Server-Side

Dynamic routing is a pivotal feature in modern web applications, allowing URLs to be flexibly handled. In Next.js, dynamic routes are defined using file names in square brackets. For instance, a URL pattern like `example.com/[id]` indicates a dynamic segment.

Here’s a simple server-side example to illustrate how dynamic routes can be implemented:

```typescript
interface Props {
  params: {
    id: string;
  };
}

export default async function Page({ params }: Props) {
  const res = await fetch(`https://example.com/api/${params.id}`);

  // Additional logic to handle the response

  return (
    <main>
      {/* Content based on the response */}
    </main>
  );
}
```

In this snippet, the Page component receives params as props, containing the dynamic id. It then uses this id to make a server-side request to an API.

## Dynamic Routing in Client-Side

Implementing dynamic routing on the client side in Next.js 13 is straightforward too. This is particularly useful for handling routing logic within the client-side components.

Consider the following example:
```tsx
'use client';

import { useParams } from 'next/navigation';

export default function Page() {
  const { id } = useParams();

  // You can now use 'id' to fetch data or perform other client-side logic

  return (
    <div>
      {/* Render content based on the 'id' */}
    </div>
  );
}

```

In this client-side approach, we use the useParams hook from next/navigation to access the dynamic route parameters.

## Conclusion
Next.js 13 offers a robust and straightforward way to handle dynamic routes, both server-side and client-side. This flexibility is key to building scalable and efficient web applications. In upcoming posts, I'll dive deeper into more advanced routing techniques and best practices in Next.js. Stay tuned!