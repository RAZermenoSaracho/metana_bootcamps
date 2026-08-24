# 📑 Assignments M8

### Upgradeable ERC-1155 Game Economy

We are building an **upgradeable ERC-1155** that serves as a **complete game economy**. The system uses **one currency ID** (e.g., 0) as a **fungible token**. Material IDs (e.g., 1, 2, 3) are also **fungible tokens**, while crafted items are minted as **unique IDs with a supply of 1**.

Users participate in the economy by first **acquiring currency**, then **spending that currency to buy materials**, and finally **burning materials to craft a unique item**. This creates a fully on-chain game ecosystem with tracked value flows.

### 🔹 Metadata & Access Control

All tokens expose **metadata via uri**. Admin actions are **gated with AccessControl** to restrict sensitive operations. The contract uses **checks-effects-interactions** and **ReentrancyGuard** to protect all value flows, and includes **Pausable** functionality for emergency stops. Importantly, **unbounded loops** are avoided in all state-changing paths to ensure gas efficiency.

### 💰 Currency Acquisition

Users can obtain currency in a **simple, testable way**. The choice of model is flexible; examples include a **fixed-price ETH sale** or a **capped faucet per address**. The chosen model should be **documented** in the assignment.

### 🛒 Material Purchase

Material prices are paid in the **currency ID**. On purchase:

- The contract **takes or burns currency** from the caller.
- The chosen **material IDs are minted** to the user.

This ensures fair and predictable exchange of currency for materials.

### ⚒️ Crafting System

Crafting is governed by **recipes** that define required materials and amounts. When a user crafts:

- Required materials are **burned from the caller**.
- A **new unique token ID** is minted as the crafted item.
- The crafted ID is **never reused**.

All crafting events are logged via **clear events** for transparency and traceability.

### 🔄 Upgradeable Contracts

The system is **upgradeable** using **OpenZeppelin upgradeable libraries** and a **proxy** (UUPS or Transparent).

- **V1** supports:
  - Currency acquisition
  - Buying materials with the currency ID
  - Crafting one unique item from materials
  - Pausing
  - Role-gated admin actions
- **V2** introduces **behavior changes while preserving state**, including at least one new feature such as:
  - New recipe
  - Per-material price updates
  - Bulk purchase
  - Batch crafting

### ⚡ Deployment & Testing

- Deploy **V1**, run an end-to-end **buy → craft** workflow.
- Upgrade the proxy to **V2**, ensuring that **balances, recipes, and settings persist**, and the new feature works correctly.

A **small test suite** should verify:

- Paying currency **mints the correct materials**.
- Crafting **burns required materials** and mints a unique item.
- **Pause blocks** purchases and crafting.
- Upgrading to **V2 preserves state** and enables new features.

### 📄 Documentation

The assignment should include:

- **Proxy and implementation addresses** for V1 and V2
- **Chosen tools and commands**
- A short note on **upgrade design and security choices**

| ID | Behavior |
| --- | --- |
| GE-1 | Proxy & Upgradeability – Deploy behind a UUPS proxy with OZ upgradeable contracts. Initialize once, set roles (DEFAULT\_ADMIN\_ROLE, PAUSER\_ROLE, UPGRADER\_ROLE, GAME\_ADMIN\_ROLE), base URI, currency ID 0, material IDs starting from 1, and nextUniqueId for crafted items. |
| GE-2 | Pause Control – Role-gated pause/unpause. Paused state blocks currency buys, material purchases, and crafting. |
| GE-3 | Currency Acquisition – Document what currency acquisition model you’re using : fixed-price ETH sale or a capped faucet per address  • **fixed-price ETH sale** : buyCurrency(amount) mints fungible token ID 0 for ETH at fixed price per unit. Checks price match, not paused. ETH stays in contract. Emit CurrencyBought.  • **capped faucet per address** : Declare an immutable constant MAX\_USER\_CAP to limit mint of token ID 0 per address. buyCurrency(amount) mints fungible token ID 0 to the address limited by MAX\_USER\_CAP. Checks not paused. Emit FaucetClaimed. |
| GE-4 | Admin Withdrawals – withdraw(to, amount) lets admin pull ETH. Checks CEI pattern, not paused, non-zero address, enough balance. Uses nonReentrant. Emit Withdrawn. |
| GE-5 | Material Pricing & Storage – Maintain materialPrice[id] in currency units. Role-gated updates via setMaterialPrice. Emit MaterialPriceSet. |
| GE-6 | Material Purchase – buyMaterial(id, amount) burns caller’s currency, mints materials. Checks not paused, valid material, enough currency. Emit MaterialPurchased. |
| GE-7 | Craft Recipes – Store active recipe mapping material IDs → required quantities. Role-gated setRecipe sets one active recipe. Emit RecipeSet. |
| GE-8 | Crafting Items – craft() burns recipe materials from caller, mints new unique ID with supply 1, increments nextUniqueId. Checks not paused, has materials, unique ID unused. Emit Crafted. |
| GE-9 | Security & Best Practices – All value paths follow checks-effects-interactions, nonReentrant on ETH transfers, no tx.origin, no unbounded loops in state-changing code. |
| GE-10 | V2 Upgrade Feature – Add buyMaterialsBatch(ids[], amounts[]) to purchase multiple materials in one transaction with single currency burn. State persists from V1; tests confirm balances, recipes, and prices remain after upgrade. |

### CTF Challenges:

- Ethernaut 6
- Ethernaut 16
- Ethernaut 24
