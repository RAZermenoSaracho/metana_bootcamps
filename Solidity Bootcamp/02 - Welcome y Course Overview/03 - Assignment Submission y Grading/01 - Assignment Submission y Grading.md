# Assignment Submission & Grading

This page explains everything you need to know before submitting any assignment in this bootcamp - what to submit, how your work will be evaluated, and what separates a passing submission from an excellent one.

## What You Must Submit

Every assignment submission is a **Pull Request (PR)** to the designated repository. Your PR must include:

### 1. Solidity Contract(s)

Your contract code must be fully documented using **NatSpec** (Ethereum's native documentation standard). At minimum, every function must have a complete NatSpec block - `@notice`, `@dev`, `@param`, and `@return` where applicable.

→ NatSpec reference: <https://docs.soliditylang.org/en/latest/natspec-format.html>

### 2. Assignment Requirement Tags in Comments

Every assignment spec comes with numbered requirement IDs (e.g. `CF-01`, `CF-02`). You must reference these IDs directly in your code, at the exact point where each requirement is fulfilled.

**Example:**

solidity

```
// CF-01: Transfer function must revert if sender balance is insufficient
function transfer(address to, uint256 amount) external {
    require(balances[msg.sender] >= amount, "Insufficient balance");
    ...
}
```

This makes it unambiguous to instructors where and how you've addressed each requirement.

3. [README.md](http://README.md)

A written document (Markdown) included in your PR with the following three sections:

**What I Learned** Summarise the key concepts or tools this assignment helped you understand more deeply.

**Problems & Solutions** Describe at least one problem you ran into and how you resolved it. This can be a bug, a conceptual confusion, a tooling issue - anything real.

**Testing Approach** Explain how you tested your contract: what scenarios you covered, why you chose them, and anything you deliberately left out and why.

## Grading Rubric

Your submission is graded out of **10 points** across three dimensions:

| Criteria | Points | What We're Looking For |
| --- | --- | --- |
| **Implementation** | 5 | All requirement IDs from the spec are addressed, the contract deploys without errors, and all specified behaviours work correctly |
| **Understanding** | 3 | Logic is structured sensibly, naming is intentional, and your comments/README show you know *why*, not just *how* |
| **Code & Design Quality** | 2 | Consistent style, appropriate error handling, no obvious shortcuts — your code is something you'd be comfortable showing in an interview |
| **Total** | **10** |  |

## Tips for a Strong Submission

- **NatSpec is not optional.** Undocumented functions will cost you Understanding and Quality points, even if the logic is correct.
- **Tag every requirement.** Instructors should not have to hunt for where you satisfied `CF-04`. If it's not tagged, it may be marked incomplete.
- **Your README matters.** A thoughtful README that honestly describes what you struggled with carries more weight than a perfect-looking README that says nothing. Genuine reflection is what the Understanding criterion rewards.
- **Write tests with intent.** Don't just test the happy path. Think about what could go wrong - edge cases, zero values, unauthorised callers — and explain your reasoning in the README.

## Submission Checklist

Before opening your PR, confirm the following:

- [ ] All functions have complete NatSpec documentation
- [ ] Every requirement ID from the spec is tagged in code comments
- [ ] README includes: What I Learned, Problems & Solutions, Testing Approach
