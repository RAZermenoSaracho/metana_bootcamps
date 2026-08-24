# 🎯 Overview

## Module 3: Smart Contract Security & Access Control

## Learning Objectives

- Understand key security risks in Solidity and how to prevent them.
- Apply best practices and libraries like OpenZeppelin to write secure and access-controlled smart contracts.

## Lectures

#### Solidity Vulnerabilities

- [Reentrancy](https://www.youtube.com/watch?v=4Mm3BCyHtDY)
- [Transient Storage](https://www.youtube.com/watch?v=0-hiB5I39Mk)
- [Arithmetic Overflow and Underflow](https://www.youtube.com/watch?v=zqHb-ipbmIo)
- [Phishing with tx.origin](https://www.youtube.com/watch?v=mk4wDlVB4ro)
- [Unsafe Delegatecall](https://www.youtube.com/watch?v=bqn-HzRclps)
- [Insecure Source of Randomness](https://www.youtube.com/watch?v=8FF3IBTMeK0)
- [Front Running](https://www.youtube.com/watch?v=MN55R440twQ)

#### OpenZeppelin’s Ownable & Access Control

- [Ownable](https://www.youtube.com/watch?v=sxNi2t1uNMk)
- [Ownable2Step](https://www.youtube.com/watch?v=wE7JhSZvL3I)
- [AccessControl](https://www.youtube.com/watch?v=J4mhJUTfgNs)

## Timestamps for Module 03

**Solidity Vulnerabilities**

- Reentrancy – 15:32
- Transient Storage – 11:26
- Arithmetic Overflow and Underflow – 11:38
- Phishing with tx.origin – 7:21
- Unsafe Delegatecall – 9:04
- Insecure Source of Randomness – 8:34
- Front Running – 5:38

**OpenZeppelin’s Ownable & Access Control**

- Ownable – 7:35
- Ownable2Step – 5:37
- AccessControl – 18:23

**Total Time: 1 hours, 29 minutes, and 23 seconds**

## Assignment

### Role-Based Rewards Pool

You will create a two-contract system that turns Ether donations into reward tokens and secures every action with **OpenZeppelin AccessControl**

**Key flow**

1. Anyone sends ETH to **RewardsVault.donate()**.
2. Vault mints **1 CommunityToken per 0.01 ETH** to the donor.
3. Treasurer can withdraw ETH (minus accumulated fee) to the foundation wallet.
4. Auditor or any pauser can freeze or unfreeze both contracts in an emergency.

*All permissions must be enforced solely with AccessControl (no Ownable)*

**Unit-testing requirements**

Use **Hardhat** *or* **Foundry**.

Provide **at least three** tests:

1. donate mints the right token amount and emits Donation.
2. withdraw works for TREASURER\_ROLE and reverts for others.
3. When pause() is active, both donate and withdraw revert.

Feel free to add more tests. (pause/unpause cycle, burn, etc.).
