# Solidity Production Style Guide

# Solidity Production Style Guide

**Industry Best Practices for the Ethereum Ecosystem**

*Edition: Solidity 0.8.x · June 2026*

---

This style guide establishes the conventions and best practices for writing production-grade Solidity code in the Ethereum ecosystem. It was compiled from the following authoritative sources:

- Solidity Language Documentation — <https://docs.soliditylang.org/en/latest/style-guide.html>
- Solidity NatSpec Format — <https://docs.soliditylang.org/en/latest/natspec-format.html>
- OpenZeppelin Contracts (v5) — <https://docs.openzeppelin.com/contracts/5.x/>
- ConsenSys Diligence — Smart Contract Best Practices — <https://consensysdiligence.github.io/smart-contract-best-practices>
- Trail of Bits — Building Secure Contracts — <https://secure-contracts.com/development-guidelines/guidelines.html>

---

## Table of Contents

1. Introduction
2. File Structure and Layout
3. Contract Layout and Element Order
4. Naming Conventions
5. Formatting and Whitespace
6. Documentation (NatSpec)
7. Types and State Variables
8. Functions
9. Error Handling
10. Events
11. Security Patterns
12. Inheritance and Libraries
13. Modifiers
14. Gas Optimisation
15. Upgradability
16. Testing Standards
17. Tooling and Automation
18. Production Readiness Checklist
19. Complete Annotated Example

---

## 1. Introduction

Solidity is not a typical programming language. Code deployed to Ethereum is immutable by default, publicly visible, and directly handles financial value. Every stylistic and architectural choice carries consequences that extend beyond readability. This guide reflects that reality.

### 1.1 Guiding Principles

- **Correctness over cleverness.** Code that is easy to reason about is easier to audit, and easier to audit means fewer exploits.
- **Simplicity is a security property.** Complexity is the enemy of security. The simplest solution that satisfies requirements is almost always the right one.
- **Consistency throughout a codebase matters more than adherence to any individual rule.** Where a project’s existing conventions differ from this guide, prefer consistency within that project.
- **Assume adversarial conditions.** Code will be read by attackers. Design and comment accordingly.

---

## 2. File Structure and Layout

### 2.1 File Header

Every Solidity source file must begin with two lines in this exact order: an SPDX licence identifier and a pragma directive. Both are required.

solidity

```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.24;
```

Omitting the SPDX identifier produces a compiler warning and signals to readers that the licence status is unknown. Use a standard SPDX identifier from spdx.org/licenses/. MIT is common for open-source contracts; use a proprietary identifier if the code is not open-source.

#### 2.1.1 Pragma: Fixed vs. Floating

Pin the pragma to a specific version in application contracts. Use a floating range only in libraries intended for others to inherit.

| Context | Pragma style |
| --- | --- |
| Deployed contract | `pragma solidity 0.8.24;` (exact version) |
| Library / package (e.g. OpenZeppelin-style) | `pragma solidity ^0.8.20;` (floating range) |

If you are the deployer, you know the compiler version used. Fixing it removes ambiguity. If others consume your library, you cannot know their compiler, so a range is appropriate. Never use `pragma solidity >= 0.8.0;` without an upper bound in application code.

### 2.2 Import Order

Imports must be explicit (named imports only) and ordered as follows, with a blank line between each group:

1. External package imports (npm / Foundry remappings)
2. Internal project imports from parent directories
3. Internal project imports from the same directory

solidity

```
// External
import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import {Ownable} from "@openzeppelin/contracts/access/Ownable.sol";

// Internal – parent
import {IVault} from "../interfaces/IVault.sol";

// Internal – same directory
import {VaultLib} from "./VaultLib.sol";
```

- Always use named imports: `import {ERC20} from "...";` not `import "...";`
- Pin the library version in the import path where your toolchain supports it: `@openzeppelin/contracts@5.0.2` prevents silent breakage when a dependency updates.
- Delete all unused imports. Static analysis tools (Slither) will flag them.

### 2.3 File Naming and One-Contract-Per-File

- One primary contract, interface, or library per file.
- File name must exactly match the primary contract/interface/library name: `Vault.sol` for `contract Vault`.
- **Interfaces:** prefix with `I`. File: `IVault.sol`, declaration: `interface IVault`.
- **Abstract base contracts:** prefix with `Base` or `Abstract`. Example: `BaseVault.sol`.
- **Libraries:** no special prefix. Example: `SafeMath.sol`, `VaultLib.sol`.

---

## 3. Contract Layout and Element Order

The official Solidity style guide specifies a canonical ordering of elements within a contract. All contracts must follow this order precisely. Consistent ordering lets reviewers and auditors navigate code without needing to search.

### 3.1 Element Order

Within a contract, elements must appear in this sequence:

1. Type declarations (`using` statements, `struct`, `enum` definitions)
2. State variable declarations
3. Events
4. Errors (custom errors)
5. Modifiers
6. Constructor
7. `receive` function (if present)
8. `fallback` function (if present)
9. External functions
10. Public functions
11. Internal functions
12. Private functions

solidity

```
contract Vault is Ownable, ReentrancyGuard {
    // 1. Type declarations
    using SafeERC20 for IERC20;

    // 2. State variables
    uint256 public constant MAX_DEPOSIT = 1_000_000e18;
    uint256 private _totalDeposited;
    mapping(address => uint256) private _balances;

    // 3. Events
    event Deposited(address indexed depositor, uint256 amount);
    event Withdrawn(address indexed recipient, uint256 amount);

    // 4. Errors
    error InsufficientBalance(uint256 available, uint256 requested);
    error DepositLimitExceeded();

    // 5. Modifiers
    modifier validAmount(uint256 amount) {
        if (amount == 0) revert ZeroAmount();
        _;
    }

    // 6. Constructor
    constructor(address owner_) Ownable(owner_) {}

    // 7. Receive / fallback (if needed)
    receive() external payable { revert DirectEtherNotAccepted(); }

    // 8-11. Functions by visibility (see Section 8)
}
```

