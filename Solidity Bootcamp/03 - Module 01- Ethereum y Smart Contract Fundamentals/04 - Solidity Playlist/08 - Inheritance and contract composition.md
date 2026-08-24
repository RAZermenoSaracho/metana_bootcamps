# Inheritance and contract composition

As your contracts grow, you'll want to share logic across multiple contracts rather than copy-paste it. This section covers Solidity's inheritance model from single parent-child relationships to multiple inheritance and how Solidity resolves conflicts between them. You'll learn how to pass arguments to parent constructors, call parent function implementations using `super`, and use `virtual` and `override` to control which version of a function gets executed. These patterns are the foundation of most standard contract libraries you'll use in the real world.

### **Inheritance**

Explains how smart contracts can inherit from other contracts in Solidity. Demonstrates single inheritance (one contract extending another), including overriding functions and using the virtual and override keywords.

<https://www.youtube.com/watch?v=Ck5PUwL2D6I>

### **Multiple Inheritances**

Discusses how to handle multiple inheritance in Solidity (where a contract inherits from more than one base contract). Explains Solidity’s method resolution order and how to use the override keyword to resolve function name conflicts.

<https://www.youtube.com/watch?v=ITxPOG9Djwc>

### **Calling Parent Constructors**

Shows how to call a base contract’s constructor when inheriting. Provides examples of initializing parent contract state by passing parameters to the parent constructor in the derived contract’s constructor.

<https://www.youtube.com/watch?v=nPtEpw4olSk>

### **Calling Parent Functions**

Illustrates how to invoke a parent contract’s function from a child contract. Discusses using super to call the immediate parent implementation and how multiple inheritance can call ancestors’ functions.

<https://www.youtube.com/watch?v=lqRYnIejWMk>

## Links

- [https://www.youtube.com/watch?v=Ck5PUwL2D6I](https://www.youtube.com/watch?v=Ck5PUwL2D6I)
- [https://www.youtube.com/watch?v=ITxPOG9Djwc](https://www.youtube.com/watch?v=ITxPOG9Djwc)
- [https://www.youtube.com/watch?v=nPtEpw4olSk](https://www.youtube.com/watch?v=nPtEpw4olSk)
- [https://www.youtube.com/watch?v=lqRYnIejWMk](https://www.youtube.com/watch?v=lqRYnIejWMk)
