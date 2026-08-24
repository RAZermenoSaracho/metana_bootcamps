# 🎯 Overview

## Module 05 – Frontend Integration & Web3 Development

## Learning Objectives

- Build responsive and modern frontends using **React** and **TailwindCSS**.
- Learn how to interact with smart contracts using **Viem** and **ethers.js**.
- Understand how to connect decentralized applications (dApps) with wallets such as **MetaMask** and **WalletConnect**.

## Lectures / Lessons

**Interacting with Smart Contracts using [Viem.sh](http://Viem.sh)**

- [**Learn how to use Viem**](https://www.youtube.com/watch?v=P9oUqVsHBkA)
- [**VIEM vs Ethers**](https://www.youtube.com/watch?v=MXU4FN3fkmY)
- [**Implementing ERC20 payment gateway with React, Wagmi and Viem**](https://www.youtube.com/watch?v=b8uYGc1rP7s)

**Connecting dApps with Wallets (MetaMask, WalletConnect)**

- [**Web3 Tutorial | Connect Wallet Tutorial | Web3 Connect Metamask Wallet**](https://www.youtube.com/watch?v=xKaJ-GGoikk)

**Frontend Development using React & TailwindCSS**

- [**React For Beginners**](https://www.youtube.com/watch?v=SqcY0GlETPk)
- [**Interact with Simple Contracts using React**](https://www.youtube.com/watch?v=3LFUgMqBSI8)
- [**Wagmi Hooks in React**](https://www.youtube.com/watch?v=VEm5hzGSvVg)
- [**Wallet Models in Web3 Frontend Development**](https://www.youtube.com/watch?v=Q5dv7qv08Fw)

## Timestamps for Module 05

**Interacting with Smart Contracts using [Viem.sh](http://Viem.sh) & ethers.js**

- Learn how to use Viem – 1:06:03
- VIEM vs Ethers – 5:05
- Implementing ERC20 payment gateway with React, Wagmi and Viem – 16:10

**Connecting dApps with Wallets (MetaMask, WalletConnect)**

- Web3 Tutorial | Connect Wallet Tutorial | Web3 Connect Metamask Wallet – 27:54

**Frontend Development using React & TailwindCSS**

- React For Beginners – 1:20:03
- Interact with Simple Contracts using React – 4:51
- Wagmi Hooks in React – 11:38
- Wallet Models in Web3 Frontend Development – 5:55

**Total Time – 3 hours, 38 minutes, and 23 seconds.**

## Assignment

Implement a complete **ERC20 token with capped supply**, a **token sale contract** that supports buying and selling tokens in exchange for ETH, and a **frontend DApp** that integrates these smart contracts on a testnet.

- **Part A (ERC20 Token):** Build a capped ERC20 token using OpenZeppelin libraries. The token should enforce a maximum supply via `_update()`, restrict minting to accounts with `MINTER_ROLE`, and manage permissions through `AccessControlDefaultAdminRules`.
- **Part B (Token Sale Contract):** Implement a token sale mechanism with `Ownable2Step` ownership for secure withdrawals. The contract must allow users to **buy tokens with ETH** (via explicit function calls or by sending ETH directly) and **sell tokens back for ETH** at a lower rate. It should handle reserves properly, prevent exceeding `MAX_SUPPLY`, and allow the owner to withdraw both tokens and ETH. The contract itself is granted the `MINTER_ROLE` in the ERC20 contract.
- **Part C (Frontend DApp):** Deploy the system to a public testnet and build a web-based DApp. Users can connect their wallet (with automatic network switching), view their native ETH balance and token balance, and interact with the token sale contract to **buy or sell tokens**. The frontend should disable buying if the max token supply is reached and disable selling if the contract lacks enough ETH liquidity.
