# 📑 Assignments M1

Build **two contracts** and deploy them in Remix.

1. **CrowdfundHub** – create and manage crowdfunding projects.
2. **SimpleEnglishAuction** – a one-shot ascending-price auction for any ERC-721 *token ID* (interface only, no NFT code required).

Each contract must compile by itself; they do **not** interact.

**Contract A – CrowdfundHub**

Required behaviour:

| **ID** | **Behavior** |
| --- | --- |
| CF-1 | Anyone can open a project with a title, a funding **goal** (wei) and a **deadline** (Unix timestamp > now + 1 day). For testing, you may use a shorter deadline. Creator becomes *owner* of that project. |
| CF-2 | A project lives in one of three states: FUNDING, SUCCESS, FAIL. State is an enum. |
| CF-3 | Anyone can send ETH via contribute(uint projectId) while the project is FUNDING. The contract emits PledgeReceived(backer, projectId, amount). |
| CF-4 | After the deadline anyone may call finalise(uint projectId). If total pledged **≥ goal** change state to SUCCESS, else FAIL. Emit ProjectFinalised. |
| CF-5 | In SUCCESS state the project owner can withdraw(uint projectId) once. Use a *pull* pattern (send ETH to owner). |
| CF-6 | In FAIL state any backer can claim a 100 % refund of their contribution (self-service). |
| CF-7 | The hub charges a **2 % fee** on the total raised for successful projects and holds it. The contract owner may withdraw accumulated fees. |
| CF-8 | Protect external value transfers with **ReentrancyGuard**. |
| CF-9 | Provide a getProject(uint projectId) view that returns all public details without loops that could run O(n) on chain. |

*Recommended inheritance:* Ownable, ReentrancyGuard, Pausable.

**Contract B – SimpleEnglishAuction**

Required behaviour:

| **ID** | **Behaviour** |
| --- | --- |
| AU-1 | Constructor parameters: NFT contract address, tokenId, startPrice (wei), biddingPeriod (seconds). |
| AU-2 | States: STARTED, ENDED, CANCELLED. |
| AU-3 | Auction starts immediately; bids via bid() must exceed current highest by **≥ 10 %**. |
| AU-4 | Store each out-bidder’s amount in a withdrawal balance. Provide claimRefund() to pull their ETH. |
| AU-5 | Anyone can end the auction after the bidding period with end(). Transfer highest bid to the seller, emit AuctionEnded with winner & price, set state ENDED. |
| AU-6 | Seller can cancel early *only if* no bids have been placed, moving state to CANCELLED. |
| AU-7 | Use custom errors for common fails, e.g., BidTooLow() , AuctionNotEnded() . |
| AU-8 | Royalty/market-fee logic **not** required. |
| AU-9 | All external transfers protected with **ReentrancyGuard** pattern. |

**Grading Rubric**

| Criteria | Points | Assessment Notes |
| --- | --- | --- |
| Implementation — all specified requirements and behaviours are correctly built, deployed, and functional | 5 | Every ID in the module spec is addressed, runs without errors, and produces the expected output |
| Understanding — the student demonstrates genuine comprehension of the concepts behind the implementation | 3 | Logic is structured sensibly, naming is intentional, comments or explanations show the student knows why not just how |
| Code & Design Quality — clean, readable, and thoughtfully written with edge cases and best practices in mind | 2 | Consistent style, appropriate error handling, no obvious oversights or lazy shortcuts |
| Total | 10 |  |
