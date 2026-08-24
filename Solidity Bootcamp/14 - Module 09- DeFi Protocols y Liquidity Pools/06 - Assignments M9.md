# 📑 Assignments M9

In this assignment, you will implement a complete DeFi system with three core components:

### Deposit Contract

Users deposit an ERC-20 token called **Metana (MTN)** to receive a 1:1 wrapped token, **wMTN**. The deposit contract will have a way to notify and sync the newly added rewards to be streamed over time. It will require a function to be only called by deposit contract on the ERC4626 vault.

| ID | Behavior |
| --- | --- |
| DF-1 | Accept deposits of MTN tokens and mint wMTN at 1:1 ratio. |
| DF-2 | Sync newly added rewards for streaming over time. |
| DF-3 | Notify the ERC-4626 vault of deposited assets. |
| DF-4 | Restrict certain functions to only be callable by the deposit contract. |
| DF-5 | Track total MTN deposited and wMTN minted. |
| DF-6 | Emit events on deposit, withdrawal, and reward sync. |

- Deploy a simple ERC20 token contract that has mint functionality with name METANA and Symbol MTN
- Deploy a simple ERC20 token contract that has mint and burn functionality accessed by `MINTER_ROLE` and `BURNER_ROLE` with name Wrapped METANA and Symbol wMTN. The mint and burn rights will be with deposit contract.
- Deposit contract’s constructor will have arguments for underlying token (MTN), staking contract address for MTN and address for autocompounding vault
- User deposits MTN token to deposit contract via deposit(`address _receiver, bool _compound`) function. The deposit function will stake MTN into MTN staking contract.
  - Deposit function will mint wMTN 1:1 to the `_receiver` address if `_compound` is false
  - Deposit function will deposit wMTN to autocompounding vault such that \_receiver gets aMTN if `_compound` is true
- The deposit contract will have a `harvest()` function to claim the MTN rewards from staking contract and re-stake into staking contract.
  - The harvest function will mint wMTN tokens to the autocompounding vault
  - The harvest function will also call `notifyRewardAmount()` on autocompounding vault
- User can redeem with wMTN using redeem(`uint256 _assets, address _receiver`) function where `_assets` is the amount of wMTN to redeem and `_receiver` is the beneficiary address to receive MTN.
  - The redeem function will have to withdraw required MTN from staking contract
  - It will burn assets worth of wMTN and transfer MTN to the `_receiver` address

### Autocompounding Vault for wMTN

Users stake their wMTN into a standardized ERC-4626 vault to receive aMTN. The vault mints vault shares to represent each user’s proportional claim on the strategy. (Note that, in order to take the advantage of yield earned by deposit contract, wMTN holder needs to stake in autocompounding vault)

| ID | Behavior |
| --- | --- |
| DF-7 | Accept deposits of wMTN and mint proportional aMTN shares. |
| DF-8 | Calculate the user’s proportional share of total assets. |
| DF-9 | Periodically harvest yield generated from underlying assets. |
| DF-10 | Increase total assets backing aMTN as yield is harvested. |
| DF-11 | Allow withdrawals of aMTN for underlying wMTN. |
| DF-12 | Emit events on deposit, withdrawal, and yield harvest. |

- This contract inherits **ERC4626** (<https://github.com/transmissions11/solmate/blob/main/src/tokens/ERC4626.sol>).
- Add `notifyRewardAmount()` only callable by Deposit contract.
  - This function is used to start a new reward period by calculating how much reward is available and setting the reward rate.
  - It calculates the new reward amount by subtracting:
    - The currently staked tokens (`totalStaked`), and
    - The already-earned rewards (`earned()`) from the total token balance held by the contract.
    - This ensures it only considers newly deposited tokens meant for rewards.
  - It then sets the rewardRate based on a fixed `REWARDS_DURATION`.
  - Finally, it updates the timestamps and emits a RewardAdded event.
- Internal method called `_stake(uint256 amount)` to keep track of the total amount of staked token/asset on deposit/mint. It will increment global variable totalStaked by amount
- Internal method called `_withdrawInternal(uint256 amount)` to keep track of the total amount of staked token/asset on withdrawal/redeem. It will decrement totalStaked by amount
- `harvest()` function to claim and stake available rewards. Don’t confuse claim and stake here with MTN staking contract. They both are different.
- `earned()` should return earned rewards so far by the vault
- `rewardPerToken()` should return amount of rewards per staked token/asset
- `totalAssets()` should return the amount of available MTN in the contract. Rewards are streamed for the duration set in `REWARDS_DURATION`

### MTN staking contract

- **Single Token Staking**
  - Users stake a single MTN.
  - Rewards are also paid out in the MTN token\*\*.\*\*
  - You must track user balances and total supply of staked tokens.

**Reward Distribution Logic**

- A fixed rewardRate determines how much token is distributed per second.
- Rewards are calculated proportionally based on how much and how long each user stakes.
- Use the Synthetix-style reward per token formula:

`rewardPerTokenStored + (lastTimeRewardApplicable() - lastUpdateTime) * rewardRate / totalSupply`

**For each user, track:**

`rewards[account] += balanceOf(account) * (rewardPerToken - userRewardPerTokenPaid[account]) / 1e18`

### Core Functions

- Implement these public/external functions:
  - `stake(uint256 amount)` : Stake tokens and start earning rewards.
  - `withdraw(uint256 amount)` : Withdraw staked tokens (but not rewards).
  - `getReward()` : Claim accumulated rewards (paid in the same token).
  - `exit()` : Withdraw all staked tokens and claim all rewards.
  - `earned(address account) (view)` : Returns how much reward a user has earned.

### Admin Functions

- `notifyRewardAmount(uint256 reward)` — Called to fund the reward pool and set reward parameters (e.g., duration).
- Must require that the contract holds enough tokens to cover the reward.

### Events

- Emit the following events:
  - `Staked(address indexed user, uint256 amount)`
  - `Withdrawn(address indexed user, uint256 amount)`
  - `RewardPaid(address indexed user, uint256 reward)`
  - `RewardAdded(uint256 reward)`

### Users benefit from:

- Holding wMTN (the wrapped version of Metana)
- Earning yield through aMTN (vault shares)

### CTF Challenges:

- **[Ethernaut](https://ethernaut.openzeppelin.com/)**
  - Ethernaut 9
  - Ethernaut 22
  - Ethernaut 23
- **Damn Vulnerable Defi**
  - [Free Rider](https://www.damnvulnerabledefi.xyz/challenges/free-rider/)
  - [Selfie](https://www.damnvulnerabledefi.xyz/challenges/selfie/)
- **Secureum**
  - [LendingPool](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/3_LendingPool)
  - [BalloonVault](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/5_balloon-vault)
  - [YieldPool](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/6_yieldPool)
  - [Liquidatooor](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/8_oiler)
  - [RescueToken](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/4_RescuePosi) (Optional)
