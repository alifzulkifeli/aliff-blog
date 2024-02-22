---
title: "Generics in Go"
date: 2024-02-10T08:07:05+08:00
description: "Generics allow programmers to write flexible, reusable functions and types that can work with any data type..."
draft: false 
tags: ["Go"]
---
# Generics in Go: A Comprehensive Guide

## Understanding Generics
Generics allow programmers to write flexible, reusable functions and types that can work with any data type. Before generics, Go developers had to rely on interfaces and type assertions to achieve similar functionality, which could be less efficient and more error-prone.

## Why Generics?
Generics can significantly improve your Go code by:

- Reducing Code Duplication: Write a function or data structure once, and use it with different types.
- Improving Performance: Avoid the overhead of runtime type assertions and interface conversions.
- Enhancing Type Safety: Catch errors at compile time rather than at runtime.

# How to Use Generics in Go
Generics in Go can be used with both functions and types. Let's explore how to use them in each case.

## Generic Functions
A generic function is declared by specifying type parameters in square brackets after the function name. Here's a simple example:

```go
package main

import "fmt"

// Generic function to swap values
func Swap[T any](a, b T) (T, T) {
    return b, a
}

func main() {
    a, b := Swap[int](1, 2)
    fmt.Println(a, b) // Output: 2 1

    x, y := Swap[string]("hello", "world")
    fmt.Println(x, y) // Output: world hello
}
```

In this example, `T` is a type parameter, and `any`` is a type constraint that means `T`` can be any type.

## Generic Types

Similarly, you can define generic types, such as custom slices, maps, or even more complex data structures. Here's how you can define a generic slice:

```go
package main

import "fmt"

// Generic slice type
type MySlice[T any] []T

// Method to add an element to the slice
func (s *MySlice[T]) Add(elem T) {
    *s = append(*s, elem)
}

func main() {
    var intSlice MySlice[int]
    intSlice.Add(1)
    intSlice.Add(2)
    fmt.Println(intSlice) // Output: [1 2]

    var stringSlice MySlice[string]
    stringSlice.Add("hello")
    stringSlice.Add("world")
    fmt.Println(stringSlice) // Output: [hello world]
}
```
