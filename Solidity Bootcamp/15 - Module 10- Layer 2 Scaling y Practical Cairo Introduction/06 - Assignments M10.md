# 📑 Assignments M10

- Deploy an ERC-20 token on Optimism or Arbitrum.
- Write a basic Cairo contract for a simple storage system.
- Extends Learning: Focuses on Layer 2 deployment and interoperability.

#### Part A : Deploy ERC20 token on zkSync

| ID | Behaviour |
| --- | --- |
| L2-1 | Add the transaction URL to the document about acquiring gas from ethereum testnet/mainnet to zksync testnet/mainnet |
| L2-2 | Develop an ERC20 token contract by inheriting OZ’s ERC20 contract. |
| L2-3 | Pass the name and symbol of token to the constructor arguments upon deployment |
| L2-4 | Deploy and verify the contract on <https://sepolia-era.zksync.network/> (if testnet) or <https://era.zksync.network/> ( if mainnet). Add the deployed contract links to the doc. |

#### Part B : Write a basic Cairo contract for a simple storage system.

| ID | Behaviour |
| --- | --- |
| L2-5 | Write a basic Cairo 1.0 smart contract implementing a simple storage system (set and get a felt252 value). |
| L2-6 | Use appropriate decorators like #[storage], #[external], and #[view] in the contract. |
| L2-7 | Add comments explaining each function and storage item for readability. |
| L2-8 | Compile and deploy the contract using starkli or sncast to a Starknet testnet. |
| L2-9 | Add the deployed contract address and transaction hash to the documentation. |
| L2-10 | Write unit tests using snforge to test the set and get functions. |

#### Part C : Send messages between two chains using layer zero protocol

Create an omnichain Application (OApp) to send messages between two chains. You can refer this [sample](https://github.com/LayerZero-Labs/devtools/blob/main/examples/oapp/README.md)

| ID | Behaviour |
| --- | --- |
| L2-11 | Set up the project by installing LayerZero devtools (or cloning the OApp example) and importing OApp.sol. |
| L2-12 | Implement sendMessage using \_lzSend and \_lzReceive to handle sending and receiving cross-chain messages. |
| L2-13 | Configure trusted peers by mapping contract addresses across chains to ensure only valid sources are accepted. |
| L2-14 | Use quoteSend to estimate messaging fees and apply execution options (\_options) like gas limits or native drops. |
| L2-15 | Deploy the OApp contract on two EVM testnets (e.g., Optimism [Sepolia Testnet] + Arbitrum [Sepolia Testnet]) and connect to LayerZero endpoints/libraries. |
| L2-16 | Write and run Foundry/Hardhat tests with TestHelper, then document contract addresses, tx hashes, and test results. |
