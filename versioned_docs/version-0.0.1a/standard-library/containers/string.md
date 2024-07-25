---
sidebar_position: 1
description: The string type used for convenient text handling.
---

# String

The string container type is a wrapper over a char array with automatic memory management, resizing and shrinking. It provides common functionality like substrings, string-ranges and string comparisons.

## Working with Strings

Strings are created like any other struct type:

```hyve
// Define the type and convert char array to String implicitly
var string: String = ""
// Or create a string explicitly
var string = String.create("")
```

:::note
String fulfills the `Convertible` and `Constructable` contracts so it can be used as a char pointer, or created via a char array.
:::

## Substrings

Strings may be sliced into substrings. Substrings are parts of a string.

Creating a substring is easy:

```hyve
var str: String = "Foo, Bar"

// Reads `Foo`
var foo = str.substring(from: 0, count: 3)
```

Alternatively, a substring can be constructed from `from` to `to`:

```hyve
var str: String = "Foo, Bar"

// Reads `Foo`
var foo = str.substring(from: 0, to: 2)
```

:::danger
Both substring functions will result in a panic if the string does not have enough characters
:::

## String attributes

The length of a string is retrieved by accessing the `length` property:

```hyve
var str: String = "Foo, Bar"

// Prints 8
print(str.length)
```

The underlying memory can be accessed via the `data()` function:

```hyve
var str: String = "Foo, Bar"

// Prints some address
print(str.data())
```

## String ranges

String fulfills the `Iterable` contract, allowing it to be used by iterators like `for` loops:

```hyve
var str: String = "Foo, Bar, Foobar"

// Use each character
for character in str {
    ...
}
```

## String comparison

String fulfills the `Comparable` contract, allowing it to be compared against char arrays and other strings or string views:

```hyve
var foo = "Foo"
var fooStr: String = "Foo"

// Compare
if foo == fooStr {
    // Works because String has a `compare(with: Char*)` function.
}
```

## String Views

A string view is a non-owning reference to a string. It only holds an immutable reference, allowing comparison and iteration of the string. Views are faster to pass around and are geenrally favoured when ownership should remain on the string the veiw was created for.

A string view is created like this:

```hyve
var str: String = "Foo, Bar"
var view = StringView.from(string: str)

// Iterate over the characters like it was a regular string
for character in view {
    ...
}
```