### 3.2 Ordering within Visibility Groups

Within each visibility group (external / public / internal / private), order functions by state-mutability, descending from most to least privileged:

1. `payable`
2. non-payable (state-changing)
3. `view`
4. `pure`

This ordering mirrors how callers think about the contract’s API: what can send ETH, what changes state, what only reads, what has no side effects. It also clusters the highest-risk functions at the top where reviewers naturally look first.

---

## 4. Naming Conventions

Consistent, descriptive naming is the single highest-leverage readability practice. The following rules follow the official Solidity style guide with additions from production codebases.

### 4.1 Casing Rules

| Element | Convention and Example |
| --- | --- |
| Contracts, interfaces, libraries, structs, enums | `UpperCamelCase` — `Vault`, `IVault`, `SafeMath`, `UserPosition`, `TokenType` |
| Functions, local variables, function parameters | `lowerCamelCase` — `deposit()`, `userBalance`, `maxAmount` |
| State variables (public) | `lowerCamelCase` — `totalSupply`, `feeRate` |
| State variables (private / internal) | `lowerCamelCase` with leading underscore — `_balance`, `_owner` |
| Constants | `SCREAMING_SNAKE_CASE` — `MAX_SUPPLY`, `BASIS_POINTS` |
| Immutables | `SCREAMING_SNAKE_CASE` — `UNDERLYING_TOKEN`, `DEPLOYER` |
| Events | `UpperCamelCase`, past tense — `Deposited`, `OwnershipTransferred` |
| Custom errors | `UpperCamelCase`, descriptive noun/adjective — `InsufficientBalance`, `ZeroAmount` |
| Modifiers | `lowerCamelCase` — `onlyOwner`, `whenNotPaused` |
| Enum members | `UpperCamelCase` — `Active`, `Paused`, `Closed` |

### 4.2 Naming Quality Rules

- **Avoid generic nouns.** `user`, `data`, `info`, `addressTo` are imprecise. Prefer `depositor`, `recipient`, `userData` → `userAccount`, `poolInfo` → `poolConfig`.
- **Maintain a single canonical term per real-world entity.** If `depositor` and `liquidityProvider` refer to the same actor, pick one and use it everywhere.
- **Include units in numeric variable names.** `interestRate` is ambiguous; `interestRateBps` (basis points), `feeInWei`, or `durationInSeconds` are not.
- **State-changing functions must contain a verb.** `deposit()`, `withdraw()`, `setFee()`, `emergencyPause()` clearly communicate intent.
- **Use `get` prefix for view functions that return a computed value:** `getVaultBalance()`, `getUserShares()`.
- **Do not use conflicting underscore conventions.** If `_` prefix means “private state variable”, do not also use it for function parameters. Pick one semantic and apply it consistently throughout the entire codebase.

### 4.3 Function Parameter Shadowing

When a constructor or setter parameter would shadow a state variable of the same name, suffix the parameter with a trailing underscore:

solidity

```
address public owner;

constructor(address owner_) {
    owner = owner_;
}
```

Do not use the leading-underscore convention for parameters (i.e., avoid `_owner` as a parameter name) since that conflicts with the convention for private state variables.

---

## 5. Formatting and Whitespace

### 5.1 Indentation

- Use 4 spaces per indentation level. Never use tabs.
- Do not mix spaces and tabs within a project.
- Enforce automatically using Prettier with the Solidity plugin (`prettier-plugin-solidity`) or `forge fmt`.

### 5.2 Line Length

- Maximum line length: **120 characters.**
- The official style guide recommends 79 characters, but 120 is the accepted modern standard in the Ethereum ecosystem, as lines with many type annotations and modifiers routinely exceed 79 characters.
- When a function signature exceeds the line limit, break after each parameter and align the closing parenthesis with the opening line:

solidity

```
function deposit(
    address token,
    uint256 amount,
    address recipient
) external nonReentrant returns (uint256 shares) {
    // ...
}
```

### 5.3 Blank Lines

- Two blank lines between top-level declarations (contracts, interfaces, libraries).
- One blank line between function declarations within a contract.
- One blank line between logically distinct blocks within a function.
- No trailing whitespace.
- One blank line at the end of each file.

### 5.4 Braces

- Opening brace on the same line as the declaration (K&R style), preceded by a single space.
- Closing brace on its own line.
- **Always use braces, even for single-statement `if`/`else` bodies.** Never use braceless conditionals.

solidity

```
// CORRECT
if (amount == 0) {
    revert ZeroAmount();
}

// INCORRECT — never omit braces
if (amount == 0) revert ZeroAmount();
```

### 5.5 Spacing Around Operators

- Single space on each side of binary operators: `a + b`, `x == y`.
- No space between unary operator and operand: `-x`, `!flag`, `++i`.
- No space inside parentheses: `f(a, b)`, not `f( a, b )`.
- Single space after commas in argument lists.
- No space before a semicolon.

### 5.6 Large Numbers

Use underscores to separate thousands groups in numeric literals. This is a language feature with no runtime cost:

solidity

```
uint256 public constant MAX_SUPPLY       = 1_000_000_000e18;
uint256 public constant BASIS_POINTS_MAX = 10_000;
uint256 public constant ONE_YEAR         = 365 days;
```

### 5.7 Solidity Time and Ether Units

Always use Solidity’s built-in time and ether unit suffixes rather than raw numbers:

| Avoid | Prefer |
| --- | --- |
| `60 * 60 * 24` | `1 days` |
| `60 * 60 * 24 * 7` | `1 weeks` |
| `10 ** 18` | `1 ether` or `1e18` |
| `msg.value == 100000000000000000` | `msg.value == 0.1 ether` |
| `3600` | `1 hours` |

