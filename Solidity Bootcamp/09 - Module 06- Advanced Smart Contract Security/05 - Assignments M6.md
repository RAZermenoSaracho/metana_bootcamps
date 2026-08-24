# 📑 Assignments M6

Build a time-locked wallet that holds ETH for a beneficiary until a future time. Anyone can create a lock for a non-zero beneficiary with an amount and an unlock timestamp at least a minimum delay from now. Support many locks per beneficiary with unique ids.

Expose simple views to discover and inspect locks. Emit events for creation and payout. Reject direct ETH that bypasses lock creation.

### 💰 Claiming Funds

A beneficiary can claim a matured lock. Let them optionally choose a payout recipient at claim time. Enforce checks-effects-interactions. Update storage so a second payout can’t occur.

Transfer with a low-level call and verify success. Emit a payout event.

### ♻️ Reclaiming Funds

Add a reclaim path. If a lock stays unclaimed after a grace period past the unlock time, the original depositor may reclaim the funds. Apply the same protections.

Update state before transfer. Verify the call result.

### 📦 Batch Claim

Support batch claim. Let a beneficiary claim several matured locks in one transaction. Update state for each selected lock before any external transfer. Revert cleanly if any selected lock is ineligible.

Keep the batch gas-bounded by:

- Setting a fixed maximum number of IDs per call (e.g., 32).
- Doing constant work per ID only, no storage scans
- Update state for all IDs before making one transfer
- Revert if the cap is exceeded or any ID is invalid or ineligible.

### 🏦 Protocol Fee

Accrue a small protocol fee on each successful payout to an internal balance. Do not forward the fee inline. Provide a separate admin-only fee withdrawal path.

### 🛡️ Security & Controls

Protect that path the same way as other value-moving functions. Include pause controls that block creation, claims, reclaims, batch claims, and fee withdrawals while paused.

Use custom errors. Do not rely on tx.origin. Use OpenZeppelin where it helps, such as ReentrancyGuard and Pausable.

### 🧪 Testing & Verification

Your tests must prove that all value-moving paths are not reentrant: single claim, batch claim, reclaim, and fee withdrawal.

Run Foundry fuzz tests to check security.

|  |  |
| --- | --- |
| **ID** | **Behavior** |
| TLW-1 | Checks: validate non-zero beneficiary, amount > 0, unlock time ≥ min delay, not paused. Effects: create new lock struct, assign unique ID, index by beneficiary. Interactions: none. |
| TLW-2 | Reject any plain ETH transfers by reverting in receive() and fallback(). |
| TLW-3 | Return stored lock data for given ID if it exists. |
| TLW-4 | Return stored list of lock IDs for a beneficiary without scanning all storage. |
| TLW-5 | Checks: only beneficiary, lock exists, matured, not claimed/reclaimed, not paused. Effects: mark claimed, calculate and accrue fee. Interactions: low-level call to beneficiary, verify success. |
| TLW-6 | Same as TLW-5 but sends payout to specified non-zero recipient instead of beneficiary. |
| TLW-7 | Checks: only depositor, lock exists, matured + grace, not claimed/reclaimed, not paused. Effects: mark reclaimed. Interactions: low-level call to depositor for full amount, verify success. |
| TLW-8 | Checks: array length ≤ MAX\_BATCH, each lock valid, matured, belongs to caller, not claimed/reclaimed, not paused. Effects: mark all claimed, sum payouts and fees, accrue fee. Interactions: one low-level call to recipient for total payout, verify success. |
| TLW-9 | On successful single/batch payout, accrue protocol fee in internal balance; do not forward inline. |
| TLW-10 | Checks: admin only, valid to and amount ≤ accrued fees, not paused. Effects: deduct from protocol fees. Interactions: low-level call to recipient, verify success. |
| TLW-11 | Admin can pause/unpause; paused state blocks create, claim, reclaim, batch claim, and fee withdrawal. |
| TLW-12 | Apply nonReentrant to all ETH-moving functions and follow checks-effects-interactions; batch updates state for all IDs before any transfer. |

## Challenges

#### Ethernaut

[![ethernaut.openzeppelin.com](https://icons.duckduckgo.com/ip3/ethernaut.openzeppelin.com.ico) ethernaut.openzeppelin.com](https://ethernaut.openzeppelin.com/level/0)

- **Ethernaut 0** → *Hello Ethernaut*
- **Ethernaut 1** → *Fallback*
- **Ethernaut 3** → *Coin Flip*
- **Ethernaut 5** → *Token*
- **Ethernaut 11** → *Elevator*
- **Ethernaut 13** → *Gatekeeper One*
- **Ethernaut 20** → *Denial*
- **Ethernaut 21** → *Shop*

#### Secureum

- [MagicETH](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/1_MagicETH)
- [ModernETH](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/2_ModernWETH)
