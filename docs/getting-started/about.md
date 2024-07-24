---
sidebar_position: 1
description: A Modern Language for a Secure, Concurrent World
---

# About Hyve

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# A Modern Language for a Secure, Concurrent World

Hyve is a cutting-edge programming language designed to empower developers to build robust, high-performance applications across a wide range of platforms. 

By blending modern language principles with systems programming sensibilities, Hyve strikes a balance between safety, productivity, and control; All without any runtime cost by providing zero cost abstractions for common paradigms.

:::warning
Hyve is **not** a finished programming language. Most features are missing and the compiler might produce bad code.
:::

## Key Features

<Tabs>

<TabItem value="performance" label="Performance" default>

- **Zero-Cost Abstractions:** Hyve's design philosophy emphasizes zero-cost abstractions, ensuring that high-level code can achieve the performance of hand-tuned, low-level implementations.
- **Manual Memory Management:** Hyve provides developers with precise control over memory allocation and deallocation, minimizing overhead and maximizing performance in critical scenarios.

</TabItem>

<TabItem value="safety" label="Safety">

- **Immutability by Default:** Hyve promotes immutability as a core principle, leading to more predictable code and easier concurrency management. Mutable state is possible but requires explicit declaration.
- **Optional Types:** Hyve's optional types enforce explicit handling of potentially missing values, eliminating a whole class of null pointer errors.
- **Memory Safety:** Hyve comes with a set of smart pointer types to prevent common memory-related issues like leaks and dangling pointers.

</TabItem>

<TabItem value="concurrency" label="Concurrency">

- **Async-First Design:** Hyve is built from the ground up to support asynchronous programming, making it easier to build responsive and efficient applications that can handle concurrent operations seamlessly.


</TabItem>

</Tabs>

## Why Choose Hyve?

- No performance compromises: You get what you pay for. No hidden runtime burden.
- Cross-Platform Compatibility: Write code once and deploy it across a wide range of platforms, including Windows, macOS, and Linux.
- Strong Security Focus: Hyve prioritizes security through type safety, bounds checking, and other measures to protect against vulnerabilities.
- Expressive and Enjoyable: Hyve combines the power and flexibility needed for complex projects with the expressiveness and ease of use of a scripting language.