---

## 6. Documentation (NatSpec)

NatSpec (Natural Language Specification Format) is Solidity’s built-in documentation standard. It is compiled into the ABI and rendered by block explorers including Etherscan. Complete NatSpec coverage for all public and external interfaces is expected in production contracts.

### 6.1 Comment Syntax

- Single-line NatSpec: `///`
- Multi-line NatSpec: `/** ... */`
- Standard single-line comments for internal implementation notes: `//`
- Avoid block comments `/* ... */` for implementation notes; use `//` for each line.

### 6.2 Contract-Level NatSpec

Every contract, interface, and library must have contract-level NatSpec immediately above the declaration:

solidity

```
/// @title Vault – Non-custodial ERC-20 deposit vault
/// @author Foo Protocol (https://foo.xyz)
/// @notice Allows users to deposit ERC-20 tokens and receive yield-bearing
///         share tokens in return.
/// @dev Inherits OpenZeppelin ERC4626. Deposits are paused via Pausable.
///      Shares are calculated using the standard ERC4626 formula.
contract Vault is ERC4626, Pausable, Ownable {
```

### 6.3 Function-Level NatSpec

All public and external functions must be fully documented. Internal and private functions should be documented wherever the logic is non-obvious.

| Tag | When to use |
| --- | --- |
| `@notice` | Describes what the function does for an end user. Plain English. Displayed by Etherscan. |
| `@dev` | Technical notes for developers: state changes, events emitted, reverts triggered, edge cases. |
| `@param <name>` | Describes each input parameter. One tag per parameter. |
| `@return <name>` | Describes each return value. One tag per return value. Always name return values in the NatSpec even if not named in the signature. |
| `@inheritdoc <ContractName>` | Inherits NatSpec from the specified base contract or interface. Use instead of duplicating parent documentation. |

solidity

```
/// @notice Deposit ERC-20 tokens into the vault.
/// @dev Emits Deposited. Reverts if contract is paused or amount is zero.
///      Calls SafeERC20.safeTransferFrom – caller must have approved this contract.
/// @param token   The address of the ERC-20 token to deposit.
/// @param amount  The quantity of tokens to deposit, in the token's native decimals.
/// @return shares The number of vault share tokens minted to the caller.
function deposit(address token, uint256 amount)
    external
    whenNotPaused
    nonReentrant
    returns (uint256 shares)
{
    // ...
}
```

### 6.4 State Variable NatSpec

Public state variables that form part of the contract’s API should have NatSpec:

solidity

```
/// @notice Total tokens deposited across all users.
uint256 public totalDeposited;

/// @notice Mapping of user address to their deposited balance.
mapping(address => uint256) public balances;
```

### 6.5 Custom Error NatSpec

Document custom errors. This information is surfaced in tooling and block explorers:

solidity

```
/// @notice Thrown when a caller requests more tokens than their balance.
/// @param available  The caller's actual balance.
/// @param requested  The amount the caller attempted to withdraw.
error InsufficientBalance(uint256 available, uint256 requested);
```

---

## 7. Types and State Variables

### 7.1 Explicit Types

- Always use explicit type sizes. Never use `int` or `uint` without a size suffix: use `uint256`, `int128`, etc.
- Use `uint256` as the default unsigned integer type. Only use smaller types when packing storage slots (see 7.3).
- Use `address payable` only where Ether must be sent to the address. Use `address` for all other address storage.

### 7.2 Constants and Immutables

Constants and immutables are embedded directly in contract bytecode, costing zero storage reads (SLOAD). Use them aggressively:

| Pattern | When to use |
| --- | --- |
| `constant` | Value is known at compile time and never changes. e.g. `MAX_SUPPLY`, `BASIS_POINTS`. |
| `immutable` | Value is set once in the constructor and never changes. e.g. token address, owner, fee rate set at deployment. |
| State variable | Only when the value must change after deployment. |

solidity

```
// constant — compile-time value
uint256 public constant BASIS_POINTS = 10_000;

// immutable — set once in constructor
address public immutable UNDERLYING_TOKEN;

constructor(address token_) {
    UNDERLYING_TOKEN = token_;
}
```

### 7.3 Storage Packing

The EVM stores state variables in 32-byte (256-bit) slots. Reading or writing a slot costs gas. Pack related variables of smaller types into adjacent declarations to minimise the number of slots used:

solidity

```
// INEFFICIENT: three separate slots
uint256 public a;  // slot 0
uint128 public b;  // slot 1 (wastes 128 bits)
uint128 public c;  // slot 2 (wastes 128 bits)

// EFFICIENT: b and c share one slot
uint256 public a;  // slot 0
uint128 public b;  // slot 1 (lower 128 bits)
uint128 public c;  // slot 1 (upper 128 bits)
```

Storage packing trades readability for gas efficiency. Only pack variables that are logically related and frequently accessed together. Do not pack variables that are updated independently in the same transaction, as this forces multiple SLOADs to retrieve the shared slot.

### 7.4 Magic Numbers

All numeric literals with meaning must be extracted to named constants. A number without a name forces every reader to infer its meaning from context:

solidity

```
// BAD — what do 25 and 10_000 mean here?
uint256 fee = (amount * 25) / 10_000;

// GOOD — intent is explicit
uint256 public constant FEE_NUMERATOR   = 25;
uint256 public constant FEE_DENOMINATOR = 10_000; // basis points

uint256 fee = (amount * FEE_NUMERATOR) / FEE_DENOMINATOR;
```

### 7.5 Visibility

All state variables must have explicit visibility. Never rely on the default (which is `internal`).

- Use `private` by default.
- Use `internal` only if derived contracts genuinely need direct access.
- Use `public` only if the variable forms part of the contract’s public API (which automatically creates a getter function).
- Never make a state variable `public` if it exposes sensitive information.

---

## 8. Functions

### 8.1 Function Modifier Order

