---
sidebar_position: 7
description: Structures in hyve
---

# Structures

Structure are the building blocks for every applications. They are generic, reusable bits of code that contain data and provide functionality in a scoped and secure way.
Unlike other C-based languages, Structures are defined in a single file, freeing the developer from the burden of having to maintain both an interface and implementation.

:::note
In hyve there is **no** concept of *classes*.

Structures represent both classes and structs found in other languages as the distinction of reference or value is made via allocation.
:::

A struct is defined like this:

```hyve
struct {
    ...
}
```

Structures may contain properties (variables) and functions (both reading and mutating):

```hyve
struct Ticket {
    let price = 22.99
    let seat = 3
    let row = 23
}

struct TicketServer {
    var leftTickets: [Ticket] = [Ticket { price: 22.99, seat: 2, row: 23 }]

    mut fn buyTicket(row: Int, seat: Int) {
        // Find ticket and remove it from the array ...
        self.leftTickets.remove(...)
    }

    fn availableTickets() -> [Ticket]& {
        return self.leftTickets
    }
}
```

:::note
Functions inside structs are called *methods*.

They automatically have a hidden `self` parameter than can be used inside of the function. `self` always points to the object itself.
:::

## Initialisation

Every struct can be initialised in two different ways

If all properties are accessible from outside the struct: Via the object literal:

```hyve
struct Ticket {
    let price: Float
}

var ticket = Ticket { price: 23.99 }
```

:::note
The properties of the struct need to have a possible default value if the object literal is used.

Otherwise the compiler will result in an error when not all properties are assigned in the object literal.

Invalid example:

```hyve
struct User {
    let userId: Int
}

struct Ticket {
    let price: Float
    let user: User
}

// Error: user has no default value but was not initialised in object literal
var ticket = Ticket { price: 23.99 }
```

:::

Or via a special `init` function:

```hyve
struct Ticket {
    let price: Float

    init(price: Float) {
        self.price = price
    }
}

var ticket = Ticket(price: 23.99)
```

When using init, every property must be initialised:

```hyve
struct Ticket {
    let price: Float
    let seat: Int

    init(price: Float) {
        self.price = price
        // Error: seat was not initialised in init
    }
}

var ticket = Ticket(price: 23.99)
```

To allow default values for custom structs, an empty init can be provided:

```hyve
struct User {
    var userId: Int

    init() {
        userId = 0
    }
}

// Now we can do this:
struct Ticket {
    let row: Int
    let price: Float
    let user: User
}

// User is automatically created via its default `init`
var ticket = Ticket { row: 1, price: 22.99 }
```

A struct may have multiple `init` functions, as long as all properties are assigned. One `init` may call another to achieve this:

```hyve
struct User {
    let userId: Int
    var money: Float

    init(userId: Int, money: Float) {
        self.userId = userId
        self.money = money
    }

    init() {
        init(userId: 0, money: 0)
    }

    init(userId: Int) {
        init(userId: userId, money: 0)
    }

    init(money: Float) {
        init(userId: 0, money: 22.99)
    }
}
```

:::note
When an `init` function is provided, the compiler disallows using the object literal
:::
