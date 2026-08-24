# Exercise 7 – Solving Damn Vulnerable DeFi: Side Entrance

**Table of contents:**

- **Exercise 7**
  - Setup
  - Goals

## Setup

1. Clone the repo: `git clone https://github.com/Metana-Inc/damn-vulnerable-defi-echidna`
2. install the dependencies via `yarn install`.
3. Analyze the `before` function in `test/side-entrance/side-entrance.challenge.js` to identify what initial setup needs to be done.
4. Create a contract to be used for the property testing by Echidna.

No skeleton will be provided for this exercise.

## Goals

- Setup the testing environment with the right contracts and necessary balances.
- Add a property to check whether the balance of the `SideEntranceLenderPool` contract has changed.
- Create a `config.yaml` with the necessary configuration option(s).
- Once Echidna finds the bug, fix the issue, and re-try your property with Echidna.

Hint: It might help to start with doing a manual flashloan to get familiar with the workings of the target contract.