Function modifiers must appear in the following order on every function declaration:

1. Visibility: `public`, `external`, `internal`, `private`
2. State mutability: `payable` (explicit), then nothing (implicit non-payable), then `view`, then `pure`
3. `virtual` (if the function may be overridden)
4. `override` (if overriding a parent)
5. Custom modifiers (e.g. `onlyOwner`, `whenNotPaused`, `nonReentrant`)

solidity

```
// visibility → mutability → virtual/override → custom
function deposit(uint256 amount) external payable nonReentrant { }
function getBalance() public view returns (uint256) { }
function _transfer(address to, uint256 amount) internal virtual { }
function supportsInterface(bytes4 id) public view override returns (bool) { }
```

### 8.2 Function Size and Responsibility

Write small functions with clear, single purposes. The goal is for each function to be independently testable, auditable, and understandable without reading supporting context.

- If a function body exceeds 40–50 lines, consider whether its logic can be split into clearly-named helper functions.
- Separate validation logic, state changes, and external calls into distinct, named helper functions for complex flows.
- Do not use the `virtual` modifier on functions that will not be overridden. Marking a function `virtual` when it will never be overridden misleads readers about the contract’s design intentions.

### 8.3 Return Values from External Calls

Always handle return values from external calls. Ignoring a return value silently allows a failed call to proceed:

solidity

```
// BAD — ignores return value; call may have failed
token.transfer(recipient, amount);

// GOOD — use SafeERC20 which checks and reverts on failure
token.safeTransfer(recipient, amount);

// GOOD — or check manually for non-standard tokens
(bool success, ) = address(token).call(abi.encodeWithSelector(
    IERC20.transfer.selector, recipient, amount
));
require(success, "Transfer failed");
```

### 8.4 Receive and Fallback Functions

Both `receive` and `fallback` should be present only when explicitly required. If Ether should not be sent directly to the contract, both should revert with a clear error:

solidity

```
// Explicit rejection — clear intent
receive() external payable {
    revert DirectEtherNotAccepted();
}

fallback() external {
    revert FallbackNotSupported();
}
```

The `receive` function handles plain Ether transfers. The `fallback` handles calls with calldata that do not match any function selector, or plain Ether transfers if `receive` is not defined. Separate them and make their intent explicit.

---

## 9. Error Handling

### 9.1 Custom Errors (Required in Solidity 0.8.4+)

Custom errors are the required error mechanism for new production code. They are more gas-efficient than `require` with string messages (the error selector is 4 bytes vs. ABI-encoding a full string) and provide structured, machine-readable error data.

solidity

```
// REQUIRED in new code — custom errors with if/revert
error InsufficientBalance(uint256 available, uint256 requested);
error ZeroAmount();
error NotAuthorised();

function withdraw(uint256 amount) external {
    if (amount == 0) revert ZeroAmount();
    if (_balances[msg.sender] < amount) {
        revert InsufficientBalance(_balances[msg.sender], amount);
    }
    // ...
}

// DEPRECATED in new code — require with string message
require(amount > 0, "Amount must be > 0");  // more gas, less useful
```

### 9.2 assert vs. require vs. revert

| Mechanism | Correct Use |
| --- | --- |
| `assert()` | Internal invariant checking only. An `assert` failure indicates a bug in the contract itself. Uses `Panic` error type. Should never trigger under normal use. Not for input validation. |
| `require()` / `if...revert` | Input validation, precondition checking, and validating return values from external calls. The correct tool for all user-facing error conditions. |
| `revert()` | Unconditional revert, typically in an else-branch or after a manual check. Always pair with a custom error. |

solidity

```
function deposit(uint256 amount) external {
    // if+revert: validating user input
    if (amount == 0) revert ZeroAmount();

    _totalDeposited += amount;
    _balances[msg.sender] += amount;

    // assert: verifying internal invariant — should never fail
    assert(_totalDeposited >= amount);
}
```

### 9.3 Error Naming Conventions

- Name errors as noun phrases describing the condition, not the action: `InsufficientBalance`, not `BalanceCheckFailed`.
- Include relevant state data in error parameters where useful: `InsufficientBalance(available, requested)`.
- Declare errors at the contract level, not inside functions.
- Provide NatSpec for every custom error (see Section 6.5).

---

## 10. Events

Log all critical operations. Events are the primary mechanism for off-chain monitoring and incident response. They are cheap and irreversible.

### 10.1 When to Emit Events

- Every state-changing operation that represents a meaningful business event.
- All access control changes (ownership transfers, role grants, role revocations).
- All configuration changes (fee rate updates, limit changes, pause/unpause).
- All token transfers, mints, and burns.
- All governance actions.

### 10.2 Event Design Rules

- **Index the primary lookup key(s).** Three indexed parameters are the maximum. Use `indexed` on addresses that off-chain systems will filter by (e.g. `depositor`, `recipient`, `token`).
- **Include both old and new values when emitting from a setter function.** This enables off-chain systems to reconstruct history without tracking prior state:

solidity

```
event FeeRateUpdated(uint256 indexed oldRate, uint256 indexed newRate);

function setFeeRate(uint256 newRate) external onlyOwner {
    uint256 old = feeRate;
    feeRate = newRate;
    emit FeeRateUpdated(old, newRate);
}
```

- **Name events in past tense (UpperCamelCase):** `Deposited`, `OwnershipTransferred`, `Paused`, `RoleGranted`.
- **Do not use events as a substitute for return values.** Emit the event in addition to returning the value.

---

## 11. Security Patterns

Security is not a separate concern from style. The following patterns must be applied consistently in production code.

### 11.1 Checks-Effects-Interactions (CEI) Pattern

Every state-changing function that interacts with external contracts must follow the CEI pattern. Violating CEI is the root cause of most reentrancy vulnerabilities.

