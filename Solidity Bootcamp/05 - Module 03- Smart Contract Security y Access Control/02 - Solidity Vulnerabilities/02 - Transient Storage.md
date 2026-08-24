# Transient Storage

This section will explain **transient storage** in Solidity, how it differs from regular storage and memory, and how to use it in a contract. It starts by reviewing storage (persistent on the blockchain) and memory (cleared after each function call). Transient storage sits in between: data persists only for the duration of a transaction. The section provides examples showing how to store and retrieve data in regular storage versus transient storage, including interactions between contracts and how to specify storage slots for transient data.

It also describes what a **reentrancy attack** is, demonstrates how it occurs when an external call is made before updating the contract’s state, and presents techniques to prevent it (such as the **checks-effects-interactions** pattern, `ReentrancyGuard`, or using transient storage to handle temporary values).

> Note: Since Solidity 0.8.28, the transient keyword is available. This allows developers to declare transient variables directly without relying on low-level opcodes like TSTORE and TLOAD. [See Solidity docs.](https://docs.soliditylang.org/en/v0.8.30/contracts.html#transient-storage)

[Video: Transient Storage | Solidity 0.8](https://www.youtube.com/watch?v=0-hiB5I39Mk)

## Links

- [Transient Storage | Solidity 0.8](https://www.youtube.com/watch?v=0-hiB5I39Mk)
