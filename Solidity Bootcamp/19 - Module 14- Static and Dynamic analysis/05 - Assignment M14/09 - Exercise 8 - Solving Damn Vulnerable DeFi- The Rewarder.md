# Exercise 8 – Solving Damn Vulnerable DeFi: The Rewarder

**Table of contents:**

- **Exercise 8**
  - Setup
  - Context
  - Goals
  - Hints

## Setup

1. Clone the repo: `git clone https://github.com/crytic/damn-vulnerable-defi-echidna`
2. install the dependencies via `yarn install`.

## Context

The challenge is described here: <https://www.damnvulnerabledefi.xyz/challenges/5.html>, we assume that the reader is familiar with it.

## Goals

- Setup the testing environment with the right contracts and necessary balances.
- Analyze the before function in `test/the-rewarder/the-rewarder.challenge.js` to identify what initial setup needs to be done.
- Add a property to check whether the attacker can get almost whole reward (let us say more than 99 %) from the `TheRewarderPool` contract.
- Create a `config.yaml` with the necessary configuration option(s).
- Once Echidna finds the bug, …. well, this time to fix the issue would mean to apply completely different reward logic as in this particular solution is rather naive implementation.

Only the following contracts are relevant:

- `contracts/the-rewarder/TheRewarderPool.sol`
- `contracts/the-rewarder/FlashLoanerPool.sol`

## Hints

We recommend to first try without reading the following hints. The hints are in the [`hints` branch](https://github.com/crytic/damn-vulnerable-defi-echidna/tree/hints).

- The invariant that we are looking for is “an attacker cannot get almost whole amount of rewards”
- Read what is the [multi abi option](https://montyly.github.io/building-secure-contracts/program-analysis/echidna/basic/common-testing-approaches.html#external-testing)
- A config file is provided in [the-rewarder.yaml](https://github.com/crytic/damn-vulnerable-defi-echidna/blob/solutions/the-rewarder.yaml)