1. **Checks:** validate all preconditions (inputs, permissions, state).
2. **Effects:** apply all state changes to the contract’s storage.
3. **Interactions:** make external calls, token transfers, and ETH sends last.

solidity

```
function withdraw(uint256 amount) external nonReentrant {
    // 1. CHECKS
    if (amount == 0) revert ZeroAmount();
    if (_balances[msg.sender] < amount) {
        revert InsufficientBalance(_balances[msg.sender], amount);
    }

    // 2. EFFECTS (state updated BEFORE external call)
    _balances[msg.sender] -= amount;
    _totalDeposited -= amount;

    // 3. INTERACTIONS (external call LAST)
    UNDERLYING_TOKEN.safeTransfer(msg.sender, amount);
    emit Withdrawn(msg.sender, amount);
}
```

### 11.2 Reentrancy Protection

Apply both CEI and OpenZeppelin’s `ReentrancyGuard` to every function that sends Ether, calls external contracts, or transfers tokens. Do not rely on CEI alone for high-value functions:

solidity

```
import {ReentrancyGuard} from "@openzeppelin/contracts/utils/ReentrancyGuard.sol";

contract Vault is ReentrancyGuard {
    function withdraw(uint256 amount) external nonReentrant {
        // ...
    }
}
```

On chains that support EIP-1153 (transient storage, available on Ethereum mainnet post-Dencun), consider using OpenZeppelin’s `ReentrancyGuardTransient`. It provides equivalent protection at lower gas cost because transient storage is automatically cleared at transaction end.

### 11.3 Access Control

Use OpenZeppelin’s battle-tested access control contracts. Do not implement custom access control for standard roles unless there is a specific design requirement:

| Contract | Use case |
| --- | --- |
| `Ownable` / `Ownable2Step` | Single-owner contracts. Prefer `Ownable2Step` — it requires the new owner to accept, preventing accidental transfers to wrong addresses. |
| `AccessControl` | Role-based access control with multiple roles. Preferred for complex permission models. |
| `AccessControlEnumerable` | As above, with the ability to enumerate role members on-chain. |

- **Never use `tx.origin` for authentication.** Use `msg.sender` exclusively. `tx.origin` is vulnerable to phishing attacks and breaks account abstraction compatibility.
- Separate privileged operations from standard user operations. Never combine admin functions and user functions in the same call path.
- Apply the principle of least privilege: grant only the permissions required.

### 11.4 Integer Arithmetic

Solidity 0.8.0 introduced built-in overflow and underflow checking. The `SafeMath` library is no longer required for standard arithmetic. However:

- Use `unchecked { }` blocks only where overflow is mathematically impossible and gas savings are material. Document the reason:

solidity

```
// Safe: i is bounded by array length, overflow impossible
for (uint256 i = 0; i < items.length; ) {
    // ...
    unchecked { ++i; } // saves ~40 gas per iteration
}
```

- **Prefer `++i` over `i++`** in loops. Pre-increment is slightly more gas-efficient as it does not create a temporary copy.
- Be explicit about precision loss in division. Solidity integer division truncates. Where rounding matters, document the direction of rounding:

solidity

```
// Rounds down: user receives slightly less, excess stays in contract
uint256 fee = (amount * FEE_NUMERATOR) / FEE_DENOMINATOR;
```

### 11.5 External Calls

Treat every external call as a potential attack vector. External contracts can be malicious, can reenter your contract, or can fail unexpectedly.

**Use the pull-over-push pattern for ETH distributions.** Instead of pushing ETH to multiple recipients in one call, record balances owed and let recipients pull their own funds:

solidity

```
// PUSH — vulnerable if any recipient reverts or reenters
for (uint i = 0; i < recipients.length; i++) {
    recipients[i].transfer(amount);
}

// PULL — safe pattern
mapping(address => uint256) public pendingWithdrawals;

function withdraw() external nonReentrant {
    uint256 amount = pendingWithdrawals[msg.sender];
    pendingWithdrawals[msg.sender] = 0;  // effects before interactions
    (bool success, ) = msg.sender.call{value: amount}("");
    if (!success) revert TransferFailed();
}
```

- **Always use `SafeERC20`** from OpenZeppelin when transferring ERC-20 tokens. Non-standard tokens (e.g. USDT) do not return a boolean on transfer, and `SafeERC20` handles these correctly.
- **Always check the return value of low-level `call()`.** A call that returns `false` has failed.
- Minimise the number of external calls within a single transaction. Each call to an external contract expands the attack surface.

### 11.6 Timestamp and Block Number Dependence

- Never use `block.timestamp` for precise timing with second-level granularity. Validators can manipulate timestamps within a ~15-second window.
- Do not use `block.timestamp` as a source of randomness.
- For deadlines and expiry, a tolerance of a few minutes is acceptable. For games of chance or pseudo-random selection, use a commit-reveal scheme or Chainlink VRF.
- Never use `block.number` as a precise timer. Block times vary. Use `block.timestamp` for time-based logic, accepting its limitations.

---

## 12. Inheritance and Libraries

### 12.1 Inheritance Hierarchy

Keep the inheritance tree shallow and narrow. Deep hierarchies obscure storage layout, complicate audits, and make the MRO (method resolution order) in Solidity’s C3 linearisation difficult to reason about.

- Prefer composition over inheritance where possible.
- No more than three to four levels of inheritance depth for production contracts.
- Be explicit about the inheritance order. Solidity resolves function conflicts using C3 linearisation (most-derived to most-base, right-to-left). List the most-derived (most specific) contracts first:

solidity

```
// Most specific first, most generic last
contract Vault is ERC4626, Pausable, Ownable2Step, ReentrancyGuard {
```

- Call `super` deliberately, not blindly. Understand what each parent’s function does before calling it.

### 12.2 Interfaces vs. Abstract Contracts

