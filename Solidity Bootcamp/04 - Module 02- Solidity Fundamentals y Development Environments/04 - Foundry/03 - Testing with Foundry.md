# Testing with Foundry

### Introduction | Testing with Foundry

Introduces Foundry, a fast Rust-based Ethereum testing framework. Shows how to set up a Foundry project and outlines the basics of writing and running Solidity tests with Foundry’s `forge test`. This video sets the stage for more advanced testing topics by covering project initialization and configuration.

[Video: Introduction | Testing with Foundry](https://www.youtube.com/watch?v=tgs5q-GJmg4)

### How to Write Basic Tests

Demonstrates writing simple unit tests for smart contracts using Foundry. Walks through creating a test contract (using Solidity) that inherits from `DSTest` (or similar), using assertions (`assertEq`, etc.), and testing basic contract functionality. It highlights Foundry’s syntax and tools for testing.

[Video: How to Write Basic Tests | Testing with Foundry](https://www.youtube.com/watch?v=HA0GWauMOsU)

### Set Solidity Compiler Version

Explains how to specify the Solidity compiler version in Foundry projects. Likely shows adjusting the `foundry.toml` configuration to set the `solc` version or using `pragma` statements in test contracts, ensuring that tests run with the intended compiler (for compatibility with certain language features).

[Video: Set Solidity Compiler Version | Testing with Foundry](https://www.youtube.com/watch?v=bmOxtjzFcbk)

### Remappings

Covers the concept of remappings in Foundry (and generally in Solidity projects). Shows how to configure import remappings in `foundry.toml` (for example, mapping `@openzeppelin` to a local `lib/openzeppelin-contracts` path). This makes it easier to manage dependencies in tests by telling the compiler where to find imported packages.

[Video: Remappings | Testing with Foundry](https://www.youtube.com/watch?v=7DK75j8csTA)

### Auto Format Code

Demonstrates Foundry’s automated code formatter. Likely introduces the `forge fmt` command which formats Solidity code according to a standard style. The video may show before-and-after examples of code formatting and explain the importance of consistent style in collaborative projects.

[Video: Auto Format Code | Testing with Foundry](https://www.youtube.com/watch?v=k55TIWUFLbQ)

### Console Log

Shows how to use Foundry’s `console.log` (enabled via the `forge-std/console.sol` library) to print debug information in tests. Provides examples of logging variables and messages during test execution, which can help in debugging failing tests by inspecting intermediate values on the test output.

[Video: Console Log | Testing with Foundry](https://www.youtube.com/watch?v=pO3kfXCFLuE)

### Authentication

Covers testing access control and authentication logic using Foundry. Likely demonstrates impersonating different addresses (via Foundry cheat codes like `vm.prank`) to simulate calls from various users, and testing that functions with `onlyOwner` or other access modifiers behave correctly by allowing authorized users and rejecting others.

[Video: Authentication | Testing with Foundry](https://www.youtube.com/watch?v=gYwO3Jbi4O4)

### Error

Demonstrates how to test for expected errors and reverts in Foundry. Shows how to use cheat codes like `vm.expectRevert` (or the `assertRevert` from DSTest) to anticipate that a certain call should fail, and then call the function to verify that it indeed reverts with the expected error message or error type.

[Video: Error | Testing with Foundry](https://www.youtube.com/watch?v=yY9lL4Jxkd8)

### Event

Shows how to verify events in Foundry tests. Possibly uses `vm.expectEmit` to set an expectation that a certain event will be emitted with specific parameters, then executes the contract call, and confirms that the event was logged. This ensures that events (like Transfer events in tokens, etc.) are properly emitted by the contract.

[Video: Event | Testing with Foundry](https://www.youtube.com/watch?v=GYwKDSSpzjQ)

### Time

Explains how to manipulate blockchain time in a Foundry test environment. Shows using cheat codes like `vm.warp` to change the block timestamp or `vm.roll` to change the block number, allowing tests to simulate the passage of time (for testing time-dependent functions like vesting, timelocks, or expiring options).

[Video: Time | Testing with Foundry](https://www.youtube.com/watch?v=B_3Kax70sF4)

### Send ETH

Demonstrates testing Ether transfers and payable functions in Foundry. Likely shows how to send Ether to contracts in tests by specifying `value` in calls or using `vm.deal` to set an address’s balance, and then verifying balances before and after to ensure Ether moved as expected when functions are called.

[Video: Send ETH | Testing with Foundry](https://www.youtube.com/watch?v=GuwUC-Wy_B0)

**Signature**

Shows how to test ECDSA signature functionality using Foundry. Possibly demonstrates generating a signature in a test (using `vm.sign` or an external library) and then calling the contract’s signature verification function (as built in the “Verify Signature” video) to assert that the signature is recognized correctly.

[Video: Signature | Testing with Foundry](https://www.youtube.com/watch?v=cs5IeYqviSQ)

### Fork

Shows Foundry’s ability to fork mainnet (or any network) state for testing. The video likely walks through writing a test that uses `vm.createSelectFork(<RPC URL>, <blockNumber>`) to pull live blockchain state, then interacting with a deployed contract (like calling a function on a live DeFi contract) within the test. This allows testing scenarios using real contract interactions and data.

[Video: Fork | Testing with Foundry](https://www.youtube.com/watch?v=eKxJZgp9CTg)

### Mint 1 Million DAI on Mainnet Fork

Uses Foundry’s forking and cheat codes to simulate minting tokens on a mainnet fork for testing. Likely shows how to impersonate the DAI contract’s owner or modify storage to give an address a large balance of DAI on a fork, demonstrating the power of cheat codes to set up test conditions (in this case, creating 1 million DAI out of thin air on a forked mainnet state) for verifying contract behavior.

[Video: Mint 1 Million DAI on Mainnet Fork | Testing with Foundry](https://www.youtube.com/watch?v=I8mzJxMBzs0)

### Fuzz

Introduces fuzz testing in Foundry, where the framework generates random inputs for your test functions to try and catch edge cases automatically. The video demonstrates how to write a test that uses fuzzing (by simply writing tests with parameters or using the `assert` style in Forge which automatically fuzzes inputs) and how Foundry will run the test multiple times with different data to ensure the contract holds up for all cases.

[Video: Fuzz | Testing with Foundry](https://www.youtube.com/watch?v=6sMOeuqwk-U)

### **Deploy Smart Contract With Foundry**

The video is a step-by-step tutorial on deploying an ERC20 token using Foundry, covering everything from setting up a .env file with RPC URLs, private keys, and an Etherscan API key to writing and compiling the Solidity contract, deploying it, minting tokens, and verifying the contract on Etherscan. It highlights the importance of simulating transactions before deployment and is aimed at developers interested in learning practical smart contract deployment workflows.

[Video: Deploy Smart Contract With Foundry](https://www.youtube.com/watch?v=AxnvSYxQC5o)

### **Print Storage, Functions and ABI with Foundry**

The video explains how to use Foundry’s **Forge inspect** command to quickly analyze smart contracts, summarizing state variables, functions, and interfaces without manual review. It’s aimed at developers needing fast insights and shows how command-line tools can streamline understanding contract functionality.

[Video: Print Storage, Functions and ABI with Foundry](https://www.youtube.com/watch?v=puUL_vTrXhA)

### **Manager Wallet and Send Transaction with Foundry Cast**

The video is a tutorial on using Foundry’s cast tool for Ethereum wallet management and smart contract interactions, covering how to import, list, remove wallets, send transactions, and call contracts-ideal for developers exploring blockchain execution.

[Video: Manager Wallet and Send Transaction with Foundry Cast](https://www.youtube.com/watch?v=0AugPHQpmKQ)

### **Import wallet into Foundry script using cast**

The video shows how to securely deploy Ethereum smart contracts with Foundry by using Cast for wallet management instead of exposing private keys. It focuses on deploying a counter contract while teaching safe deployment practices, environment variable setup, and improved security for developers.

[Video: Import wallet into Foundry script using cast](https://www.youtube.com/watch?v=7HRhRw3vrUI)

## Links

- [Introduction | Testing with Foundry](https://www.youtube.com/watch?v=tgs5q-GJmg4)
- [How to Write Basic Tests | Testing with Foundry](https://www.youtube.com/watch?v=HA0GWauMOsU)
- [Set Solidity Compiler Version | Testing with Foundry](https://www.youtube.com/watch?v=bmOxtjzFcbk)
- [Remappings | Testing with Foundry](https://www.youtube.com/watch?v=7DK75j8csTA)
- [Auto Format Code | Testing with Foundry](https://www.youtube.com/watch?v=k55TIWUFLbQ)
- [Console Log | Testing with Foundry](https://www.youtube.com/watch?v=pO3kfXCFLuE)
- [Authentication | Testing with Foundry](https://www.youtube.com/watch?v=gYwO3Jbi4O4)
- [Error | Testing with Foundry](https://www.youtube.com/watch?v=yY9lL4Jxkd8)
- [Event | Testing with Foundry](https://www.youtube.com/watch?v=GYwKDSSpzjQ)
- [Time | Testing with Foundry](https://www.youtube.com/watch?v=B_3Kax70sF4)
- [Send ETH | Testing with Foundry](https://www.youtube.com/watch?v=GuwUC-Wy_B0)
- [Signature | Testing with Foundry](https://www.youtube.com/watch?v=cs5IeYqviSQ)
- [Fork | Testing with Foundry](https://www.youtube.com/watch?v=eKxJZgp9CTg)
- [Mint 1 Million DAI on Mainnet Fork | Testing with Foundry](https://www.youtube.com/watch?v=I8mzJxMBzs0)
- [Fuzz | Testing with Foundry](https://www.youtube.com/watch?v=6sMOeuqwk-U)
- [Deploy Smart Contract With Foundry](https://www.youtube.com/watch?v=AxnvSYxQC5o)
- [Print Storage, Functions and ABI with Foundry](https://www.youtube.com/watch?v=puUL_vTrXhA)
- [Manager Wallet and Send Transaction with Foundry Cast](https://www.youtube.com/watch?v=0AugPHQpmKQ)
- [Import wallet into Foundry script using cast](https://www.youtube.com/watch?v=7HRhRw3vrUI)
