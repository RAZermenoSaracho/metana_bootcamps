# Ethereum Protocol by Vitalik Buterin

[Video: DEVCON1: Understanding the Ethereum Blockchain Protocol - Vitalik Buterin](https://www.youtube.com/watch?v=gjwr-7PgpN8)

Transcript for the AI

Welcome, everyone, to the third day of our conference, *Deep Dive into Ethereum Protocols*. We began with an excellent presentation from Alex, who discussed the foundational protocol on which other Ethereum protocols are built. Naturally, it makes sense to follow that with a presentation focused on the Ethereum protocol itself.

The concept of Ethereum first emerged around late 2013, during a period when enthusiasm for Bitcoin was peaking. Blockchain technology was gaining attention not just for digital currency but for broader applications such as asset issuance, crowdfunding, domain registration, prediction markets, IoT, and more. However, back then, most blockchain protocols were built for a single use case—Bitcoin for currency, Namecoin for domain registration, and Primecoin for scientific computing. These were rigid, single-purpose tools.

Later, second-generation protocols emerged, offering multiple hardcoded transaction types for specific applications like binary options or betting. Some of these protocols had 50+ transaction types, and whenever a new idea emerged, the protocol maintainers had to add a new type. This approach quickly proved unsustainable and inflexible.

Ethereum addressed this with a radically different approach: instead of building a protocol for specific use cases, it created a general-purpose platform—akin to a smartphone OS—where developers could build decentralized applications (dApps) on top. This meant Ethereum didn’t have to change each time a new application idea came up. Instead, users could deploy smart contracts—autonomous programs stored on-chain—using a built-in, Turing-complete scripting language.

Ethereum defines two types of accounts: externally owned accounts (EOAs), controlled by private keys, and contract accounts, controlled by code. Both account types have equal privileges. Developers can write contracts in high-level languages (like Solidity or Serpent), compile them into EVM bytecode, and deploy them to the blockchain. Once deployed, these contracts live at a unique address and can be interacted with through transactions.

A good example is a decentralized DNS system where users can register `.eth` domains. A simple contract can map domain names to owner addresses and associated IPs. Users interact with this contract by calling methods like `register()` or `setIp()` through transactions. All state changes (like domain ownership or IP mapping) are persistently stored in the contract’s storage.

Ethereum’s global state is represented as a key-value mapping of addresses to account objects. EOAs store only a nonce and balance, while contract accounts also store code and a storage trie. All of this is replicated and maintained by every full node in the network. Every node executes every transaction and maintains the full state—ensuring consistency and decentralization.

To prevent abuse of its Turing-complete nature (e.g., infinite loops), Ethereum introduces **gas**—a fee for computation and storage usage. Each transaction must specify a gas price (the fee per unit of computation) and a gas limit (the maximum computation allowed). If a transaction exceeds its gas limit, it fails and reverts state changes—but still pays for the consumed gas. Gas also incentivizes responsible use of the network’s resources and plays a role similar to Bitcoin’s block size limit, with miners voting to adjust the gas limit over time.

Ethereum transactions include several fields: `nonce` (to prevent replay attacks), `gasPrice`, `gasLimit`, `to` (destination address), `value` (amount of Ether), `data` (contract input), and a digital signature (`v, r, s`). When contracts are called, this `data` field encodes the function signature and arguments using the Ethereum ABI, which specifies a standardized way of encoding function calls and parameters.

Each transaction produces a **receipt**, containing the post-execution state root, the cumulative gas used, and **logs**. Logs are event records created by contracts that are cheap, append-only, and not accessible by other contracts. They are mainly used by light clients and event listeners to track contract activity, such as domain registrations or token transfers.

At the heart of Ethereum lies the **Ethereum Virtual Machine (EVM)**—a stack-based virtual machine capable of executing smart contracts. It provides access to memory, persistent storage, and environment variables like block timestamp, block number, and sender address. Contracts can also call other contracts, enabling composable, modular logic.

While developers write in high-level languages like Solidity or Serpent, all contracts are compiled into EVM bytecode. Ethereum also uses Recursive Length Prefix (RLP) encoding to serialize data structures across blocks, transactions, and state.

Ethereum introduced a novel **proof-of-work** algorithm called **Ethash**, designed to be ASIC-resistant and GPU-friendly. Ethash is **memory-hard**, meaning miners must perform heavy memory operations rather than pure computation, thereby discouraging centralized ASIC mining farms. Miners must generate a large dataset and sample from it to find valid blocks, while verifiers need only a smaller cache—making mining expensive but verification lightweight.

Ethereum’s block time is ~17 seconds, compared to Bitcoin’s 10 minutes. Faster blocks increase the likelihood of forks, where two miners produce blocks simultaneously. To mitigate centralization risks and improve security, Ethereum introduces **uncles**—blocks that don’t make it to the main chain but are still rewarded if they were valid and timely. This reduces the incentive for miners to form large, centralized pools.

Another critical data structure in Ethereum is the **Merkle Patricia Trie**. It enables efficient and verifiable proof of any data (like account balances or contract state) without needing the full blockchain. Unlike Bitcoin, Ethereum uses Merkle trees not only for transactions but also for account state and storage, forming a layered structure where each component of the system is verifiably hashed and linked.

These trie structures allow **light clients**—devices that don’t store the full blockchain—to operate securely by verifying only the parts relevant to them using Merkle proofs. This is crucial for scalability and for enabling blockchain access on constrained devices like mobile phones or IoT hardware.

In summary, Ethereum’s protocol is a powerful, general-purpose platform that transforms the blockchain from a single-use system into a decentralized world computer. With features like smart contracts, gas metering, EVM execution, Merkle-Patricia state structures, and ASIC-resistant mining, Ethereum was designed to be flexible, secure, and future-proof for an expanding universe of decentralized applications.

## Links

- [DEVCON1: Understanding the Ethereum Blockchain Protocol - Vitalik Buterin](https://www.youtube.com/watch?v=gjwr-7PgpN8)