| Use | When |
| --- | --- |
| `interface` | Defining the external API of a contract type. No implementation. All functions are implicitly `external`. Use for ERC standards, protocol hooks, and cross-contract calls. |
| `abstract contract` | When you have partial implementation to share but the contract is not directly deployable. Use as a base when implementation code must be shared between concrete contracts. |
| `library` | For stateless helper functions that operate on types. Libraries have no storage. Use for mathematical operations, type conversion, and reusable algorithm implementations. |

### 12.3 Using OpenZeppelin

OpenZeppelin Contracts is the canonical library for the Ethereum ecosystem. Its code is extensively audited, widely deployed, and maintained by dedicated security engineers.

- **Always import from a published release.** Never copy-paste OpenZeppelin source into your project. Pinned imports ensure you receive security patches via dependency updates.
- Use OpenZeppelin’s standard contracts (`ERC20`, `ERC721`, `ERC1155`, etc.) rather than writing custom implementations of these standards.
- When writing an ERC-20, extend OpenZeppelin’s `ERC20`. When writing an NFT, extend `ERC721` or `ERC1155`. The standards are subtle — edge cases abound.
- Review OpenZeppelin’s contracts changelog when upgrading library versions. Contracts 5.x introduced breaking changes from 4.x, including constructor signature changes in `Ownable` and error renaming across most contracts.

---

## 13. Modifiers

Modifiers encapsulate reusable precondition checks. Used correctly, they eliminate duplicate validation code and make function signatures self-documenting. Misused, they obscure control flow and complicate audits.

### 13.1 Rules for Modifiers

- Use modifiers only for access control checks and simple state preconditions (e.g. `whenNotPaused`, `onlyOwner`). They are a good fit for guard conditions that apply to multiple functions.
- Do not put complex logic in modifiers. If the modifier body exceeds a few lines of validation, extract it into an internal function and call that from the modifier.
- Do not use modifiers for Checks-Effects-Interactions sequences. Mixing effects and interactions across a modifier and function body makes the CEI order impossible to trace.
- Each modifier should express one clear condition. Do not chain multiple unrelated conditions in a single modifier.

solidity

```
// GOOD — single, clear purpose
modifier onlyOwner() {
    if (msg.sender != owner) revert NotOwner();
    _;
}

// GOOD — reads cleanly at the function signature level
function pause() external onlyOwner whenNotPaused {
    _pause();
}

// BAD — modifier contains business logic and side effects
modifier processAndValidate(uint256 amount) {
    require(amount > 0);
    _totalFees += calculateFee(amount); // side effect in modifier!
    _;
}
```

---

## 14. Gas Optimisation

Gas optimisation is important but must never compromise security or readability. The correct order of priorities is: **correct, secure, readable, then efficient.** Premature optimisation of gas is a common source of subtle bugs.

### 14.1 High-Impact Patterns

| Pattern | Guidance |
| --- | --- |
| Storage reads / writes | Each SLOAD costs 100–800 gas; each SSTORE costs 5,000–20,000 gas. Cache storage reads in local memory variables when a value is used more than once within a function. |
| Custom errors | Use custom errors over `require` strings. The 4-byte selector encoding is cheaper than ABI-encoding a string. Already required by this guide (see Section 9). |
| Packing storage | Pack related smaller-type variables into the same slot (see Section 7.3). |
| Constants and immutables | Constants and immutables cost zero for reads. Use them aggressively (see Section 7.2). |
| Loop incrementors | Use `unchecked { ++i; }` in bounded loops (see Section 11.4). |
| Calldata vs. memory | Use `calldata` for external function parameters that are read-only. `calldata` is cheaper than `memory` for complex types. |
| Short-circuit evaluation | Solidity evaluates `&&` and `||` left-to-right, short-circuiting on the first determinative value. Place the cheapest (or most likely to fail) check first. |
| Events vs. storage | If data is only needed off-chain, emit it in an event rather than storing it. Events are significantly cheaper than storage. |

### 14.2 Calldata Parameter Guidance

solidity

```
// LESS EFFICIENT: memory copies the array on function entry
function processItems(uint256[] memory items) external { }

// MORE EFFICIENT: calldata reads directly from call data
function processItems(uint256[] calldata items) external { }
```

### 14.3 Avoid Premature Optimisation

- Use `uint256` as the default integer type. The EVM operates on 32-byte words; smaller types are padded and can occasionally cost more, not less, for isolated variables.
- **Do not use inline assembly (Yul) unless you have deep EVM expertise and the gas savings are measured and material.** Assembly bypasses Solidity’s safety checks and is difficult to audit.
- **Profile before optimising.** Use Foundry’s gas reports (`forge test --gas-report`) or Hardhat Gas Reporter to identify actual bottlenecks rather than optimising by intuition.

---

## 15. Upgradability

Decide on upgradability before writing any code, because this decision fundamentally shapes the contract’s architecture.

### 15.1 Core Principle

Favour contract migration over upgradeability where possible. Migration means deploying a new contract and migrating state, rather than upgrading in-place via proxies. Migration avoids proxy-specific risks while offering similar flexibility.

If upgradeability is required, understand its costs:

- Upgradeable contracts introduce significant complexity: proxy-implementation storage layout alignment, initialiser patterns replacing constructors, and the risk of uninitialised implementations.
- Upgradeability is a trust assumption. Users must trust the upgrade key holder. Consider timelocks and multi-sig governance for all upgrade authority.
- Use OpenZeppelin’s Upgrades plugins for Hardhat or Foundry. Never implement a custom upgrade mechanism without security review.

### 15.2 Proxy Pattern Rules (if used)

- **Storage layout must be identical between proxy and implementation.** Derive both from a shared base storage contract, or use ERC-7201 namespaced storage.
- **Never use constructors in implementation contracts.** Use an initialiser function with an initialised guard to prevent re-initialisation:

solidity

