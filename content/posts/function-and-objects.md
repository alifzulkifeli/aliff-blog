---
title: "Function and Objects in TypeScript"
date: 2023-12-14T23:08:53+08:00
description: "Explore the intricacies of functions and objects in TypeScript."
draft: false 
tags: ["TypeScript"]
---

# Functions in TypeScript

TypeScript enhances JavaScript functions with type safety and additional configurations. Here are some useful compiler options for functions:

```json
{
  "noUnusedLocals": true,       /* Reports errors for unused local variables. */
  "noUnusedParameters": true,   /* Raises errors for unused function parameters. */
  "noImplicitReturns": true,    /* Ensures all code paths in a function explicitly return a value. */
}
```

## Function Declaration Example

```ts
function calculateTax(income: number, year: number): number {
    if (year < 2022) {
        return income * 1.2
    }
    return income * 1.3
}
calculateTax(10_000, 2023)
```

## Setting Default Parameter Values

```ts
function calculateTax(income: number, year = 2023): number {
    if (year < 2022) {
        return income * 1.2;
    }
    return income * 1.3;
}
calculateTax(10_000); // Default year is 2023
```

# Objects in TypeScript

TypeScript allows you to define the shape of an object with specific types for properties.

## Declaring Objects
```ts
let employee: {
    id: number,
    name: string
} = {id: 1, name: 'aliff'}
```

## Set object property optional
```ts
let employee: {
    id: number,
    name: string,
    age?: number // Optional property
} = { id: 1, name: 'Aliff' };
```

## Readonly Properties
```ts
let employee: {
    readonly id: number,
    name: string,
    age?: number
} = {id: 1, name: 'aliff'}
```

## Adding Methods to Objects
```ts
let employee: {
    readonly id: number,
    name: string,
    age?: number,
    retire: (date: Date) => void
} = {
    id: 1, 
    name: 'Aliff', 
    retire: (date: Date) => {
        console.log(`Retirement date: ${date}`);
    }
};
```