# 📑 Assignments M4

### Mastering OpenZeppelin Token Standards

This sprint has three independent mini-projects so you touch **all** major token standards.

Pick **Hardhat** *or* **Foundry** (same tool for every part) and deliver the specified unit tests.

### Part A – ERC-20 VestingToken and VestingVault 🏦

You ship two contracts that cooperate:

1. **VestingToken** is a standard fungible token. It does nothing special on its own.
2. **VestingVault** is the brain.
   - The admin loads token amounts into time-locked “schedules” for any beneficiary.
   - Until a schedule’s cliff passes, the beneficiary can claim nothing.
   - After that, tokens unlock linearly (or all at once, depending on how you code the formula) until the schedule’s end date.
   - The beneficiary calls claim whenever they like; the vault mints the exact vested amount and transfers it to them.
   - No one can drain tokens early, and the vault never pushes tokens—users must pull.

A passing implementation shows tokens becoming available only when the calendar says so and prevents double-claims.

### Part B – ERC-721 MetaverseItem NFT collection 🎮

You deliver a single NFT contract:

- It can mint up to **10 000** unique tokens, each identified by an incrementing ID.
- The contract stores one IPFS base URI (e.g., ipfs://bafy…/).
  - tokenURI(42) returns ipfs://bafy…/42.json.
- A default 5 % royalty is embedded with ERC-2981, so any marketplace that reads the standard will route 5 % of every secondary sale back to the creator address.
- Only addresses holding the **MINTER\_ROLE** can mint; everyone else must buy or receive tokens off-chain.

A working deployment lets you change the base URI once, mint NFTs up to the cap, and see correct URIs and royalty info in tests.

### Part C – ERC-1155 LootCrate1155 📦

This single contract behaves like a video-game loot-crate shop:

- Token IDs 1 and 2 are fungible “Sword” and “Shield” items (supply-capped).
- IDs 3 and higher represent one-of-one cosmetic NFTs.
- Any user calls openCrate, pays **0.02 ETH** per crate, and receives a pseudorandom assortment of items—typically some swords/shields and, with lower probability, a cosmetic NFT.
- Because the contract is ERC-1155, all items are minted in one cheap batch.
- An authorised account holding **PAUSER\_ROLE** can halt crate openings instantly (and resume later).
- An authorised airdropper with **MINTER\_ROLE** can mint batches straight to players without payment when needed.

A correct solution mints the right mix when crates are opened, rejects under-payment, and blocks all minting while paused.

### Part A – VestingToken & VestingVault ⏳

| ID | Behaviour |
| --- | --- |
| A-1 | VestingToken inherits ERC20, ERC20Burnable, AccessControl. Constructor (name, symbol, admin) mints **100 M** tokens to admin and grants MINTER\_ROLE to a separate VestingVault. |
| A-2 | VestingVault inherits AccessControl, ReentrancyGuard. Constructor takes token address and admin. |
| A-3 | createSchedule(address beneficiary, uint64 cliff, uint64 duration, uint256 amount) – only admin; stores schedule struct (mapping by ID). |
| A-4 | claim(uint scheduleId) – beneficiary pulls tokens vested up to block.timestamp. Uses **pull over push** pattern, emits Claimed. |
| A-5 | Uses custom errors, immutable variables, and unchecked blocks (where safe) for gas savings. |

### Part B – IPFS-NFT Collection 🌐

| ID | Behaviour |
| --- | --- |
| B-1 | MetaverseItem inherits ERC721, ERC721Royalty, AccessControl, ERC721Enumerable. |
| B-2 | Constructor (name, symbol, baseURI, admin) sets default 5 % royalty and grants MINTER\_ROLE to admin. |
| B-3 | mint(address to) – only minter; tokenId auto-increments; max supply = **10 000**. |
| B-4 | setBaseURI(string) – only admin; stores IPFS base (e.g., ipfs://CID/). |
| B-5 | Override \_baseURI(); tokenURI = baseURI + tokenId + “.json”. |

### Part C – LootCrate1155 🧰

| ID | Behaviour |
| --- | --- |
| C-1 | Inherit ERC1155, AccessControl, Pausable. |
| C-2 | Token IDs: 1 = “Sword” (max 5000, fungible), 2 = “Shield” (max 5000), 3+ = unique cosmetic NFTs (non-fungible style, max supply 1). |
| C-3 | openCrate(uint count) payable mints random mix of IDs 1–3 based on keccak256(msg.sender, block.timestamp). Price: **0.02 ETH** each. |
| C-4 | mintBatch(address to, uint[] ids, uint[] amounts) – only MINTER\_ROLE for airdrops. |
| C-5 | pause() / unpause() – PAUSER\_ROLE. |

---

### Unit-testing requirements

Write tests in **test/**:

| Part | Minimum tests |
| --- | --- |
| A | Schedule releases correct amounts over time (use warp) Non-admin cannot create schedules |
| B | mint increments id & respects captokenURI returns expected IPFS link |
| C | openCrate reverts with wrong ETH pause blocks openCrate |

Feel free to add additional tests.