```
import {Initializable} from "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";

contract VaultImpl is Initializable {
    function initialize(address owner_) external initializer {
        // ...
    }
}
```

- **Immediately initialise the implementation contract after deployment.** Uninitialised implementation contracts have caused catastrophic losses.
- **Check for function shadowing.** If a function of the same selector exists on both the proxy and the implementation, the proxy’s function will be called. Audit for this explicitly.
- **Use `slither-check-upgradability`** from Trail of Bits’ Slither to verify proxy storage layout safety before deployment.

---

## 16. Testing Standards

An extensive test suite is essential for developing high-quality smart contracts. Testing is not a separate phase — it is an integral part of contract development.

### 16.1 Required Test Coverage

- Every public and external function must have unit tests covering the happy path, all expected revert conditions, and boundary conditions.
- **Access control:** explicitly test that each protected function reverts when called by an unauthorised address.
- **Events:** assert that the correct events are emitted with the correct indexed parameters.
- **State transitions:** assert the state of the contract before and after each operation.
- **Integer boundaries:** test with zero, one, `uint256.max`, and at least one realistic mid-range value.

### 16.2 Testing Tools

| Tool | Purpose |
| --- | --- |
| Foundry (`forge`) | Primary testing framework. Fast, Solidity-native tests, built-in fuzzing and invariant testing, gas profiling, forking. |
| Hardhat | JavaScript/TypeScript-based tests. Use where ecosystem integrations require it, or for integration tests that require off-chain scripting. |
| Slither (Trail of Bits) | Static analyser. Detects common vulnerabilities, code quality issues, and style violations. Run in CI on every pull request. |
| Medusa (Trail of Bits) | Primary coverage-guided fuzzer (v1 released February 2025). Parallel fuzzing, on-chain state seeding, and Slither-integrated value generation. The recommended fuzzer for new projects. |
| Echidna (Trail of Bits) | Property-based fuzzer. Predecessor to Medusa; now in maintenance mode (minor bug fixes only). Use Medusa for new projects; Echidna remains suitable for existing test suites written against it. |
| Halmos (a16z) | Symbolic testing tool that runs directly against existing Foundry tests with no separate property language required. Open-source; install via pip. Use for bounded formal verification of invariants early in development. |

### 16.3 Foundry Test Naming Convention

solidity

```
// test_<functionName>_<condition>_<expectedOutcome>
function test_deposit_normalAmount_mintsCorrectShares() public { }
function test_deposit_zeroAmount_revertsZeroAmount() public { }
function test_deposit_whenPaused_revertsPaused() public { }

// Fuzz tests use testFuzz_ prefix
function testFuzz_deposit_anyAmount_totalDepositedIncreases(
    uint256 amount
) public { }

// Invariant tests use invariant_ prefix
function invariant_totalDepositedEqualsBalancesSum() public { }
```

### 16.4 Continuous Integration

- Run `forge test` on every pull request. No exceptions.
- Run `slither` on every pull request and treat high-severity findings as blocking.
- Run `forge test --gas-report` periodically. Gas regressions should be reviewed and accepted deliberately, not silently.
- Maintain minimum **90% line coverage** for production contracts. Use `forge coverage`.

---

## 17. Tooling and Automation

Integrate the following tools into the development workflow from the start of a project.

| Tool | Role and Integration Point |
| --- | --- |
| Prettier + `prettier-plugin-solidity` | Code formatter. Enforces indentation, line length, spacing, and brace style. Run as a pre-commit hook and in CI. |
| Solhint | Solidity linter. Enforces naming conventions, visibility, NatSpec completeness, and import style. Configure with `solhint:recommended` plus custom rules. Run in CI. |
| Slither (Trail of Bits) | Static analyser and security detector. Run in CI on every pull request. Fix all high and medium findings before merge. |
| Foundry (`forge fmt`) | Native Foundry formatter. An alternative to Prettier; both are acceptable. Choose one and enforce it consistently. |
| `forge test --gas-report` | Gas profiling. Run periodically to track gas usage. Review regressions. |
| Echidna / Medusa | Fuzz and invariant testing. Essential for protocols handling significant value. |

### 17.1 Pre-commit Hooks

Configure a pre-commit hook (using Husky or Foundry’s hook support) to run at minimum:

1. Prettier / `forge fmt` (auto-format)
2. Solhint (lint)
3. `forge build` (compilation check)

---

## 18. Production Readiness Checklist

Use this checklist before declaring a contract ready for production deployment.

### File and Structure

- [ ] `SPDX-License-Identifier` on line 1
- [ ] Pragma pinned to a specific version
- [ ] Named imports only, with version pins
- [ ] One contract per file, filename matches contract name
- [ ] Contract elements in correct order (types, vars, events, errors, modifiers, constructor, functions)

### Naming and Documentation

- [ ] All naming conventions followed (`UpperCamelCase`, `lowerCamelCase`, `SCREAMING_SNAKE_CASE`)
- [ ] NatSpec complete for all public/external functions, state variables, and custom errors
- [ ] No magic numbers — all numeric literals named as constants
- [ ] No commented-out code

### Security

- [ ] CEI pattern applied in all state-changing functions with external interactions
- [ ] `nonReentrant` applied to all functions sending ETH or transferring tokens
- [ ] Access control applied to all admin/privileged functions
- [ ] `tx.origin` not used for authentication
- [ ] `SafeERC20` used for all ERC-20 transfers
- [ ] All external call return values checked
- [ ] No inline assembly unless absolutely necessary and documented
- [ ] Timestamp usage justified and documented where approximate tolerance is acceptable

### Error Handling

- [ ] Custom errors used in all revert conditions
- [ ] `assert()` used only for internal invariants, never for input validation
- [ ] All error conditions covered by tests

### Gas and Efficiency

- [ ] Storage reads cached in memory for multi-use values
- [ ] `calldata` used for read-only array/struct parameters in external functions
- [ ] Bounded loop increments use `unchecked`
- [ ] Events used instead of storage for off-chain-only data

