# 🎯 Overview

## Module 12 – Account abstraction, Gasless transaction and Meta transactions

## Learning Objectives

- Understand key EIPs (e.g., 155, 191, 712, 4337, 7702) and their roles in secure transactions, structured signing, and account abstraction.
- Learn to use advanced wallet features, gasless transfers, and smart contract wallets while managing security and usability trade-offs.

# Lectures / Lessons

**EIPs**

- [**EIP 155 : Simple Replay protection**](https://eips.ethereum.org/EIPS/eip-155)
- [**EIP 191 : Signed Data Standard**](https://eips.ethereum.org/EIPS/eip-191)
- [**EIP 712 : Typed structured data hashing and signing**](https://eips.ethereum.org/EIPS/eip-712)
- [**EIP 712 Explained**](https://www.youtube.com/watch?v=X-HVI9dFv94)
- [**EIP 7201: Namespaced Storage Layout**](https://eips.ethereum.org/EIPS/eip-7201)
- [**ERC20 Permit**](https://www.youtube.com/watch?v=rucZrL1nOO8)
- [**EIP 4337**](https://eips.ethereum.org/EIPS/eip-4337)
- [**EIP-4337 (Account Abstraction)**](https://www.youtube.com/watch?v=YXwKB0htrwM)
- [**EIP-4337 (Account Abstraction) using Alt Mempool**](https://www.youtube.com/watch?v=CgXzDuN5Xqc)
- [**What is Account Abstraction?**](https://www.youtube.com/watch?v=PZ8svp68NXM)
- [**Account Abstraction – Playlist**](https://youtube.com/playlist?list=PLMj8NvODurfE9yPZ2beXSjuEgVtVcY1a6&si=ruhmMPdYB7O4PZz6)
- [**EIP 2771**](https://eips.ethereum.org/EIPS/eip-2771)
- [**EIP 2770**](https://eips.ethereum.org/EIPS/eip-2770)
- [**EIP 3005**](https://eips.ethereum.org/EIPS/eip-3005)
- [**EIP 3009**](https://eips.ethereum.org/EIPS/eip-3009)
- [**Gas-less Token Transfer**](https://www.youtube.com/watch?v=YJN7MMllK8M)
- [**EIP 7701**](https://eips.ethereum.org/EIPS/eip-7701)
- [**EIP 7702**](https://www.youtube.com/watch?v=_k5fKlKBWV4)
- [**EIP 7702 – Doc**](https://getfoundry.sh/reference/cheatcodes/sign-delegation)
- [**EIP 7702 Vulnerability**](https://www.youtube.com/watch?v=0uy4nd8vIe8)

## Timestamp

- EIP 712 Explained – 8:01
- ERC20 Permit – 4:37
- EIP-4337 (Account Abstraction) – 1:15:55
- EIP-4337 (Account Abstraction) using Alt Mempool – 1:06:35
- What is Account Abstraction? ERC-4337- 10:13
- ccount Abstraction – 7:50
- Gas-less Token Transfer – 9:33
- EIP 7702 – 21:40
- EIP 7702 Vulnerability – 8:36

**Total Time – 3 hours and 33 minutes**

### Assignment

- **Part A (EIP-7702):** Build and deploy a batch execution contract that can perform multiple actions (ETH transfer, ERC20 transfer, and Counter increments) in one transaction, write a viem script to execute them, and verify with testnet + Foundry tests.
- **Part B (ERC-4337):** Extend the contract with account abstraction (IAccount, IAccountExecute) and a MockEntryPoint to handle user operations, then test the same three actions via Foundry.
