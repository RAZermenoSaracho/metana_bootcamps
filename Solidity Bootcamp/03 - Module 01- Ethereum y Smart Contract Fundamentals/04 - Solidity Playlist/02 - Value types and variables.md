# Value types and variables

Before you can write meaningful contracts, you need to know how Solidity stores and represents data. This section walks you through the core value types - integers, booleans, addresses, and more - and explains the three kinds of variables every contract uses: state variables that live on the blockchain, local variables that exist only during a function call, and global variables that give you context about the transaction and the block. You'll also learn when to reach for constants and immutables to save gas and lock in values at compile or deploy time.

### **Value Types**

Explains the fundamental data types in Solidity (e.g., uint, int, boolean, address, bytes32) and how to use them in contracts, including their default values and ranges.

<https://www.youtube.com/watch?v=8Tj-Th_S7NU>

### **State Variables**

Discusses state variables in Solidity, which store data on the blockchain. Explains how to declare state variables and how they persist between function calls.

<https://www.youtube.com/watch?v=hl692-xJPUQ>

### **Local Variables**

Explains local variables within functions – variables that exist temporarily during function execution. Shows the difference between local and state variables with examples.

<https://www.youtube.com/watch?v=5Gxzwn0SQDU>

### **Global Variables**

Covers special global variables provided by Solidity (like msg.sender, msg.value, block.timestamp, etc.) that give information about the blockchain, transactions, and execution context.

<https://www.youtube.com/watch?v=ryA86ZiSD-w>

### **Constants**

Shows how to define constant state variables in Solidity. Explains that constants are variables that cannot be changed after deployment and how using constants can reduce gas costs for certain operations.

<https://www.youtube.com/watch?v=y5uiQ9IJhMc>

### **Immutable**

Discusses immutable state variables in Solidity (introduced in 0.8). Shows how to declare variables as immutable which allows them to be set once in the constructor and then remain constant, combining flexibility of initialization with the gas savings of constants.

<https://www.youtube.com/watch?v=nQi8lVi4xT4>

## Links

- [https://www.youtube.com/watch?v=8Tj-Th_S7NU](https://www.youtube.com/watch?v=8Tj-Th_S7NU)
- [https://www.youtube.com/watch?v=hl692-xJPUQ](https://www.youtube.com/watch?v=hl692-xJPUQ)
- [https://www.youtube.com/watch?v=5Gxzwn0SQDU](https://www.youtube.com/watch?v=5Gxzwn0SQDU)
- [https://www.youtube.com/watch?v=ryA86ZiSD-w](https://www.youtube.com/watch?v=ryA86ZiSD-w)
- [https://www.youtube.com/watch?v=y5uiQ9IJhMc](https://www.youtube.com/watch?v=y5uiQ9IJhMc)
- [https://www.youtube.com/watch?v=nQi8lVi4xT4](https://www.youtube.com/watch?v=nQi8lVi4xT4)