### Testing and Tooling

- [ ] 90%+ line coverage achieved
- [ ] All revert conditions explicitly tested
- [ ] Slither run with no high or medium severity findings
- [ ] Pre-commit hooks configured and active
- [ ] Foundry gas report reviewed

---

## 19. Complete Annotated Example

The following contract demonstrates all style conventions in a single coherent example.

solidity

```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.24;

import {IERC20}          from "@openzeppelin/contracts/token/ERC20/IERC20.sol";
import {SafeERC20}       from "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
import {Ownable2Step}    from "@openzeppelin/contracts/access/Ownable2Step.sol";
import {ReentrancyGuard} from "@openzeppelin/contracts/utils/ReentrancyGuard.sol";
import {Pausable}        from "@openzeppelin/contracts/utils/Pausable.sol";

/// @title SimpleVault – Single-asset deposit vault
/// @author Foo Protocol
/// @notice Users deposit an ERC-20 token and earn yield.
///         Deposits and withdrawals are pausable by the owner.
/// @dev Non-upgradeable. Uses CEI + ReentrancyGuard for reentrancy safety.
contract SimpleVault is Ownable2Step, ReentrancyGuard, Pausable {
    using SafeERC20 for IERC20;

    // -------------------------------------------------------------------------
    // Constants & Immutables
    // -------------------------------------------------------------------------

    /// @notice The maximum total deposits the vault will accept.
    uint256 public constant MAX_TOTAL_DEPOSIT = 10_000_000e18;

    /// @notice The ERC-20 token accepted by this vault.
    IERC20 public immutable UNDERLYING;

    // -------------------------------------------------------------------------
    // State Variables
    // -------------------------------------------------------------------------

    /// @notice Total tokens deposited across all users.
    uint256 public totalDeposited;

    /// @notice Deposited balance per user.
    mapping(address => uint256) private _balances;

    // -------------------------------------------------------------------------
    // Events
    // -------------------------------------------------------------------------

    /// @notice Emitted when a user deposits tokens.
    event Deposited(address indexed depositor, uint256 amount);

    /// @notice Emitted when a user withdraws tokens.
    event Withdrawn(address indexed recipient, uint256 amount);

    // -------------------------------------------------------------------------
    // Errors
    // -------------------------------------------------------------------------

    /// @notice Thrown when a deposit would exceed the vault cap.
    error DepositCapExceeded(uint256 cap, uint256 requested);

    /// @notice Thrown when caller has insufficient balance for withdrawal.
    /// @param available  Caller's actual balance.
    /// @param requested  Amount the caller attempted to withdraw.
    error InsufficientBalance(uint256 available, uint256 requested);

    /// @notice Thrown when a zero-value amount is passed.
    error ZeroAmount();

    // -------------------------------------------------------------------------
    // Constructor
    // -------------------------------------------------------------------------

    /// @param underlying_ Address of the ERC-20 token the vault accepts.
    /// @param owner_      Initial owner address.
    constructor(address underlying_, address owner_) Ownable2Step() {
        UNDERLYING = IERC20(underlying_);
        _transferOwnership(owner_);
    }

    // -------------------------------------------------------------------------
    // External: state-changing
    // -------------------------------------------------------------------------

    /// @notice Deposit tokens into the vault.
    /// @dev Emits Deposited. Reverts if paused, amount is zero, or cap exceeded.
    ///      Caller must have approved this contract for at least `amount`.
    /// @param amount Amount of UNDERLYING tokens to deposit.
    function deposit(uint256 amount)
        external
        whenNotPaused
        nonReentrant
    {
        // CHECKS
        if (amount == 0) revert ZeroAmount();
        uint256 newTotal = totalDeposited + amount;
        if (newTotal > MAX_TOTAL_DEPOSIT) {
            revert DepositCapExceeded(MAX_TOTAL_DEPOSIT, newTotal);
        }

        // EFFECTS
        totalDeposited = newTotal;
        _balances[msg.sender] += amount;

        // INTERACTIONS
        UNDERLYING.safeTransferFrom(msg.sender, address(this), amount);
        emit Deposited(msg.sender, amount);
    }

    /// @notice Withdraw tokens from the vault.
    /// @dev Emits Withdrawn. Reverts if paused, amount is zero, or balance insufficient.
    /// @param amount Amount of UNDERLYING tokens to withdraw.
    function withdraw(uint256 amount)
        external
        whenNotPaused
        nonReentrant
    {
        // CHECKS
        if (amount == 0) revert ZeroAmount();
        uint256 available = _balances[msg.sender];
        if (available < amount) {
            revert InsufficientBalance(available, amount);
        }

        // EFFECTS
        _balances[msg.sender] = available - amount;
        unchecked {
            // Safe: amount <= available <= totalDeposited
            totalDeposited -= amount;
        }

        // INTERACTIONS
        UNDERLYING.safeTransfer(msg.sender, amount);
        emit Withdrawn(msg.sender, amount);
    }

    // -------------------------------------------------------------------------
    // External: admin
    // -------------------------------------------------------------------------

    /// @notice Pause all deposits and withdrawals.
    function pause() external onlyOwner {
        _pause();
    }

    /// @notice Unpause deposits and withdrawals.
    function unpause() external onlyOwner {
        _unpause();
    }

    // -------------------------------------------------------------------------
    // External: view
    // -------------------------------------------------------------------------

    /// @notice Returns the deposited balance of a given account.
    /// @param account The address to query.
    /// @return balance The account's deposited balance.
    function balanceOf(address account)
        external
        view
        returns (uint256 balance)
    {
        return _balances[account];
    }

    // -------------------------------------------------------------------------
    // Fallback: reject direct ETH
    // -------------------------------------------------------------------------

    receive() external payable {
        revert();
    }
}
```
