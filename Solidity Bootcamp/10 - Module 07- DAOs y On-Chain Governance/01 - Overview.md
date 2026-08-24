# 🎯 Overview

## Module 7 – DAOs & On-Chain Governance

### Learning Objectives

- Understand the mechanisms of Decentralized Autonomous Organizations (DAOs), including governance tokens, voting power, and proposal creation.

- Learn how to implement snapshot voting for off-chain governance decisions.

- Gain hands-on experience with OpenZeppelin Governor to build and manage DAO governance frameworks.

## Lectures / Lessons

- [What is a DAO?](https://www.youtube.com/watch?v=CQKoyMpFo_E)
- [What is a governance token?](https://www.youtube.com/watch?v=iUQhntRQVlo)
- [How to vote on snapshot](https://www.youtube.com/watch?v=sCmk8qkbFIc)
- OpenZeppelin Governance
  - [OpenZeppelin Governance API](https://docs.openzeppelin.com/contracts/5.x/api/governance)
  - [How OpenZeppelin governance contract works](https://docs.openzeppelin.com/contracts/5.x/governance)
- [How to build a on-chain DAO](https://www.youtube.com/watch?v=AhJtmUqhAqg)
- [Tally setup and technical documentation](https://docs.tally.xyz/set-up-and-technical-documentation/tally-architecture)
- [How does governance works in compound and Uniswap?](https://docs.uniswap.org/contracts/v2/reference/Governance/governance-reference)
- [Guide of building a web3 community](https://www.alchemy.com/overviews/the-definitive-guide-to-starting-a-dao)

## Timestamps for Module 07

- What is a DAO? – 1:20
- What is a governance token? – 2:30
- How to vote on snapshot – 2:55
- How to build a on-chain DAO – 1:26:31

**Total Time: 1 hour, 33 minutes, and 16 seconds**

## Assignments

- **Participation DAO Design:** An upgradeable DAO where voting power is earned through on-chain actions (e.g., funding treasury, time-boxed check-ins) instead of just token balances. Voting is tracked via a non-transferable, votes-compatible token with delegation, and capped per-user/epoch rules.
- **Governance & Execution:** Uses OpenZeppelin Governor + TimelockController with defined parameters (delay, period, quorum). Proposals go through snapshot, and approved ones execute real state changes on-chain (e.g., treasury payouts). Security best practices and full test coverage ensure reliability.
