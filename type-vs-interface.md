# Type Aliases vs Interfaces in TypeScript

## Introduction

Let's know about Type Aliases vs Interfaces in TypeScript. TypeScript gives us two ways to describe the shape of data: `type` aliases and `interface`. They look similar, but they work differently in a few important ways. Knowing differences helps us to pick the right path.

## What They Share

Apparently they Both can describe objects and both can be extended. Below, `Cat` gets `species` from `Animal` and `Car` gets `brand` from `Vehicle`.

```ts
interface Animal {
  species: string;
}
interface Cat extends Animal {
  breed: string;
}
type Vehicle = {
  brand: string;
};
type Car = Vehicle & {
  //? "&" symbol is used to perform intersection
  model: string;
};
```

## Core Differences

**1. What they can describe:** An `interface` is mainly used for object shapes and a `type` can also give a name to a primitive like `number` or to a union like `"admin" | "member"`. An interface cannot do this.

```ts
type ID = number;
//! interface id = number

type Role = "admin" | "member";
//! interface "admin" | "member"
```

**2. Declaration merging:** Interfaces with the same name merge automatically. Here both `IEmployee` declarations merge together, so `employee` have both `name` and `id`. Type aliases cannot be declared twice, so `TEmployee` is not valid.

```ts
interface IEmployee {
  name: string;
}
interface IEmployee {
  id: number;
}
// both interface above represents this same thing
// interface IEmployee {
//   name: string;
//   id: number;
// }

///! This is not valid
// type TEmployee = {
//   name: string;
// };
// type TEmployee = {}

const employee: IEmployee = {
  id: 123,
  name: "ABC",
};
```

So, This is useful when the same object shape is described in multiple place.

**3. Extension style:** Interfaces use `extends`, like `Cat extends Animal`. Types use the intersection operator `&`, like `Car = Vehicle & { ... }`. Both give the same result: a new type with all the properties.

## When to Choose Which

 Use `interface` for object shapes, like `Cat` or `IEmployee`, especially when they may be extended or merged later. Use `type` for primitives, unions and literal types, like `ID` and `Role`.

## Conclusion

Interfaces are best for describing objects that can grow. Type aliases are more flexible for composing types. Pick one style for objects and stay consistent across project.
