# Function Modifiers, Mappings, Error Handling

## Array Remove An Element By Shifting

Demonstrates a technique to remove an element from an array by shifting subsequent elements left to fill the gap. Shows an example of deleting an element at a given index and then reducing the array length.

[Video: Array Remove An Element By Shifting | Solidity 0.8](https://www.youtube.com/watch?v=szv2zJcy_Xs)

## Array Remove An Element By Replacing Last

Shows an alternative, gas-efficient method to remove an array element by swapping it with the last element and then popping the last element off. Discusses how this approach avoids looping but changes element order.

[Video: Array Remove An Element By Replacing Last | Solidity 0.8](https://www.youtube.com/watch?v=8i4CChP99XQ)

## Iterable Mapping

Discusses why standard mappings are not iterable and provides patterns to create iterable mappings. Shows how to maintain a list of keys for a mapping in order to iterate through all key-value pairs.

[Video: Iterable Mapping | Solidity 0.8](https://www.youtube.com/watch?v=YOjo_lvUhj8)

## Call Other Contracts

Shows how a contract can interact with another contract’s functions. Provides examples of calling functions on external contracts (both using interfaces and low-level calls) and discusses checking return values and handling failures when calling other contracts.

[Video: Call Other Contracts | Solidity 0.8](https://www.youtube.com/watch?v=6aQErpWPLbk)

## Interface

Introduces Solidity interfaces, which declare function signatures without implementation. Explains how to use interfaces to call external contracts (like ERC20 token interfaces) and how they help in interacting with contracts when you don’t need the full code.

[Video: Interface | Solidity 0.8](https://www.youtube.com/watch?v=tbjyc-VQaQo)

### Call

Focuses on the low-level `call` function in Solidity. Demonstrates using `address.call{value: …}(data)` to invoke functions or send Ether and how to handle the returned boolean success and bytes data. Also covers security considerations (reentrancy) when using `call`.

[Video: Call | Solidity 0.8](https://www.youtube.com/watch?v=xIAs2S9aCKo)

### Delegatecall

Explains the `delegatecall` opcode and how to use it in Solidity. Shows that `delegatecall` allows one contract to execute code in the context of another contract’s storage. Discusses use cases (like proxy patterns) and the serious security pitfalls if used incorrectly.

[Video: Delegatecall | Solidity 0.8](https://www.youtube.com/watch?v=uawCDnxFJ-0)

### New

Demonstrates deploying a new contract from within a contract using the `new` keyword. It’s a practical example of a contract factory that creates another contract instance and maybe keeps track of it, illustrating the concept of dynamic contract creation.

[Video: New | Solidity 0.8](https://www.youtube.com/watch?v=J2Wp2SHq1Qo)

### Library

Covers how to define and use libraries in Solidity. Shows how library contracts contain reusable code (like utility functions) that can be called without needing deployment (for internal libraries) or via DELEGATECALL (for deployed libraries), and examples like SafeMath usage.

[Video: Library | Solidity 0.8](https://www.youtube.com/watch?v=OH5mafV6jVE)

### Keccak256 Hash Function

Explains the use of the `keccak256` hash function in Solidity (which produces a 256-bit hash). Includes examples of hashing inputs (like combining variables into a single hash) and common use cases such as creating unique IDs or verifying signatures (via *ecrecover* with hashed messages).

[Video: Keccak256 Hash Function | Solidity 0.8](https://www.youtube.com/watch?v=wCD3fOlsGc4)

### Verify Signature

Shows how to verify an off-chain ECDSA signature within a Solidity contract. Walks through recovering the signer’s address from a message hash and signature using `ecrecover`, and demonstrates verifying that the recovered address matches an expected signer.

[Video: Verify Signature | Solidity 0.8](https://www.youtube.com/watch?v=vYwYe-Gv_XI)

### Access Control

Discusses implementing more complex access control schemes in Solidity (beyond a single owner). Likely demonstrates role-based access control (e.g., using multiple roles or an OpenZeppelin-like AccessControl) or multi-owner patterns to restrict function execution rights.

[Video: Access Control | Solidity 0.8](https://www.youtube.com/watch?v=tfk25O-5Ppg)

### Deleting Contracts

Explains how to delete or destroy a smart contract using `selfdestruct`. Shows that `selfdestruct` removes the contract’s bytecode and sends any remaining Ether to a specified address. Also covers the consequences of contract destruction (such as storage being cleared).

[Video: Deleting Contracts | Solidity 0.8](https://www.youtube.com/watch?v=ajCsPRl5S3Q)

`selfdestruct` has been updated—contracts can now only be destroyed within the same transaction in which they are created. For full details, refer to the official EIP here: <https://eips.ethereum.org/EIPS/eip-6780>

### Create2

Demonstrates the use of the CREATE2 opcode (accessible in Solidity via `new` with salt) to deploy contracts at a deterministic address. Explains how the address is computed (from deployer, salt, and bytecode hash) and shows a scenario where this can be useful (like precomputing contract addresses or counterfactual deployments).

[Video: Create2 | Solidity 0.8](https://www.youtube.com/watch?v=883-koWrsO4)

### Multi Call

Shows how to implement a multicall function that can execute multiple function calls in one transaction. For example, the contract may have a function that takes an array of encoded function calls and executes them sequentially, returning all results. This pattern is useful for bundling operations and reducing overhead.

[Video: Multi Call | Solidity 0.8](https://www.youtube.com/watch?v=PDR054Cy8qM)

### Multi Delegatecall

Explores an advanced concept where a contract uses delegatecall multiple times to execute code. Likely demonstrates a contract that can execute multiple functions on itself via `delegatecall` (somewhat like an extension of multicall, but ensuring state changes persist). It might also warn about security issues (this pattern relates to the Parity wallet bug).

[Video: Multi Delegatecall | Solidity 0.8](https://www.youtube.com/watch?v=NkTWU6tc9WU)

### ABI Decode

Illustrates how to use `abi.decode` in Solidity to decode raw bytes data into meaningful values. Shows scenarios like decoding function call data or output data (for example, decoding bytes returned from a low-level call into specific types). This is helpful for building low-level contract proxies or handling dynamic call results.

[Video: ABI Decode | Solidity 0.8](https://www.youtube.com/watch?v=LTh58SFEYqE)

### Bitwise Operators

Explains how to use bitwise operations (AND, OR, XOR, NOT, bit shifts) in Solidity. Provides examples of manipulating binary representations of numbers, which can be useful for low-level optimizations or encoding multiple values in a single uint (bit packing).

[Video: Bitwise Operators | Solidity 0.8](https://www.youtube.com/watch?v=i2o4TfSC9nA)

### Most Significant Bit using Binary Search Code

Shows how to find the index of the most significant set bit in a number using a binary search approach in Solidity. This can be used to efficiently compute floor(log2(x)). The video likely steps through an algorithm that checks halves of the 256-bit number to zero in on the highest set bit position.

[Video: Most Significant Bit using Binary Search Code | Solidity 0.8](https://www.youtube.com/watch?v=M6awK0lskR4)

### Call Functions with Key Value Inputs

Demonstrates Solidity’s support for named (key-value) function parameters when calling functions. Shows how to call a function by specifying parameter names (e.g., `myFunction{value:1 ether}(arg1: 123, arg2: true)`) and explains that while the feature improves readability, it’s mainly available for clarity in internal and external calls within Solidity.

[Video: Call Functions with Key Value Inputs | Solidity 0.8](https://www.youtube.com/watch?v=Y6mMnIZ7AAo)

### 3 Ways to Encode Call Data

Explores different methods to encode function call data manually. Likely demonstrates using `abi.encode,` `abi.encodePacked`, and `abi.encodeWithSignature` (or `abi.encodeWithSelector`) to produce transaction data, and explains scenarios where each is useful (e.g., constructing calldata for low-level calls or hashing).

[Video: 3 Ways to Encode Call Data | Solidity 0.8](https://www.youtube.com/watch?v=70_2YHJvKIc)

### Unchecked Math

Shows how to use the `unchecked` block in Solidity 0.8 to bypass overflow/underflow checks. Explains that Solidity 0.8 by default checks arithmetic operations for overflow, and demonstrates wrapping operations in `unchecked { ... }` when you intentionally want wrapping behavior or to save gas when you are certain overflow cannot occur.

[Video: Unchecked Math | Solidity 0.8](https://www.youtube.com/watch?v=_pvup5lyC3Q)

### Input and Output with Fallback

Demonstrates how to handle inputs and outputs through a contract’s fallback function. Shows an example where the fallback function can accept call data, parse it (if using assembly), and return data. This is an advanced usage where the fallback behaves like a regular function, enabling proxy-like behavior or contract multiplexing by examining `msg.data`.

[Video: Input and Output with Fallback | Solidity 0.8](https://www.youtube.com/watch?v=hcQyRmFOmvA)

### Function Types

Here, we’ll explore what *function types* are in Solidity. These are the types that represent functions themselves. You can use them to assign functions to variables, pass functions as parameters, or even return functions from other functions. Solidity provides two kinds of function types: internal functions and external functions and we’ll dive into both.

<https://docs.soliditylang.org/en/v0.8.30/types.html#function-types>

## Links

- [Array Remove An Element By Shifting | Solidity 0.8](https://www.youtube.com/watch?v=szv2zJcy_Xs)
- [Array Remove An Element By Replacing Last | Solidity 0.8](https://www.youtube.com/watch?v=8i4CChP99XQ)
- [Iterable Mapping | Solidity 0.8](https://www.youtube.com/watch?v=YOjo_lvUhj8)
- [Call Other Contracts | Solidity 0.8](https://www.youtube.com/watch?v=6aQErpWPLbk)
- [Interface | Solidity 0.8](https://www.youtube.com/watch?v=tbjyc-VQaQo)
- [Call | Solidity 0.8](https://www.youtube.com/watch?v=xIAs2S9aCKo)
- [Delegatecall | Solidity 0.8](https://www.youtube.com/watch?v=uawCDnxFJ-0)
- [New | Solidity 0.8](https://www.youtube.com/watch?v=J2Wp2SHq1Qo)
- [Library | Solidity 0.8](https://www.youtube.com/watch?v=OH5mafV6jVE)
- [Keccak256 Hash Function | Solidity 0.8](https://www.youtube.com/watch?v=wCD3fOlsGc4)
- [Verify Signature | Solidity 0.8](https://www.youtube.com/watch?v=vYwYe-Gv_XI)
- [Access Control | Solidity 0.8](https://www.youtube.com/watch?v=tfk25O-5Ppg)
- [Deleting Contracts | Solidity 0.8](https://www.youtube.com/watch?v=ajCsPRl5S3Q)
- [Create2 | Solidity 0.8](https://www.youtube.com/watch?v=883-koWrsO4)
- [Multi Call | Solidity 0.8](https://www.youtube.com/watch?v=PDR054Cy8qM)
- [Multi Delegatecall | Solidity 0.8](https://www.youtube.com/watch?v=NkTWU6tc9WU)
- [ABI Decode | Solidity 0.8](https://www.youtube.com/watch?v=LTh58SFEYqE)
- [Bitwise Operators | Solidity 0.8](https://www.youtube.com/watch?v=i2o4TfSC9nA)
- [Most Significant Bit using Binary Search Code | Solidity 0.8](https://www.youtube.com/watch?v=M6awK0lskR4)
- [Call Functions with Key Value Inputs | Solidity 0.8](https://www.youtube.com/watch?v=Y6mMnIZ7AAo)
- [3 Ways to Encode Call Data | Solidity 0.8](https://www.youtube.com/watch?v=70_2YHJvKIc)
- [Unchecked Math | Solidity 0.8](https://www.youtube.com/watch?v=_pvup5lyC3Q)
- [Input and Output with Fallback | Solidity 0.8](https://www.youtube.com/watch?v=hcQyRmFOmvA)
