# Solidity Development with Foundry

This tutorial introduces Foundry, covering its installation and key tools like Cast, Anvil, Chisel, and Forge. It walks you through initializing projects, creating and running tests, including fuzzing and invariant testing to help you master Foundry for smart contract development.

[Video: Solidity Development with Foundry: Cast, Anvil, Chisel, and Forge](https://www.youtube.com/watch?v=K83Y9NMSBVo)

**Transcript for the AI**

Hello everyone, and welcome to today’s session! My name is Peter Robinson, and I’m thrilled to have Christian on the line to share his expertise on Foundry and its related tools. Christian, why don’t you introduce yourself before we dive in?

Christian: Sure, it’s actually one of my first slides, so let me go ahead and share them. Can you see my slides and hear me well?

Peter: Yes, everything looks good.

Christian: Alright, great. A bit about me: I’m a long-time listener, first-time caller, so to speak, of the show. I got into smart contract development during the COVID lockdown, and I’ve been pretty much focused on it ever since. I’m also an open-source enthusiast, always trying to give back where I can. I’ve been a big fan of Foundry since its early days, both as a user and an occasional contributor. I’m super excited to share my enthusiasm and knowledge about the project with you all today. If you have any questions, corrections, or want to reach out, feel free to contact me on Telegram. You can also check out my GitHub to see what I’m working on. Without further ado, let’s talk about Foundry.

Foundry is a smart contract development toolkit, somewhat similar to tools like Hardhat or Truffle, but it does things a bit differently, which I’ll highlight today. As far as I know, it’s an extended fork of a previous project called DappTools, so if you’re familiar with that, you’ll notice similarities in the interface and philosophy. Foundry is implemented in Rust, which makes it incredibly fast. As a side note, it’s a fantastic project for anyone interested in contributing to open-source Rust projects. The community is amazing and very welcoming to new contributors, making it a great opportunity to learn Rust.

Foundry consists of four main components. A lot of content out there focuses heavily on Forge, the primary testing framework, compilation, and scripting tool, but there are three other powerful tools in the toolkit: Cast, Anvil, and Chisel. Today, I’ll give a quick overview of these three, teasing what they’re about and how you can use them, and then dive deeper into Forge, focusing mainly on testing and a bit on scripting.

Let’s start with how to get started with Foundry. Unlike Hardhat, Foundry isn’t a JavaScript framework, so you can’t install it with npm or Yarn. Instead, it uses its own installer called Foundryup. The command to download and initialize Foundryup is straightforward, and once installed, it adds the Foundryup command to your terminal path. You can use it to install Foundry for the first time and manage versions, such as upgrading or downgrading. After installation, you’ll have access to the four toolkit commands: Forge, Cast, Anvil, and Chisel, each available as command-line tools to leverage their functionalities.

First up is Cast. Cast is a versatile tool for interacting with Ethereum or any EVM-compatible blockchain. It’s great for ad-hoc tasks like retrieving data about a block, transaction, or address, making calls to contracts, executing transactions, reading specific storage values, encoding and decoding call data, and much more. It’s particularly useful for debugging the state of a chain or a local test node. Cast has a vast array of commands—use the help command to explore them all. I’ll highlight two that have been productivity game-changers for me.

The first is `cast interface`. This command takes a contract address and automatically generates a Solidity interface file for you. If you’ve ever worked on a smart contract integrating a third-party contract, you might have manually copied function signatures from the source code, removed the function bodies, and created an interface. Cast automates this process, ensuring you include all functions, including those from inherited contracts. It typically uses Etherscan to fetch the contract’s ABI, so it works best for verified contracts or those you’re developing locally. For other chains, you can provide a custom Etherscan URL. This has saved me a ton of time.

The second command is `cast run`. Honestly, this alone makes installing Foundry worthwhile. It’s a game-changer for debugging transactions. It re-simulates a given transaction on a local EVM by forking the chain just before the transaction, then reruns it locally, providing a detailed trace of all external calls, errors, gas usage, and even delegate calls, which helps identify proxies. It’s great for pinpointing issues like gas shortages or specific error causes, avoiding vague “reverted without reason” messages. I often use it when working with Hardhat, as its traces are more detailed than Hardhat’s. With the `--debug` flag, it opens an interactive EVM debugger, letting you step through the transaction opcode by opcode for in-depth analysis. Even without the debug flag, it helps resolve issues in about four out of five cases.

Next is Anvil, which is essentially a faster version of Hardhat’s node. It runs a local node for testing, providing unlimited ETH and supporting features like forking mainnet at a specific block number. Its functionality mirrors Hardhat’s node or Truffle’s Ganache but is significantly faster. Since the RPC interface is the same, you can use Anvil interchangeably with these tools, speeding up test execution or CI pipelines.

The final tool before we focus on Forge is Chisel. Honestly, I hadn’t used Chisel much until preparing for this talk, and it’s often overlooked in Foundry discussions. Chisel is a REPL (Read-Eval-Print Loop) for Solidity, similar to typing `python` or `node` in your terminal. It allows interactive Solidity programming, where you can write commands, see variable values, and test code snippets. You have access to nearly the full Solidity syntax, can call other contracts, and specify a block number to execute code as if it’s a transaction at that block. I see potential for iterative development or debugging with Chisel, though I haven’t integrated it into my daily workflow yet.

Before diving into Forge, any questions about these tools or Foundry in general? I see a few in the chat.

Peter: Let’s address Alebenga’s question about `cast run`: Can it be used for integration tests?

Christian: `Cast run` reruns an existing transaction that’s already been included in the blockchain, so it’s primarily for debugging specific transactions. For integration tests, we’ll cover Forge later, which handles both unit and integration testing. If you have an integration test failing on a local node, you can use `cast run` to debug it and identify where it went wrong. The `0x1cff` in the example is the transaction hash.

Peter: Dev asked about decoding function details for unverified contracts. You mentioned it needs verification, but is there a way around that?

Christian: Good catch! I forgot to mention that Cast can decode functions even for unverified contracts in many cases. It first checks if the contract is verified on Etherscan or another explorer. If not, it falls back to the Four Byte Registry, an online repository of function selectors, to decode the function. It won’t work for all unverified contracts, but it covers many cases, which is really cool.

Peter: Any other questions? Looks like there’s a comment, but no more questions. Go ahead, Christian.

Christian: Great, let’s move to Forge, the core tool of Foundry, often used interchangeably with the term Foundry itself. Forge handles testing, deployment, contract compilation, and project management, similar to Hardhat but with key differences. Everything is written in Solidity—tests, scripts, and usually contracts (though Vyper is supported). This eliminates context-switching, reduces boilerplate code, and makes it very fast. Forge also offers detailed error traces, like those in `cast run`, and advanced testing features like fuzzing and invariant testing, which we’ll explore.

To start, use `forge init` to create a template project with an example contract (a standard counter), example tests, an example script, and a configuration file. All files end in `.sol` since they’re in Solidity. The configuration file has sensible defaults but lets you customize the RPC URL, block number, compiler version, and more. Dependencies are managed via Git submodules, not npm, allowing you to install any Git-based repository with `forge install <owner/repo>`.

Here’s a simple test example, slightly adjusted from the template. Tests are written as Solidity contracts inheriting from a `Test` contract provided by Forge, giving access to assertion functions and testing tools. A `setUp` function runs before each test, similar to `beforeEach` in JavaScript. Any public function starting with `test` is recognized as a test. In this example, we increment the counter and assert the number is one. Run tests with `forge test`, which supports various parameters like regex to run specific tests, block numbers, or entering the debugger on failure. Verbosity levels (e.g., `-vvv`) control trace detail, and tests are blazing fast—794 microseconds for a simple test, scaling well for larger suites.

Any questions on setting up Forge, initializing projects, or running basic tests?

Peter: Looks clear. Let’s proceed.

Christian: In real-world tests, you often need more than basic assertions, like checking for reversions (e.g., only the owner can call a function). Foundry makes this easy. You can name a test `testFail`, and Forge expects a reversion for it to pass. A better approach is `vm.expectRevert`, which checks for a specific reversion in the next call. For example, we test for an arithmetic underflow in a decrement function using a standard error library for compiler-level errors. For custom errors, you’d specify the error string.

This introduces “cheat codes,” Foundry’s extensions to Solidity for testing. Cheat codes let you control the message sender, block number, timestamp, check reversions, events, interact with the file system, environment variables, CLI commands, and more. If you think something’s impossible in Foundry, there’s likely a cheat code for it.

Another useful cheat code is `vm.expectEmit`, which tests event emissions. It’s a bit more complex—you define the event in your test, specify which parameters to check (up to three indexed parameters and the rest as data), emit the expected event, and call the function. Foundry verifies the event matches. It’s the most intricate cheat code but manageable.

Another example is `vm.prank`, which impersonates an account for the next call. In a test for access control, we use `vm.expectRevert` and `vm.prank` to call a function from the zero address, expecting a reversion. However, cheat codes require careful use. In a flawed example, using `vm.prank` with `counter.number()` followed by `setNumber` fails because only the next call (`number`) uses the impersonated address, not `setNumber`. Using `vm.startPrank` and `vm.stopPrank` impersonates all calls in between, but even this can fail if `vm.expectRevert` targets the wrong call. A corrected version factors out the `number` call or reuses `vm.prank` correctly.

For debugging, Foundry supports `console.log` via a `console.sol` library. You import it in your contract and log messages, which appear in test output. It’s strictly typed, so you need specific log functions for different types, but it’s familiar and effective.

That covers basic testing, replicating much of what you’d do in other toolkits. Any questions before we move to advanced testing?

Peter: There’s a question from someone about getting off-chain, non-Solidity data for tests, like real-time API calls for integration tests (e.g., forking a network, calling 1inch or a bridge, and building transaction call data).

Christian: In Foundry, this is a bit hackier than in JavaScript-based libraries. Cheat codes let you run arbitrary CLI commands and read JSON files from the file system. You could run a `curl` command to call an API, save the response to a file, and use a cheat code to read specific JSON parameters. Since Solidity is strictly typed, variables must match Solidity types, which can be limiting. For aggregator APIs returning call data, this workaround should work, but it’s less seamless than JavaScript.

Peter: Great question. Any others? Alright, let’s move on.

Christian: Now, let’s cover advanced testing: fuzzing and invariant testing, which aren’t standard in Hardhat but come built-in with Foundry. Fuzzing runs a test with randomized inputs. Add arguments to your test function, and Forge generates random values, running the test for each (e.g., thousands of iterations). If a test fails, it shows the failing input. In an example, we test `setNumber` with a subtraction, failing on zero due to underflow. Forge finds this quickly, running only 10 iterations, though you can configure more. It’s not fully random—it likely tests edge cases first—but it’s fast and provides great coverage.

Invariant testing is even more powerful. You define an invariant (e.g., “the counter’s number is always even”), and Forge tries random function calls, senders, and values to break it. In an example, Forge sets the number to zero, then one, breaking the invariant. It shows the call sequence and senders used. You can limit which functions or contracts Forge tests to optimize for specific scenarios, using a `FuzzSelector` struct to specify allowed functions. This is powerful for testing complex systems.

Any questions on fuzzing or invariant testing?

Peter: Everything’s clear. No quiz, right? Just kidding.

Christian: Haha, no quiz. Let’s move to scripting, an underrated Forge feature. Scripts are Solidity programs for submitting transactions, like deployments or configurations. Unlike tests, they interact with the blockchain. Forge simulates the entire script on a local EVM fork before broadcasting, ensuring no reverts or gas issues. If the simulation fails, nothing is broadcast, preventing partial script failures. Forge logs transactions and call data for review.

In an example script, we deploy a counter contract and call `setNumber`. Scripts inherit from a `Script` contract, and the main function is named `run`. Transactions to be broadcast are wrapped in `startBroadcast` and `stopBroadcast`. You can include test-like assertions in the simulation phase. Run scripts with `forge script`, adding a `--broadcast` flag to execute transactions. Forge simulates first, estimates gas, broadcasts transactions one by one, and handles nonces well, avoiding common issues.

This was an appetizer for Foundry’s capabilities. The Foundry Book (available online) is the canonical resource, with tutorials and documentation. The Smart Contract Programmer’s Foundry playlist on YouTube offers bite-sized videos. For Hardhat users, a Hardhat-Foundry template repo lets you use both tools together with some configuration. That concludes my talk. Any questions?

Peter: That was awesome, Christian. One question: Is there interest in static analysis with Forge, like beyond invariant testing?

Christian: Forge has a linter (I think it’s `forge fmt` or similar) for formatting, syntax, and some best practices, but I’m unsure about deeper static analysis. There’s also work on formal verification, analyzing all possible program states, but I don’t think it’s implemented yet. It’s something to check on their GitHub.

Peter: Yeah, tools like Slither can be unreliable. Another question: For `forge script`, you use a private key in an environment variable. For high-stakes contracts, you’d want a Hardware Security Module (HSM) or AWS Key Manager. Any support for that?

Christian: I haven’t tried it, but there might be a pull request or issue for HSM/AWS integration. It’s a valid concern for secure deployments, but I don’t know of direct support yet.

Peter: Devendra asked about extending Foundry to non-EVM chains.

Christian: I haven’t seen plans for that. Foundry uses `revm`, a Rust EVM implementation, for its speed. Supporting non-EVM chains would likely require a major rewrite, but check their Telegram or GitHub for updates. Given EVM’s momentum, non-EVM support might not be a priority.

Peter: Thanks, Christian, that was amazing. The merch store is open, shipping globally with manufacturing in Australia, the US, and Europe for reasonable costs. Next week, Clemens from ConsenSys will discuss AI and Web3, and I’ll cover Immutable’s Passport wallet and zkEVM. In two weeks, I’ll share ERC-20 bridge improvements for rollups and sidechains. Tim Beiko from Ethereum Foundation will talk about Ethereum governance, and we’ll end the year with an interactive celebrity interview challenge—bring your IDE! Recordings are on YouTube, and join our Slack for live Q&A. Example code is in the repo. Thanks again, Christian, for an awesome talk!

Christian: Thanks for having me! The merch store ships globally, right?

Peter: Yes, globally, with local manufacturing to keep costs and delivery times low. Thanks, everyone, have a great day!

## Links

- [Solidity Development with Foundry: Cast, Anvil, Chisel, and Forge](https://www.youtube.com/watch?v=K83Y9NMSBVo)
