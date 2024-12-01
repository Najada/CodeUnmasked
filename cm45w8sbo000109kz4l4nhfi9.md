---
title: "Understanding JavaScript Deobfuscation: The Power of AST and Babel"
seoTitle: "JavaScript Deobfuscation: A Practical Guide to AST and Babel | Part 1"
seoDescription: "Learn how to deobfuscate JavaScript using Abstract Syntax Trees (AST) and Babel. A step-by-step guide with practical examples for developers and security re"
datePublished: Sun Dec 01 2024 17:47:08 GMT+0000 (Coordinated Universal Time)
cuid: cm45w8sbo000109kz4l4nhfi9
slug: understanding-javascript-deobfuscation-the-power-of-ast-and-babel
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733075006307/19448bb7-d215-4ee8-90f7-acd7079888a3.png
tags: programming-blogs, javascript, babel, reverse-engineering

---

In the realm of JavaScript reverse engineering, understanding Abstract Syntax Trees (ASTs) and Babel isn't just helpful—it's essential. Today, we'll dive deep into how these tools can transform seemingly unreadable code into clear, maintainable JavaScript.

## What is an AST? (not a space station)

An Abstract Syntax Tree (AST) is a tree representation of the syntactic structure of source code. Think of it as the skeleton of your code, showing how different parts relate to each other. Every identifier, operator, and control structure becomes a node in this tree.

Let's look at a simple example:

```javascript
function add(a, b) {
    return a + b;
}
```

This transforms into an AST structure that looks something like this: [Explore the AST here](https://astexplorer.net/).

```json
{
  "type": "Program",
  "body": [{
    "type": "FunctionDeclaration",
    "id": {
      "type": "Identifier",
      "name": "add"
    },
    "params": [
      {
        "type": "Identifier",
        "name": "a"
      },
      {
        "type": "Identifier",
        "name": "b"
      }
    ],
    "body": {
      "type": "BlockStatement",
      "body": [{
        "type": "ReturnStatement",
        "argument": {
          "type": "BinaryExpression",
          "operator": "+",
          "left": {
            "type": "Identifier",
            "name": "a"
          },
          "right": {
            "type": "Identifier",
            "name": "b"
          }
        }
      }]
    }
  }]
}
```

## Enter Babel: Your AST Swiss Army Knife

Babel is known as a JavaScript compiler, but it's really an AST manipulation powerhouse. Here's why it's crucial for deobfuscation:

1. **Parsing**: Babel can parse complex JavaScript into ASTs
    
2. **Traversal**: It provides tools to walk through and modify the AST
    
3. **Generation**: It can generate clean JavaScript from modified ASTs
    

### Setting Up Your Deobfuscation Environment

```javascript
// Required dependencies
const parser = require('@babel/parser');
const traverse = require('@babel/traverse').default;
const generate = require('@babel/generator').default;
const t = require('@babel/types');

// Function to parse code into AST
function parseCode(code) {
    return parser.parse(code, {
        sourceType: 'module',
        plugins: ['jsx']  // Add more plugins as needed
    });
}
```

What's coming next? We'll explore different ways code gets scrambled and show you exactly how to unscramble it. Each article will tackle one obfuscation trick, so you can master them step by step.

See you in the next article! 👋

---

<mark>This article is part of the "Unmasking JavaScript" series, where we explore various aspects of JavaScript deobfuscation and reverse engineering.</mark>