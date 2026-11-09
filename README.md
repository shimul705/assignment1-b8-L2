# 🧩 TypeScript Problem Solving — Types, Generics & OOP

Hey everyone! 👋 Welcome to my TypeScript assignment. Nothing scary here, I promise: just **8 small problems** and **2 blog posts**, all about the TypeScript basics we learned in class.

> **Programming Hero — Level 2 · Module 4 · Assignment 1 (B8A1)**

<p>
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-Strict-3178C6?style=for-the-badge&logo=typescript&logoColor=white">
  <img alt="Problems" src="https://img.shields.io/badge/Problems-8-2EA44F?style=for-the-badge">
  <img alt="Blogs" src="https://img.shields.io/badge/Blogs-2-131318?style=for-the-badge&logo=markdown&logoColor=white">
</p>

---

## 🔗 Links

Short on time? Here's everything in one place:

| | |
|---|---|
| **Solutions** | [solutions.ts](solutions.ts) |
| **Blog 1** | [Type Aliases vs Interfaces in TypeScript](type-vs-interface.md) |
| **Blog 2** | [Type Narrowing in TypeScript](type-narrowing.md) |
| **Live Site** | Nope, not this time. It's pure logic, no UI |

---

## 📌 Overview

So what's this all about? This assignment checks what we picked up in **Modules 1–3**: basic types, optional and rest parameters, readonly tuples, interfaces, type narrowing, generics, Promises and OOP.

There are 8 coding problems, all living in one file called `solutions.ts`, plus 2 blog posts where I explain a TypeScript topic in my own words.

Sounds easy, right? Well, there were a few rules, and break one of them and you lose marks, my friend 😅

- Everything goes in **one file**: `solutions.ts`. No splitting things up.
- Use the **exact names** from the question. `multiplyValue` means `multiplyValue`, not `multiplyvalue`.
- Every parameter and return value needs an **explicit type**. And `any`? Not allowed. Not even once.
- The output has to match the sample **exactly**: every space, comma and capital letter.
- No `console.log`, no test calls and no `// Problem 1` comments in the final file. Just clean code.

---

## ✨ Problems

### 1. `multiplyValue(value, multiplier?)`
Give it a number and an optional multiplier and it multiplies them. No multiplier? It just doubles the value. The sneaky part: passing `0` has to give `0` back, not double it.

### 2. `processInput(input)`
Takes a `string`, `number` or `boolean` and checks which one it got with `typeof`. Strings get trimmed and lowercased, numbers get multiplied by `10`, and booleans turn into `"Active"` or `"Inactive"`.

### 3. `formatCoordinate(coordinate)`
Takes a **readonly tuple** like `[23.81, 90.41, "Dhaka"]` and gives back `"Location: Dhaka (23.81, 90.41)"`. No rounding allowed. The numbers stay exactly as they are.

### 4. `concatenateArrays(...arrays)`
Throw in as many arrays as you like (as long as they're the same type) and you get one new combined array back, in the same order. It's **generic** with `<T>`, so it works with strings, numbers, anything.

### 5. `Course` + `getPopularCourses(courses, minStudents)`
First a `Course` **interface**, then a function that picks out the courses that are published *and* have enough students. It returns a fresh array, and the original stays untouched.

### 6. `pluckValues(items, key)`
Got a list of objects and only want one property from each? This does exactly that. The `K extends keyof T` part means you can only ask for keys that actually exist. Typos get caught right away.

### 7. `Employee` + `Manager`
Classic OOP time! `Employee` has a `protected` name and a `private` base salary. `Manager` extends it, adds a `private` department and calls `super(name, baseSalary)`. Simple and clean.

### 8. `validateAgeAsync(age)`
An `async` function that returns `Promise<string>`. If you're 18 or older, you wait 1 second and get `"Access Granted"`. Under 18? Rejected right away with an `Error`. Sorry kiddo! 🚫

---

## 📝 Blogs

Two short blog posts, written for anyone who's just starting out with TypeScript:

| Blog | Question | What's inside |
|---|---|---|
| [Type Aliases vs Interfaces in TypeScript](type-vs-interface.md) | Q1: What's the difference between `type` and `interface`, and when should you use each? | `extends` vs `&`, primitives and unions, declaration merging |
| [Type Narrowing in TypeScript](type-narrowing.md) | Q3: What is type narrowing? | `typeof`, `instanceof` and the `in` operator, with examples |

---

## 🛠️ Tech Stack

| Technology | What I used it for |
|---|---|
| **TypeScript** | Union types, readonly tuples, interfaces, generics, `keyof`, classes, access modifiers, `Promise<T>` |
| **JavaScript (ES6+)** | Arrow functions, destructuring, template literals, `for...of`, `filter()`, `map()`, `async/await`, `setTimeout` |
| **tsc (strict mode)** | Making sure there are zero type errors |

---

## 🧪 Sample Test Results

Every sample input from the assignment, and every single one passes ✅

| Function | Input | Output |
|---|---|---|
| `multiplyValue` | `10` / `10, 5` / `7, 0` | `20` / `50` / `0` ✅ |
| `processInput` | `"  TypeScript  "` / `7` / `true` / `false` | `"typescript"` / `70` / `"Active"` / `"Inactive"` ✅ |
| `formatCoordinate` | `[23.81, 90.41, "Dhaka"]` | `"Location: Dhaka (23.81, 90.41)"` ✅ |
| `formatCoordinate` | `[22.35, 91.78, "Chittagong"]` | `"Location: Chittagong (22.35, 91.78)"` ✅ |
| `concatenateArrays` | `["a", "b"], ["c", "d"]` / `[1, 2], [3, 4], [5]` | `["a", "b", "c", "d"]` / `[1, 2, 3, 4, 5]` ✅ |
| `getPopularCourses` | sample `courses`, `80` | `TypeScript Mastery`, `Next.js Pro` ✅ |
| `pluckValues` | `users, "name"` / `users, "id"` | `["Rakib", "Sadia", "Tariq"]` / `[1, 2, 3]` ✅ |
| `Manager.getDetails` | `new Manager("Alice", 50000, "Engineering")` | `"Employee: Alice, Base Salary: 50000"` ✅ |
| `Manager.getRoleInfo` | same manager | `"Manager of Engineering: Alice"` ✅ |
| `validateAgeAsync` | `20` | `"Access Granted"` after 1 second ✅ |
| `validateAgeAsync` | `15` | `Error: Access Denied: Must be 18 or older` ✅ |

---

## 📂 Project Structure

Just four files. Nice and tidy:

```
├── solutions.ts           # All 8 problem solutions
├── type-vs-interface.md   # Blog 1: Type Aliases vs Interfaces
├── type-narrowing.md      # Blog 2: Type Narrowing
└── README.md              # You're reading it right now 👀
```

---


## 📚 What I Learned

- Writing **type-safe functions** with optional, default and rest parameters.
- Using **union types** and narrowing them with `typeof`, `instanceof` and `in`.
- Keeping data safe with **readonly tuples** and never changing input arrays.
- Writing reusable **generic** functions, and limiting keys with `keyof`.
- Building classes with **`public`, `private` and `protected`** members, and extending them with `super`.
- Returning a typed **`Promise<string>`** that resolves after a delay or rejects with an `Error`.
- And the big one: the output has to match **exactly**, character by character. Close enough doesn't count!

---

## 👤 Author

**Shimul**
GitHub: [@shimul705](https://github.com/shimul705)

---

<sub>Thanks for stopping by! This is part of my Programming Hero learning journey, one assignment at a time. 🚀</sub>
