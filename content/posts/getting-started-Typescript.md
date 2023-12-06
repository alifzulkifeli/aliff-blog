---
title: "Getting Started Typescript"
date: 2023-12-06T22:35:08+08:00
description: ""
draft: true 
tags: ["TypeScript"]
---

# Setting Up TypeScript for Your Project

TypeScript is a powerful tool that enhances JavaScript with types, making your code more robust and maintainable. Let's walk through setting up TypeScript in your project.

## Step 1: Initialize TypeScript Configuration

Start by initializing a TypeScript configuration file:

```bash
tsc --init
```

This command creates a tsconfig.json file in your project root, which is the heart of your TypeScript setup. It's where you'll specify how TypeScript compiles your code.

## Step 2: Configuring tsconfig.json

Edit the tsconfig.json file to suit your project needs. Here's a basic setup:

```json
{
  "compilerOptions": {
    "target": "es2016", // Sets the JavaScript version for output
    "module": "commonjs", // Defines the module system
    "rootDir": "./src", // Source files location
    "outDir": "./dist", // Output directory for compiled files
    "removeComments": true, // Removes comments in the output
    "noEmitOnError": true // Prevents output generation on error
  }
}
```

These settings will ensure your TypeScript compiles into the desired version of JavaScript, with comments removed for production readiness.

## Step 3: Compiling TypeScript

To compile your TypeScript code, simply run:

```bash
tsc
```

This command looks for tsconfig.json and compiles your code based on the specified settings.

## Step 4: Generating Source Maps

For easier debugging, enable source maps in your tsconfig.json:

```json
{
  "compilerOptions": {
    "sourceMap": true // Generates source map files
  }
}
```

Source maps help in debugging the original TypeScript source in tools like Chrome DevTools.

## Step 5: Integrating with Debugging Tools

If you're using VS Code, you can integrate TypeScript compilation with your debugging workflow. Add the following line to your launch.json:

```json
{
  "preLaunchTask": "tsc: build - tsconfig.json"
}
```

If your tsconfig.json is located in a subfolder, adjust the path accordingly.
