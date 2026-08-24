# 🎯 Overview

## Module 06 – Advanced Smart Contract Security

## Learning Objectives

- Understand how reentrancy attacks exploit smart contract logic and learn common patterns to prevent them through careful ordering of operations and state updates.
- Learn techniques to reduce gas usage through efficient data structures and operations, while exploring how MEV and private transactions affect transaction ordering and security.

## Lectures / Lessons

**Reentrancy Attacks**

- [Fallback](https://www.youtube.com/watch?v=CMVC6Tp9gq4)
- [REENTRANCY Attack everything that you need to know](https://www.youtube.com/watch?v=76So4jCysAQ)
- [3 Ways to Prevent ReEntrancy Attacks](https://www.youtube.com/watch?v=DRZogmD647U)
- [Fuzz & Invariant Tests | The secret to finding CRITICAL vulnerabilities faster](https://www.youtube.com/watch?v=juyY-CTolac)
- [Table Testing with Foundry](https://www.getfoundry.sh/forge/testing#table-testing)

**Gas Optimization**

- [What is Ethereum Gas](https://www.youtube.com/watch?v=Yh8cHUB-KoU)
- [EIP 1559 Explained](https://www.youtube.com/watch?v=w5-4QHLgZTU)
- [Gas Optimization in Solidity](https://www.youtube.com/watch?v=PYilP2bjtwc)
- [Simple Trick to Save Gas in Your Smart Contract](https://www.youtube.com/watch?v=l2OxNQcb8e8)
- [Gas Golf](https://www.youtube.com/watch?v=4r20M9Fr8lY)

**MEV and Private Transactions**

- [Maximum Extractable Value (MEV)](https://www.youtube.com/watch?v=eMuwGmOYjTE)

## Timestamps for Module 06

**Reentrancy Attacks & Guarding**

- Fallback – 5:21
- REENTRANCY Attack – 3:46
- Prevent ReEntrancy Attacks – 27:14

**Gas Optimization Strategies**

- What is Ethereum Gas – 13:02
- EIP 1559 Explained – 26:32
- Gas Optimization – 8:00
- Simple Trick to Save Gas in Your Smart Contract – 4:06
- Gas Golf – 6:26

**MEV and Private Transactions**

- Maximum Extractable Value (MEV) – 12:54

**Total Time: 1 hour, 32 minutes, and 37 seconds**

## Assignment

Build a time-locked wallet that holds ETH for a beneficiary until a future time. Anyone can create a lock for a non-zero beneficiary with an amount and an unlock timestamp at least a minimum delay from now. Support many locks per beneficiary with unique ids. Expose simple views to discover and inspect locks. Emit events for creation and payout. Reject direct ETH that bypasses lock creation.

A beneficiary can claim a matured lock. Let them optionally choose a payout recipient at claim time. Enforce checks-effects-interactions. Update storage so a second payout can’t occur. Transfer with a low-level call and verify success. Emit a payout event.

Add a reclaim path. If a lock stays unclaimed after a grace period past the unlock time, the original depositor may reclaim the funds. Apply the same protections. Update state before transfer. Verify the call result.

Support batch claim. Let a beneficiary claim several matured locks in one transaction. Update state for each selected lock before any external transfer. Revert cleanly if any selected lock is ineligible. Keep the batch gas-bounded by:

- Setting a fixed maximum number of IDs per call (e.g., 32).
- Doing constant work per ID only, no storage scans
- Update state for all IDs before making one transfer
- Revert if the cap is exceeded or any ID is invalid or ineligible.

Accrue a small protocol fee on each successful payout to an internal balance. Do not forward the fee inline. Provide a separate admin-only fee withdrawal path. Protect that path the same way as other value-moving functions. Include pause controls that block creation, claims, reclaims, batch claims, and fee withdrawals while paused. Use custom errors. Do not rely on tx.origin. Use OpenZeppelin where it helps, such as ReentrancyGuard and Pausable.

Your tests must prove that all value-moving paths are not reentrant: single claim, batch claim, reclaim, and fee withdrawal.

Run Foundry fuzz tests to check security.

## Challenges

**Ethernaut**

- Ethernaut 0
- Ethernaut 1
- Ethernaut 3
- Ethernaut 5
- Ethernaut 11
- Ethernaut 13
- Ethernaut 20
- Ethernaut 21

**Secureum**

- [MagicETH](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/1_MagicETH)
- [ModernETH](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/2_ModernWETH)
