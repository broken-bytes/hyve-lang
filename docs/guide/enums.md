---
sidebar_position: 6
description: Enumerations in hyve
---

# Enumerations

Enumerations provide a concise way to declare common related values. Unlike `enum` in C, they provide scope, allow to have functions as part of them, and are generally more type safe.

An enum is defined like this:

```hyve
enum State: Int {
    case on = 0
    case off = 1
}
```

And used like this:

```hyve
var state: State = .on

if state == .off {
    ...
}
```

As mentioned earlier, enums may contain functions:

```hyve
enum State {
    case on = 0
    case off = 1

    fn string() -> String {
        return if self == .on {
            "ON"
        } else {
            "OFF"
        }
    }
}

var state: State = .on

print(state.string())
```
