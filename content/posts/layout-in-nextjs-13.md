---
title: "Layout Techniques in Next.js 13"
date: 2023-11-12T20:50:54+08:00
description: "Next.js 13 layouts and discover how to effectively use root layouts to structure your applications."
draft: false
tags: ["Next.js"]
---

# Root layout

Next.js 13 introduces enhanced layout capabilities, offering developers more control and flexibility. This guide delves into the concept of root layouts and how they can transform the structure of your Next.js applications.

![root layout](/images/0003.png)


**Shared Layouts Across Pages**: The beauty of root layouts lies in their reusability. By defining a layout at the root level, all child components inherit this structure, ensuring a consistent look and feel across your application.

**Persistent Layouts Without Re-rendering**: A common challenge with layouts is managing re-renders. In Next.js 13, root layouts persist across navigations, reducing unnecessary re-renders. However, if you need a layout to re-render under specific circumstances, you can leverage `template.tsx` to control this behavior.

# Example 

- Root Layout

```tsx
// app/layout.tsx
export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="en">
      <body className={inter.className}>
        <h1>Layout1</h1>
        {children}</body>
    </html>
  )
}
```

- child Layout
```tsx
// app/notes/layout.tsx
export default function Layout({ children }: { children: React.ReactNode }) {
    return (
        <>
            <h1>Layout 2</h1>
            <main>{children}</main>

        </>
    )
}
```

- rendered on page
![nested layout](/images/0004.png)
