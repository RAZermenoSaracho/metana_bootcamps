# 📑 Assignments M7

### Participation-Based DAO on Public Testnet

This assignment involves building a **DAO where voting power is earned through participation** rather than pure token balance. Users gain influence by performing on-chain actions rather than just holding tokens.

Voting power is recorded via an **OpenZeppelin votes-compatible token** (e.g., ERC20Votes or ERC721Votes). You may choose to make the token **non-transferable**, but **delegation must work** so that votes are counted correctly on **Snapshot ([https://snapshot.org](https://snapshot.org/#/explore))**. The rules for earning voting power, including **caps per epoch/user**, and how delegation works, should be clearly documented.

⚠️ **Note on Snapshot integration:** Registering an ENS name on Sepolia currently requires payment and is no longer free for testnet use. Because of this, the live Snapshot space/proposal step (DAO-9) is now **optional/bonus** do not let it block your submission. Your token and delegation logic must still be OZ Votes-compatible in principle (checkpoints, `delegate`/`delegateBySig`, standard events); you just won't be required to prove it via a live Snapshot proposal.

### 🔹 Earning Voting Power

Define at least **two on-chain actions** that grant voting power. Examples include:

- **Funding the DAO treasury**
- A **time-boxed “check-in”** that can be claimed once per epoch

Each action must:

- Emit clear **events for earning points**
- Respect **per-user and per-epoch caps**
- Be recorded reliably on-chain

### 🏛️ Governance Setup

Use **OpenZeppelin Governor** with a **TimelockController**. Configure parameters thoughtfully:

- **votingDelay**
- **votingPeriod**
- **proposalThreshold**
- **quorum**

Justify all numbers in your documentation. Point **Snapshot** at your Governor so proposals can be created and voted on externally. The Governor should:

- Read voting power from your **participation token**
- Be the **admin of a Treasury** owned by the timelock

### ⚡ Proposal Execution

Approved proposals must **execute on-chain** and change real state. For example:

- Releasing ETH from the **Treasury** to a grantee
- Updating a **parameter** in a managed contract

The **timelock** must be the executor/owner for any target modified by proposals. **Events** should be emitted for proposing and executing actions.

### 🛡️ Security & Best Practices

- Use **AccessControlDefaultAdminRules** or **Ownable2Step** where needed
- Avoid **tx.origin**
- Follow **checks-effects-interactions** for all value transfers
- Protect any payout path with **ReentrancyGuardTransient**
- Keep storage **simple**
- Avoid **unbounded loops** in state-changing paths

### 🧪 Testing & Verification

Unit tests should cover only your **Solidity contracts**. Use **Governor + Timelock locally** to simulate the full workflow:

1. **Propose**
2. **Vote**
3. **Queue**
4. **Execute**

Tests must prove that:

- Voting power comes from **participation**
- **Quorum is reached**
- A **real state change** occurs on the target contract

Snapshot is treated as an **optional, manual step** after tests (see note above):

- Deploy to a testnet
- (Optional/Bonus) Run one proposal end-to-end on Snapshot

Include in documentation:

- Contract addresses
- (Optional/Bonus) Snapshot proposal URL - omit if ENS registration was not accessible
- Execution transaction hash
- Before/after state check

| **ID** | **Behavior** |
| --- | --- |
| DAO-1 | Participation Token Setup – Deploy ERC20Votes or ERC721Votes token (optionally non-transferable) with checkpoints. Minting restricted to Earner contract. Expose delegate/delegateBySig for Snapshot compatibility. |
| DAO-2 | Timelock & Governor Setup – Deploy TimelockController (executor=open or specific) and Governor wired to the token. Configure votingDelay, votingPeriod, proposalThreshold, quorum. Governor is sole proposer of Timelock. |
| DAO-3 | **Treasury Deployment & Ownership** – Deploy Treasury to hold ETH/ERC20. Transfer ownership to Timelock. Only Timelock can execute payouts or param updates. Protect payout paths with nonReentrant.. |
| DAO-4 | **Earning Voting Power** – Users earn votes via funding the Treasury or epoch-based check-ins. Enforce per-epoch and per-user caps. Mark claimed states using bitmaps/counters. Checks paused state. Emit PointsEarned. |
| DAO-5 | **Delegation & Views** – Users delegate votes to self or others. Expose standard OZ events (DelegateChanged, DelegateVotesChanged). Provide constant-time views: currentEpoch(), claimedCheckIn(), remainingUserCap(), remainingGlobalCap(), and token snapshots. |
| DAO-6 | **Proposal Lifecycle** – Propose, vote, queue, and execute via Governor. Only eligible users with enough votes can propose. Voting uses snapshots; quorum enforced. Emit standard Governor events (ProposalCreated, VoteCast, ProposalQueued, ProposalExecuted). |
| DAO-7 | **Concrete Proposal Actions** – Timelock-only execution: Treasury releaseETH to grantee or managed-contract setParam. Checks: non-zero addresses, sufficient balances. Effects applied before interactions. Emit GrantReleased or ParamUpdated. |
| DAO-8 | **Security & Governance Parameters** – Use AccessControl for Earner/admin roles. CEI pattern on all value transfers. No tx.origin. Pause/unpause blocks earning and value-moving functions. Document and justify votingDelay, votingPeriod, proposalThreshold, quorum. |
| DAO-9 | **Snapshot Integration (Optional/Bonus)** – Ensure token is OZ Votes-compatible and delegation works. If you have access to an ENS name, publish Governor + Timelock addresses and network info to a Snapshot space and run one proposal end-to-end.  If not, document how you would wire it up (space config, voting strategy, delegation flow) this satisfies the requirement without needing an actual ENS registration. |
| DAO-10 | **Testing & Deployment** – Unit tests simulate earn points, delegation, proposal lifecycle, and state changes. After testnet deploy, record contract addresses, execution transaction hash, and before/after state snapshots. |

### CTF Challenges:

- **Secureum** – [crystalDAO](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/7_crystalDAO)
