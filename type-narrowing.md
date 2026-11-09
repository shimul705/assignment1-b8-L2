# Type Narrowing in TypeScript

## Introduction

What is Type Narrowing in TypeScript? 
When a value can have more than one type, TypeScript will not let you use methods that belong to only one of them. Type narrowing is the process of checking a value at runtime so TypeScript knows its exact type inside a block of code. some examples are given below:

## Narrowing with `typeof`

`typeof` works for types like `string`, `number` and `boolean`. In the example below, `value` can be any of these three `string`, `number` and `boolean`. Inside the first `if` block TypeScript knows it is a string, so `toUpperCase()` is allowed. In the `else if` block it is a number, so `toFixed()` is allowed. In the last `else` block it can only be a boolean.

```ts
const print = (value: string | number | boolean) => {
  
  if (typeof value === "string") { 
    return value.toUpperCase();
  } 
  else if (typeof value === "number") { 
    return value.toFixed(2);
  } 
  else { 
    return value;
  }
};
```

## Narrowing with `instanceof`

it checks an object was created by a specific class or not. In the example below, `x` might be a `Date` object or a plain string. Inside the `if` block TypeScript knows it is a `Date`, so can call `x.toISOString()` directly. After the `if`, `x` can only be a string, so we first turn it into a `Date`.

```ts
const showDate = (x: Date | string) => {
  
  if (x instanceof Date) {
    console.log(x.toISOString());
    return;
  }

  const date = new Date(x);
  console.log(date.toISOString());
};

showDate("1971-12-16");
```

## Narrowing with `in`

The `in` operator checks whether a property exists on an object. It's useful for types like `Bird` and `Fish`, because they don't exist at runtime and can't be checked with `instanceof`. If `"fly"` is in `animal`, TypeScript knows it is a `Bird`. After the `if`, can only be a `Fish`, so `swim()` is allowed.

```ts
type Bird = { fly: () => void };
type Fish = { swim: () => void };
const move = (animal: Bird | Fish) => {
  
  if ("fly" in animal) {
    animal.fly();
    return;
  }

  animal.swim();
};
```

## Conclusion

Type narrowing lets us write flexible functions without losing type safety. Use `typeof` for primitives, `instanceof` for class instances and `in` for plain objects. TypeScript follows these checks and gives correct completion and errors in every branch.
