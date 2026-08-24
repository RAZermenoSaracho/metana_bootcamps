# 📑 Assignments M2

### Deterministic Escrow Suite

#### Build a tiny on-chain escrow platform.

Your factory contract lets anyone spin up individual escrow contracts at addresses that can be known in advance. Each escrow holds one deposit of Ether from a single payer (the depositor). The escrow releases the deposit to a single payee **only** when the depositor later signs an off-chain approval message. The factory skims a 1 % fee from every successful release and keeps a running balance of fees. If the deadline passes and no release happens, the depositor can pull funds back. Once the escrow is empty, anyone can self-destruct it to tidy the chain.

Students can choose either **Hardhat or Foundry** for coding, deployment, and testing, and use **Sepolia Testnet or Polygon Amoy** as test networks.

You can obtain free **Sepolia ETH from the Metana faucet**: <https://faucet.metana.io>.

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

### Contracts to write ✍️

#### A. EscrowFactory 🏭

| ID | Behaviour |
| --- | --- |
| F-1 | Constructor stores feeRecipient and sets immutable feePercent = 1 (units: percent). |
| F-2 | createEscrow(depositor, payee, deadline, salt) deploys a new SimpleEscrow with **CREATE2** and emits EscrowCreated(escrowAddress). |
| F-3 | Provide predictAddress(depositor, payee, salt) that returns the same CREATE2 address without deploying. |
| F-4 | Map escrows[depositor] → address[] and return it with getEscrows(depositor). |
| F-5 | Owner can pause() and unpause() deployments (use Pausable). |
| F-6 | withdrawFees() lets owner pull accumulated fees to feeRecipient. |

Recommended OpenZeppelin mix-ins: Ownable, Pausable, ReentrancyGuard.

#### B. SimpleEscrow 💼

| ID | Behaviour |
| --- | --- |
| E-1 | Constructor args: (factory, depositor, payee, deadline, feePercent); mark as immutable where possible. |
| E-2 | fund() is payable, can be called **once** by depositor. Emit Funded(amount). |
| E-3 | release(amount, sig) sends (amount – fee) to payee if sig recovers depositor from keccak256(“RELEASE”, address(this), amount). Forward the fee to the factory, emit Released(payee, amountAfterFee). |
| E-4 | After deadline and if no release happened, reclaim() lets depositor pull all funds. |
| E-5 | Use nonReentrant on external functions that move Ether. |

Inline a private hashRelease() helper and an internal verify() that wraps ecrecover.

### Tests (minimum)

1. **Address test** – predictAddress() output matches the actual deployed escrow.
2. **Happy path test** – fund → signed release → check balances and 1 % fee.

Write more tests if you wish (deadline reclaim, bad signature, pause logic, etc.).

**Grading Rubric**

| Criteria | Points | Assessment Notes |
| --- | --- | --- |
| Implementation — all specified requirements and behaviours are correctly built, deployed, and functional | 5 | Every ID in the module spec is addressed, runs without errors, and produces the expected output |
| Understanding — the student demonstrates genuine comprehension of the concepts behind the implementation | 3 | Logic is structured sensibly, naming is intentional, comments or explanations show the student knows why not just how |
| Code & Design Quality — clean, readable, and thoughtfully written with edge cases and best practices in mind | 2 | Consistent style, appropriate error handling, no obvious oversights or lazy shortcuts |
| Total | 10 |  |
