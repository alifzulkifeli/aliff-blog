---
title: "What's New in Next 13"
date: 2023-11-08T21:27:53+08:00
description: ""
draft: false 
tags: ["Next.js"]
---

## Create new next project using typescript

```bash
npx create-next-app@latest --ts app-name
```

## Basic URL structure
- about -> example/about
- [slug] -> example/{slug}
- (group_name) -> example

![basic url structure nextjs](/images/0001.png)

## Layout
- layout only will be implemented on the current sub directory
- a good place to do data fetching

![basic url structure nextjs](/images/0002.png)

## All is Server Component
since next13, all compponent is server component by default. So it will be cache if the url is not dynamic, to prevent this can use below way:

### Refresh Cache on Static URL

```tsx

async function getNote() {
    const res = await fetch('http://127.0.0.1:8090/api/collections/posts/records',
        { cache: "no-store" } //to make it to not be liek static site
    );
    const data = await res.json()
    return data?.items as any[]
}

const PageNotes = async () => {
    const notes = await getNote();

}

export default PageNotes;
```

### Use SDK

```tsx
// refresh cache
export const dynamic = 'auto',
dynamicParams = true,
revalidate = 0,
fetchCache = 'auto',
runtime = 'nodejs',
prefferedRegion = 'auto'


async function getNote() {
    const db = new PocketBase('http://127.0.0.1:8090');
    const data = await db.collection('posts').getList()
    return data?.items as any[]
}

const PageNotes = async () => {
    const notes = await getNote();
}

export default PageNotes;
```

### Retain Cache on slug URL
```tsx
async function getNote(noteID:string) {
    const res = await fetch(`http://127.0.0.1:8090/api/collections/posts/records/${noteID}`,
        {
            next: {revalidate: 10} //will refresh every 10 second
        }
    ); 
    const data = await res.json()
    return data;
}

const NotePage = async ({params}: any) => {
    const note = await getNote(params.id);
}
 
export default NotePage;
```

# Loading and Error

- loading.tsx -> this component will be rendered when data fetching occur
- error.tsx -> this component will be rendered when error occur

