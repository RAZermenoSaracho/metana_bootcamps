# Ether and payable contracts

Smart contracts aren't just logic engines they can hold and move real value. This section covers everything you need to handle ETH safely: marking functions and addresses as `payable`, sending ETH out of a contract using `transfer`, `send`, and low-level `call`, and writing `fallback` and `receive` functions to control what happens when someone sends ETH directly to your contract address. You'll come away knowing the trade-offs between each sending method and the patterns that keep funds from getting stuck.

### **Payable**

Explains the payable modifier on functions and addresses, which is required to handle Ether transfers. Demonstrates how to write functions that can receive Ether, withdraw Ether, and best practices to handle Ether safely (e.g., using address(this).balance).

<https://www.youtube.com/watch?v=A4VMhRIWSs0>

### **Send ETH**

Covers various ways to send Ether from a smart contract (using .transfer, .send, and low-level .call). Explains the differences in error handling and gas forwarding for each method and recommends safe practices for sending Ether.

<https://www.youtube.com/watch?v=mlPc3EW-nNA>

### **Fallback**

Describes the fallback function and the receive Ether function in Solidity. Shows how a contract can react when it is sent Ether with no data or when a function called doesn’t exist, and how to write fallback logic (for example, for simple forwarding or logging).

<https://www.youtube.com/watch?v=CMVC6Tp9gq4>

## Links

- [https://www.youtube.com/watch?v=A4VMhRIWSs0](https://www.youtube.com/watch?v=A4VMhRIWSs0)
- [https://www.youtube.com/watch?v=mlPc3EW-nNA](https://www.youtube.com/watch?v=mlPc3EW-nNA)
- [https://www.youtube.com/watch?v=CMVC6Tp9gq4](https://www.youtube.com/watch?v=CMVC6Tp9gq4)
