---
sidebar_position: 5
description: Functions in hyve
---

# Functions

In Hyve, there are two different types of functions, *mutating* functions and *reading* functions. By default, every functions is reading, disallowing mutation to its object.

## Reading functions

Reading functions are only used to calculate values, return properties etc. They cannot alter the state of their object but only *read* it.

A reading function is defined like this:

```hyve
fn foo() -> String {
    return ""
}

print(foo())
```

:::tip
Always use reading functions when you don't need to alter state. It makes code more concise and allows understanding side effects more easily.
:::

Functions may have parameters as well, like this:

```hyve
fn foo(bar: String) -> String {
    return "Foo" + bar
}

print(foo(bar: "Bar"))
```

## Mutating functions

If the function has a side effect, e.g. it alters the state of its object, the function must be declared at mutating, otherwise the compiler disallows such mutations:

```hyve
var value = 0

mut fn foo() -> Int {
    value += 1
    return value
}

// Prints 1
print(foo())
```

Just like reading functions, mutating functions can have parameters:

```hyve
var value = 0

mut fn foo(newValue: Int) -> Int {
    value = newValue
    return value
}

// Prints 23
print(foo(newValue: 23))
```

## Parameters

Parameters have some specialities in Hyve as well. There are three different ways of passing parameters. By value, by reference and by pointer. Additionally, the mutability of these parameters is also defined in the function signature.

For this, there are two keywords in Hyve. `mut` and `mod`. Likewise, we can use the Pointer or Reference Syntax that is used for variables as well:

- `mut` Allows mutation of an object and the reference, which means that the pointer *and* the object it points to may be changed.
- `mod` Allows only mutation of the object, not the pointer

Both keywords are applied to different parameter types:

- `mut` May only be used alongside pointer parameters as these are the only parameter types that actually allow access to the pointer.
- `mod` May be used on either pointer or reference types as it indicates that the object may change.

If no modifier is applied, the object may neither change nor the pointer to it, resulting in a truly immutable parameter.

An example of a function having a `mod` pointer parameter:

```hyve
fn foo(result: mod Int*, value1: Int, value2: Int) {
    // Changes the underlying value of result, not the pointer
    result = value1 + value2
    // The compiler would throw an error here as result is not `mut` allowing only mutations to the object.
    result = allocator.alloc(Int, 1)
}
```

An example of a function having a `mut` pointer parameter:

```hyve
fn foo(result: mut Int*, value1: Int, value2: Int) {
    // Creates a new Int on the heap and assigns its pointer to result
    result = allocator.alloc(Int, 1)
    // Assigns the result of value1 + value2 to the underlying memory of result
    result = value1 + value2
}
```

An example of a function having a `mod` reference parameter:

```hyve
fn foo(result: mod Int&, value1: Int, value2: Int) {
    // Assigns the result of value1 + value2 to the underlying memory of result
    result = value1 + value2
}
```

:::note
In Hyve, everything is passed by value unless it is a pointer type. This means if passing by reference is desired, the `&` reference syntax has to be used.
:::
