# 📑 Assignment M12

**Part A – Batch execution of action using EIP 7702**

- Implement a `BatchCallDelegation7702` contract with:
  - `struct Call { address to; uint256 value; bytes data; }`
  - `function execute(Call[] calldata calls)` that:
    - Iterates through calls.
    - Executes each via low-level call
    - Reverts if any fail.
    - Emits an event per call.
    - Accept and forward ETH.
- Deploy the contract to any testnet of your choice that has implemented Pectra Upgrade like Hoodi,Sepolia and HoleSky
- Write a script using [viem.sh](http://viem.sh/) that batches execution of at least three actions in one transaction, authorized with EIP-7702 as follows :
  - **Action 1** : Send 0.01 ETH from the smart EOA (via delegation) to another account
  - **Action 2** : Transfer 100 tokens to another address.
    - Pre-requisites :
      - Deploy ERC20 token
      - Approve ERC20 token to be spent by BatchCallDelegation contract
  - **Action 3** : Call `increment()` of a Counter contract twice.
    - Pre-requisites :
      - Deploy a simple Counter contract that increments an `uint256` variable via `increment()` function
- Add etherscan transaction URL to Readme to show successful execution of above script
- Write tests in foundry that performs above three actions

**Part B – Batch execution of actions using ERC4337**

- Implement `BatchCallDelegation4337` that inherits `BatchCallDelegation7702` , [IAccount](https://github.com/eth-infinitism/account-abstraction/blob/cc3893bcaf2272c163ce89d5eb9eadb8e6b52db7/contracts/interfaces/IAccount.sol) and [IAccountExecute](https://github.com/eth-infinitism/account-abstraction/blob/cc3893bcaf2272c163ce89d5eb9eadb8e6b52db7/contracts/interfaces/IAccountExecute.sol) as well as implements `validateUserOp` and `executeUserOp`
- Make `executeUserOp` decode `calls[]` and forward to `execute()`
- Write `MockEntryPoint` that inherits [IEntryPoint](https://github.com/eth-infinitism/account-abstraction/blob/cc3893bcaf2272c163ce89d5eb9eadb8e6b52db7/contracts/interfaces/IEntryPoint.sol) and implements
  - `function handleOps(UserOperation[] calldata ops)`
  - For each action:
    - Call validateUserOp.
    - If ok, call executeUserOp.
- Write tests in foundry that performs three actions as described in Part A

### Part A

| ID | Behavior |
| --- | --- |
| BE-1 | Implement `BatchCallDelegation7702` `contract with struct Call { address to; uint256 value; bytes data; }` and `execute(Call[] calldata calls)` function that iterates, executes low-level calls, reverts on failure, emits an event per call, and accepts ETH. |
| BE-2 | Deploy BatchCallDelegation7702 to a testnet (Hoodi, Sepolia, or HoleSky). |
| BE-3 | Write a [viem.sh](http://viem.sh) script to batch execute three actions in one transaction: • Send 0.01 ETH to another account. • Transfer 100 ERC20 tokens to another address (deploy ERC20 & approve first). • Transfer 100 ERC20 tokens to another address (deploy ERC20 & approve first). • Call increment() of Counter contract twice (deploy simple Counter contract first). |
| BE-4 | Add Etherscan transaction URL of successful batch execution to README. |
| BE-5 | Write Foundry tests covering the above three actions via BatchCallDelegation7702. |

### Part B

| ID | Behavior |
| --- | --- |
| BA-1 | Implement `BatchCallDelegation4337` contract that inherits `BatchCallDelegation7702`, `IAccount`, and `IAccountExecute`; implement `validateUserOp` and `executeUserOp`. `executeUserOp` decodes `calls[]` and forwards to `execute().` |
| BA-2 | Implement `MockEntryPoint` contract that inherits `IEntryPoint` and implements `handleOps(UserOperation[] calldata ops);` for each action, call `validateUserOp` and then `executeUserOp`. |
| BA-3 | Write Foundry tests performing the same three actions (ETH transfer, ERC20 transfer, Counter increment) via `BatchCallDelegation4337` through `MockEntryPoint`. |
