# 📑 Assignments M3

## Role-Based Rewards Pool

You will create a two-contract system that turns Ether donations into reward tokens and secures every action with **OpenZeppelin AccessControl**

**Actors & required roles**

| Role constant | Contracts where it exists | Privileges |
| --- | --- | --- |
| DEFAULT\_ADMIN\_ROLE | CommunityToken, RewardsVault | Grants and revokes all other roles & can set foundation wallet. |
| MINTER\_ROLE | CommunityToken | Allowed to mint new reward tokens. |
| PAUSER\_ROLE | CommunityToken, RewardsVault | Can pause and unpause its contract. |
| TREASURER\_ROLE | RewardsVault | Can withdraw pooled ETH to the foundation wallet. |
| AUDITOR\_ROLE | RewardsVault (same value as PAUSER\_ROLE) | Serves as an alias for PAUSER\_ROLE, giving auditors pause authority without mint or admin power. |

**Key flow**

1. Anyone sends ETH to **RewardsVault.donate()**.
2. Vault mints **1 CommunityToken per 0.01 ETH** to the donor.
3. Treasurer can withdraw ETH (minus accumulated fee) to the foundation wallet.
4. Auditor or any pauser can freeze or unfreeze both contracts in an emergency.

*All permissions must be enforced solely with AccessControl (no Ownable)*

### Contracts to write ✍️

#### 1.1 CommunityToken 🪙

| ID | Behaviour |
| --- | --- |
| CT-1 | Inherit ERC20, ERC20Pausable, AccessControl. |
| CT-2 | Constructor (string name, string symbol, address admin)  • grants DEFAULT\_ADMIN\_ROLE and PAUSER\_ROLE to admin |
| CT-3 | Declare bytes32 public constant MINTER\_ROLE = keccak256(“MINTER\_ROLE”);. |
| CT-4 | mint(address to, uint256 amount) — onlyRole(MINTER\_ROLE). |
| CT-5 | burn(uint256 amount) — token holder may burn own balance. |
| CT-6 | pause() / unpause() — onlyRole(PAUSER\_ROLE). |

#### 1.2 RewardsVault 🎁

| ID | Behaviour |
| --- | --- |
| RV-1 | Inherit AccessControl, Pausable, ReentrancyGuard. |
| RV-2 | Constructor (CommunityToken token, address admin, address foundationWallet) • grants DEFAULT\_ADMIN\_ROLE & PAUSER\_ROLE to admin |
| RV-3 | Define role constants: TREASURER\_ROLE = keccak256(“TREASURER\_ROLE”); PAUSER\_ROLE = keccak256(“PAUSER\_ROLE”); AUDITOR\_ROLE = PAUSER\_ROLE; |
| RV-4 | Public constants: RATE = 1e18 / 0.01 ether; → 1 token per 0.01 ETH. |
| RV-5 | donate() payable nonReentrant → mints msg.value \* RATE / 1e18 tokens to sender; emits Donation(sender, value). |
| RV-6 | withdraw(uint256 amount) — onlyRole(TREASURER\_ROLE) nonReentrant; sends ETH to foundationWallet; emits Withdrawal(amount). |
| RV-7 | setFoundationWallet(address) — onlyRole(DEFAULT\_ADMIN\_ROLE); reverts on zero address. |
| RV-8 | pause() / unpause() — onlyRole(PAUSER\_ROLE) (or AUDITOR\_ROLE). |
| RV-9 | receive() and fallback both revert() to block accidental transfers. |
| RV-10 | Use low-level call for ETH transfer and custom errors for gas savings. |

### Unit-testing requirements

Use **Hardhat** *or* **Foundry**.

Provide **at least three** tests:

1. donate mints the right token amount and emits Donation.
2. withdraw works for TREASURER\_ROLE and reverts for others.
3. When pause() is active, both donate and withdraw revert.

Feel free to add more tests. (pause/unpause cycle, burn, etc.).
