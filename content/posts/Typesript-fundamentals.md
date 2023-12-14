---
title: "Typesript Fundamentals"
date: 2023-12-14T21:20:15+08:00
description: ""
draft: false 
tags: ["TypeScript"]
---

TypeScript, a strongly typed programming language that builds on JavaScript, offers various built-in types to enhance the coding experience. Understanding these types is crucial for efficient TypeScript programming.

## Built-in Types

TypeScript's type inference allows variables to automatically be assigned a type based on the assigned value. However, explicitly defining the type is also possible.

### Example of Type Inference and Explicit Typing

```typescript
let profit = 123_456_789; // Inferred type: number
let explicitProfit: number = 123_456_789; // Explicit type: number

let variable; // Type: any
```

## The any Type

The any type is flexible as it can represent any JavaScript value, providing an escape hatch from strict type checking. Use this with caution as it can undermine the benefits of TypeScript's type system.

## Arrays

Arrays in TypeScript can be typed to contain elements of a specific type.

```ts
let numbers: number[] = [1, 2, 3];
```

## Tuples

Tuples are arrays with fixed lengths and ordered types.

```ts
let user: [number, string] = [1, "Aliff"];
```

## Enums

Enums are a way to define a set of named constants, enhancing code readability and maintainability.

```ts
enum Size { Small, Medium, Large };
let mySize: Size = Size.Small;
console.log(mySize); // Output: 0
```
