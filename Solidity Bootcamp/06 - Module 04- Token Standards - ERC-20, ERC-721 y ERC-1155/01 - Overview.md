# 🎯 Overview

## Module 04 – Token Standards – ERC-20, ERC-721 & ERC-1155

## Learning Objectives

- Understand the key standards of ERC-20, ERC-721, and ERC-1155 and their roles in token development
- Learn to build secure and upgradeable token contracts using OpenZeppelin libraries
- Explore techniques for gas optimization in smart contract development, especially in token logic
- Get introduced to IPFS and how it’s used for decentralized file storage in blockchain applications

## Lessons

### Token Standards

- [ERC20](https://www.youtube.com/watch?v=gwn1rVDuGL0)
- [ERC721](https://www.youtube.com/watch?v=9PBq9HfBUDY)
- [ERC1155 Intro](https://www.youtube.com/watch?v=Ai7A-_umm08)
- [ERC1155](https://www.youtube.com/watch?v=C4i4CDGb9A0)

### Introduction to IPFS and Pinata

- [How to Persist NFT Data with IPFS](https://www.youtube.com/watch?v=SLfa1vUkCH0)
- [What is an IPFS Pinning Service](https://www.youtube.com/watch?v=98bg9Q3vqdU&t=13s)
- [What is an IPFS CID](https://www.youtube.com/watch?v=v5sVaJFUAA8&t=1s)
- [Why NFT Data Should Be Hosted on IPFS](https://www.youtube.com/watch?v=_SKFyuLBopY)
- [How Do You Upload to IPFS?](https://www.youtube.com/watch?v=zpJ3jQOlfdw&t=1s)

## Timestamps for Module 04

**Token Standards**

- ERC20 – 9:20
- ERC721 – 20:18
- ERC1155 Intro – 2:17
- ERC1155 – 20:17

****Introduction to IPFS and Pinata****

- How to Persist NFT Data with IPFS – 5:03
- What is an IPFS Pinning Service – 2:38
- What is an IPFS CID – 4:55
- Why NFT Data Should Be Hosted on IPFS – 2:02
- How Do You Upload to IPFS? – 2:29

**Total Time: 1 hours, 29 minutes, and 23 seconds**

## Assignment

### Mastering OpenZeppelin Token Standards

This sprint has three independent mini-projects so you touch **all** major token standards.

Pick **Hardhat** *or* **Foundry** (same tool for every part) and deliver the specified unit tests.

### Part A – ERC-20 VestingToken and VestingVault

You ship two contracts that cooperate:

1. **VestingToken** is a standard fungible token. It does nothing special on its own.
2. **VestingVault** is the brain.
   - The admin loads token amounts into time-locked “schedules” for any beneficiary.
   - Until a schedule’s cliff passes, the beneficiary can claim nothing.
   - After that, tokens unlock linearly (or all at once, depending on how you code the formula) until the schedule’s end date.
   - The beneficiary calls claim whenever they like; the vault mints the exact vested amount and transfers it to them.
   - No one can drain tokens early, and the vault never pushes tokens—users must pull.

A passing implementation shows tokens becoming available only when the calendar says so and prevents double-claims.

### Part B – ERC-721 MetaverseItem NFT collection

You deliver a single NFT contract:

- It can mint up to **10 000** unique tokens, each identified by an incrementing ID.
- The contract stores one IPFS base URI (e.g., ipfs://bafy…/).
  - tokenURI(42) returns ipfs://bafy…/42.json.
- A default 5 % royalty is embedded with ERC-2981, so any marketplace that reads the standard will route 5 % of every secondary sale back to the creator address.
- Only addresses holding the **MINTER\_ROLE** can mint; everyone else must buy or receive tokens off-chain.

A working deployment lets you change the base URI once, mint NFTs up to the cap, and see correct URIs and royalty info in tests.

### Part C – ERC-1155 LootCrate1155

This single contract behaves like a video-game loot-crate shop:

- Token IDs 1 and 2 are fungible “Sword” and “Shield” items (supply-capped).
- IDs 3 and higher represent one-of-one cosmetic NFTs.
- Any user calls openCrate, pays **0.02 ETH** per crate, and receives a pseudorandom assortment of items—typically some swords/shields and, with lower probability, a cosmetic NFT.
- Because the contract is ERC-1155, all items are minted in one cheap batch.
- An authorised account holding **PAUSER\_ROLE** can halt crate openings instantly (and resume later).
- An authorised airdropper with **MINTER\_ROLE** can mint batches straight to players without payment when needed.

A correct solution mints the right mix when crates are opened, rejects under-payment, and blocks all minting while paused.
