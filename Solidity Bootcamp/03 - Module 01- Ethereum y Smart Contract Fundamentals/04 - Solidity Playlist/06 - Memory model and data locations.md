# Memory model and data locations

One of Solidity's most important and most misunderstood concepts is where data actually lives. This section explains the three data locations: `storage` for persistent on-chain state, `memory` for temporary data within a function call, and `calldata` for read-only function inputs, and how choosing the wrong one wastes gas or causes bugs. You'll also build the Ownable pattern from scratch, which puts constructors and storage together in a real access-control use case you'll see in nearly every production contract.

### **Storage, Memory and Calldata**

Explains the different data locations in Solidity: **storage** (persistent on-chain storage), **memory** (temporary data for function execution), and **calldata** (function input data location). Describes when to use each and how they affect gas and behavior.

<https://www.youtube.com/watch?v=wOCIhzAuhgs>

### **Ownable**

Introduces the “Ownable” pattern for access control. Shows how to designate an owner for the contract and restrict certain functions so that only the owner (or authorized addresses) can call them.

<https://www.youtube.com/watch?v=QEJYSuyYOfw>

### **Calling Parent Constructors**

Shows how to call a base contract’s constructor when inheriting. Provides examples of initializing parent contract state by passing parameters to the parent constructor in the derived contract’s constructor.

<https://www.youtube.com/watch?v=nPtEpw4olSk>

## Links

- [https://www.youtube.com/watch?v=wOCIhzAuhgs](https://www.youtube.com/watch?v=wOCIhzAuhgs)
- [https://www.youtube.com/watch?v=QEJYSuyYOfw](https://www.youtube.com/watch?v=QEJYSuyYOfw)
- [https://www.youtube.com/watch?v=nPtEpw4olSk](https://www.youtube.com/watch?v=nPtEpw4olSk)
