# Exercise 6 – Solving Damn Vulnerable DeFi: Unstoppable

**Table of contents:**

- **Exercise 6**
  - Setup
  - Context
  - Goals
  - Hints

## Setup

1. Clone the repo: `git clone https://github.com/Metana-Inc/damn-vulnerable-defi-echidna`
2. install the dependencies via `yarn install`.

## Context

The challenge is described here: <https://www.damnvulnerabledefi.xyz/challenges/1.html>, we assume that the reader is familiar with it.

## Goals

- Setup the testing environment with the right contracts and necessary balances.
- Analyze the before function in test/unstoppable/unstoppable.challenge.js to identify what initial setup needs to be done.
- Add a property to check whether `UnstoppableLender` can always provide flash loans.
- Create a `config.yaml` with the necessary configuration option(s).
- Once Echidna finds the bug, fix the issue, and re-try your property with Echidna.

Only the following contracts are relevant:

- `contracts/DamnValuableToken.sol`
- `contracts/unstoppable/UnstoppableLender.sol`
- `contracts/unstoppable/ReceiverUnstoppable.sol`

## Hints

We recommend to first try without reading the following hints. The hints are in the [`hints` branch](https://github.com/crytic/damn-vulnerable-defi-echidna/tree/hints).

- The invariant that we are looking for is “Flash loan can always be made”
- Read what is the [multi abi option](https://montyly.github.io/building-secure-contracts/program-analysis/echidna/basic/common-testing-approaches.html#external-testing)
- The `receiveTokens` callback function must be implemented
- A template is provided in [contracts/unstoppable/UnstoppableEchidna.sol](https://github.com/crytic/damn-vulnerable-defi-echidna/blob/hints/contracts/unstoppable/UnstoppableEchidna.sol)
- A config file is provided in [unstoppable.yaml](https://github.com/crytic/damn-vulnerable-defi-echidna/blob/hints/unstoppable.yaml)
