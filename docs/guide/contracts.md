---
sidebar_position: 8
description: Contracts in hyve
---

# Contracts

Contracts are something that a struct must adhere to. They are like like contracts in the real world. One party defines the contract and the other one agrees to the terms.

This is exactly how contracts work in Hyve. A struct has to fulfill a contract if it wants to use it.

This is how a contract is defined:

```hyve
contract Buyable {
    mut fn buy()
}
```

The code can be read as "define a contract that ensures all signing parties need to implement a mutating buy function".

Accordingly, a struct may use a contract like this:

```hyve
struct Ticket: Buyable {
    var isSold = false

    mut fn buy() {
        isSold = true
    }
}
```

Contracts may also require the struct to implement some properties:

```hyve
contract Countable {
    var count: Int
}

struct Counter: Countable {
    var count: Int = 0
}
```

Additionally, contracts can force to specifiy a generic:

```hyve
contract Container<T> {
    var items: [T]

    mut fn append(item: T) {
        // Add to the items
    }
}

struct List: Container<Int> {
    var items: [Int]

    mut fn append(item: Int) {
        ...
    }
}
```

Generics can also have constraints:

```hyve
contract Container<T: where T is Numeric> {
    var items: [T]

    mut fn append(item: T) {
        // Add to the items
    }
}

// Error: User is not a numeric type
struct List: Container<User> {
    var items: [User]

    mut fn append(item: User) {
        ...
    }
}
```
