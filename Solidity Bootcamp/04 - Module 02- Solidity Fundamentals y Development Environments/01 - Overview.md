# 🎯 Overview

## Module 2 – Solidity Fundamentals & Development Environments

### Learning Objectives

- Understand how function modifiers, error handling, and mappings enhance control flow and data management in Solidity
- Learn the differences between memory and storage, and how to effectively use structs and arrays for complex data structures
- Gain practical experience using Hardhat and Foundry for writing, testing, and debugging smart contracts efficiently

### Function Modifiers, Mappings, Error Handling

- [Array Remove An Element By Shifting](https://www.youtube.com/watch?v=szv2zJcy_Xs)
- [Array Remove An Element By Replacing Last](https://www.youtube.com/watch?v=8i4CChP99XQ)
- [Iterable Mapping](https://www.youtube.com/watch?v=YOjo_lvUhj8)
- [Call Other Contracts](https://www.youtube.com/watch?v=6aQErpWPLbk)
- [Interface](https://www.youtube.com/watch?v=tbjyc-VQaQo)
- [Call](https://www.youtube.com/watch?v=xIAs2S9aCKo)
- [Delegatecall](https://www.youtube.com/watch?v=uawCDnxFJ-0)
- [New](https://www.youtube.com/watch?v=J2Wp2SHq1Qo)
- [Library](https://www.youtube.com/watch?v=OH5mafV6jVE)
- [Keccak256 Hash Function](https://www.youtube.com/watch?v=wCD3fOlsGc4)
- [Verify Signature](https://www.youtube.com/watch?v=vYwYe-Gv_XI)
- [Access Control](https://www.youtube.com/watch?v=tfk25O-5Ppg)
- [Deleting Contracts](https://www.youtube.com/watch?v=ajCsPRl5S3Q)
- [Create2](https://www.youtube.com/watch?v=883-koWrsO4)
- [Multi Call](https://www.youtube.com/watch?v=PDR054Cy8qM)
- [Multi Delegatecall](https://www.youtube.com/watch?v=NkTWU6tc9WU)
- [ABI Decode](https://www.youtube.com/watch?v=LTh58SFEYqE)
- [Bitwise Operators](https://www.youtube.com/watch?v=i2o4TfSC9nA)
- [Most Significant Bit using Binary Search Code](https://www.youtube.com/watch?v=M6awK0lskR4)
- [Call Functions with Key Value Inputs](https://www.youtube.com/watch?v=Y6mMnIZ7AAo)
- [3 Ways to Encode Call Data](https://www.youtube.com/watch?v=70_2YHJvKIc)
- [Unchecked Math](https://www.youtube.com/watch?v=_pvup5lyC3Q)
- [Input and Output with Fallback](https://www.youtube.com/watch?v=hcQyRmFOmvA)

### Hardhat

- [How to Create a Hardhat Project Step by Step](https://www.youtube.com/watch?v=pKh_A0ecGgQ)
- [Master Hardhat in Minutes](https://www.youtube.com/watch?v=rxK3UXld8xY)
- [Testing Solidity Contracts with Hardhat](https://www.youtube.com/watch?v=uF-lA8dDE3o)

### Foundry

- [Intro to Foundry](https://www.youtube.com/watch?v=fNMfMxGxeag)
- [Solidity Development with Foundry](https://www.youtube.com/watch?v=K83Y9NMSBVo)

### Foundry Testing

- [Introduction | Testing with Foundry](https://www.youtube.com/watch?v=tgs5q-GJmg4)
- [How to Write Basic Tests](https://www.youtube.com/watch?v=HA0GWauMOsU)
- [Set Solidity Compiler Version](https://www.youtube.com/watch?v=bmOxtjzFcbk)
- [Remappings](https://www.youtube.com/watch?v=7DK75j8csTA)
- [Auto Format Code](https://www.youtube.com/watch?v=k55TIWUFLbQ)
- [Console Log](https://www.youtube.com/watch?v=pO3kfXCFLuE)
- [Authentication](https://www.youtube.com/watch?v=gYwO3Jbi4O4)
- [Error](https://www.youtube.com/watch?v=yY9lL4Jxkd8)
- [Event](https://www.youtube.com/watch?v=GYwKDSSpzjQ)
- [Time](https://www.youtube.com/watch?v=B_3Kax70sF4)
- [Send ETH](https://www.youtube.com/watch?v=GuwUC-Wy_B0)
- [Signature](https://www.youtube.com/watch?v=cs5IeYqviSQ)
- [Fork](https://www.youtube.com/watch?v=eKxJZgp9CTg)
- [Mint 1 Million DAI on Mainnet Fork](https://www.youtube.com/watch?v=I8mzJxMBzs0)
- [Fuzz](https://www.youtube.com/watch?v=6sMOeuqwk-U)
- [Invariant Testing – Part 1 (Open Testing)](https://www.youtube.com/watch?v=JtzBi67hgLI)
- [Invariant Testing – Part 2 (Handler Testing)](https://www.youtube.com/watch?v=RFOqce1rz7U)
- [Invariant Testing – Part 3 (Actor Management)](https://www.youtube.com/watch?v=kPx4K8kRvUQ)
- [Foreign Function Interface (FFI)](https://www.youtube.com/watch?v=DTyn5ShI2vQ)
- [Differential Test](https://www.youtube.com/watch?v=WhZQhxOG124)

## Timestamps for Module 02

**Hardhat**

- How to Create a Hardhat Project Step by Step – 20:40
- Master Hardhat in Minutes – 19:26
- Testing Solidity Contracts with Hardhat – 21:24

**Foundry**

- Intro to Foundry – 19:21
- Solidity Development with Foundry – 1:09:19
- Testing with Foundry – 2:23:00

**Total Time: 7 hours, 40 minutes, and 45 seconds**

## Assignment

**Deterministic Escrow Suite**

#### Build a tiny on-chain escrow platform.

Your factory contract lets anyone spin up individual escrow contracts at addresses that can be known in advance. Each escrow holds one deposit of Ether from a single payer (the depositor). The escrow releases the deposit to a single payee **only** when the depositor later signs an off-chain approval message. The factory skims a 1 % fee from every successful release and keeps a running balance of fees. If the deadline passes and no release happens, the depositor can pull funds back. Once the escrow is empty, anyone can self-destruct it to tidy the chain.

Students choose Hardhat or Foundry to code, deploy, and test:

- **EscrowFactory** produces deterministic addresses with CREATE2, records every escrow per depositor, and manages the fee pool.
- **SimpleEscrow** enforces the single-deposit, signature-based release, fee split, deadline reclaim, and safe teardown.

You will also write at least two unit tests:

- one that proves the predicted CREATE2 address matches the deployed one,
- and one that covers the full happy-path flow from funding to release with the correct fee split.

When you finish, you will have a self-contained repo that anyone can clone, run forge test **or** npx hardhat test, and see a deterministic, signature-protected escrow system working end-to-end.

*Anyone* calls the **factory** to spin up a personal escrow contract at a predictable address.

- The depositor sends Ether once.
- The payee claims the funds later by presenting a signed approval from the depositor.
- The factory skims a 1 % fee from every successful release.
- If the deadline passes first, the depositor can reclaim the money.
- When an escrow hits zero balance, anyone may self-destruct it to save storage.

Pick **Hardhat** *or* **Foundry**.

Code, deploy, and write at least two unit tests with your chosen tool.
