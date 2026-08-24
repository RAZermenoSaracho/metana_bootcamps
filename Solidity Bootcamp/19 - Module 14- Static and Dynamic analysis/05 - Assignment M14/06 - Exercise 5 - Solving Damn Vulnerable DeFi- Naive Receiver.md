# Exercise 5 – Solving Damn Vulnerable DeFi: Naive Receiver

**Table of contents:**

- **Exercise 5**
  - Setup
  - Context
  - Goals
  - Hints

## Setup

1. Clone the repo: `git clone https://github.com/Metana-Inc/damn-vulnerable-defi-echidna`
2. install the dependencies via `yarn install`.

## Context

The challenge is described here: <https://www.damnvulnerabledefi.xyz/challenges/2.html>, we assume that the reader is familiar with it.

## Goals

- Setup the testing environment with the right contracts and necessary balances.
- Analyze the before function in test/naive-receiver/naive-receiver.challenge.js to identify what initial setup needs to be done.
- Add a property to check whether the balance of the `FlashLoanReceiver` contract can change.
- Create a `config.yaml` with the necessary configuration option(s).
- Once Echidna finds the bug, fix the issue, and re-try your property with Echidna.

Only the following contracts are relevant:

- `contracts/naive-receiver/FlashLoanReceiver.sol`
- `contracts/naive-receiver/NaiveReceiverLenderPool.sol`

## Hints

We recommend to first try without reading the following hints. The hints are in the [`hints` branch](https://github.com/crytic/damn-vulnerable-defi-echidna/tree/hints).

- Remember that sometimes you have to supply the test contract with Ether. Read more in [the Echidna wiki](https://github.com/crytic/echidna/wiki/Config) and look at [the default config setup](https://github.com/crytic/echidna/blob/master/tests/solidity/basic/default.yaml).
- The invariant that we are looking for is “the balance of the receiver contract can not decrease”
- Read what is the [multi abi option](https://montyly.github.io/building-secure-contracts/program-analysis/echidna/basic/common-testing-approaches.html#external-testing)
- A template is provided in [contracts/naive-receiver/NaiveReceiverEchidna.sol](https://github.com/crytic/damn-vulnerable-defi-echidna/blob/hints/contracts/naive-receiver/NaiveReceiverEchidna.sol)
- A config file is provided in [naivereceiver.yaml](https://github.com/crytic/damn-vulnerable-defi-echidna/blob/hints/naivereceiver.yaml)
