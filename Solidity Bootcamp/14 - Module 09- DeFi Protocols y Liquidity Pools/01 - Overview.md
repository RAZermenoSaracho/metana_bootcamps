# 🎯 Overview

## Module 09 – DeFi Protocols & Liquidity Pools

## Learning Objectives

- Understand the mechanics of token swapping, peer-to-peer lending and borrowing, and vault-based yield strategies in DeFi ecosystems.
- Learn how to design, manage, and interact with various token types and smart contract components to facilitate secure and efficient DeFi operations.

## Lectures / Lessons

**Swapping**

- [Liquidity Providers](https://www.youtube.com/watch?v=8-Jd1CYpBGk)
- [Constant Product AMM Math](https://www.youtube.com/watch?v=QNPyFs8Wybk)
- [Constant Product AMM](https://www.youtube.com/watch?v=JSZbvmyi_LE)
- [Add Liquidity in Uniswap V2](https://www.youtube.com/watch?v=816kTTNzcHs)
- [Swap Tokens in Uniswap V2](https://www.youtube.com/watch?v=qB2Ulx201wY)
- [Incentives for LPs](https://docs.uniswap.org/contracts/v2/concepts/advanced-topics/understanding-returns)
- [LPing and swapping fees](https://docs.uniswap.org/contracts/v2/concepts/advanced-topics/fees)
- [Slippage and Impermanent Loss](https://www.youtube.com/watch?v=A36vnzXDl98)

**Peer to Peer Borrow and Lend**

- [Lending and Borrowing in DeFi](https://www.youtube.com/watch?v=aTp9er6S73M)
- [DEFI Pooled lending](https://www.youtube.com/watch?v=utv1Qgln388)
- [Compound – Deposit and withdraw](https://www.youtube.com/watch?v=dHKLcbqFzvE)
- [Compound – Borrow and Repay](https://www.youtube.com/watch?v=d9_ZEvLDSl8)
- [Compound – Liquidation](https://www.youtube.com/watch?v=w-oVV0Ie3Fw)
- [Compound – Long and short](https://www.youtube.com/watch?v=pl6iNIL72kY)
- [Aave – Flash Loan](https://www.youtube.com/watch?v=_GZHt-FVAQs)

**Vaults**

- [Vault Math](https://www.youtube.com/watch?v=k7WNibJOBXE)
- [Vault](https://www.youtube.com/watch?v=HHoa0c3AOqo)
- [ERC4626 Vault](https://www.youtube.com/watch?v=ftfsCxG1560)

**Tokens**

- [Rebasing tokens](https://www.youtube.com/watch?v=omWpeh8ZKmU)
- [How does Ampleforth work?](https://docs.ampleforth.org/learn/about-the-ampleforth-protocol)
- [Tokens in Olympus DAO](https://docs.olympusdao.finance/main/contracts-old/tokens/#sohm)
- [Synthetix Staking Rewards Contract Explained – Part 0](https://www.youtube.com/watch?v=6ZO5aYg1GI8)
- [Synthetix Staking Rewards Contract Explained – Part 1](https://www.youtube.com/watch?v=LWWsjw3cgDk)
- [Synthetix Staking Rewards Contract Explained – Part 2](https://www.youtube.com/watch?v=YqpRwJDz3xg)
- [Synthetix Staking Rewards Contract Explained – Part 3](https://www.youtube.com/watch?v=pFX1-kNrJFU)
- [Token Bonding curve](https://www.youtube.com/watch?v=sLD_jFUFMqA)
- [Solidity Bonding Curves & Dynamic Token Pricing Explained](https://speedrunethereum.com/guides/solidity-bonding-curves-token-pricing)

## Timestamp

**Swapping**

- Liquidity Providers – 1:57
- Constant Product AMM Math – 25:40
- Constant Product AMM – 30:00
- Add Liquidity in Uniswap V2 – 10:14
- Swap Tokens in Uniswap V2 – 9:20
- Slippage and Impermanent Loss – 29:09

**Peer to Peer Borrow and Lend**

- Lending and Borrowing in DeFi – 13:32
- DEFI Pooled lending – 19:24
- Compound – Deposit and withdraw – 10:18
- Compound – Borrow and Repay – 11:09
- Compound – Liquidation – 8:42
- Compound – Long and short – 13:43
- Aave – Flash Loan – 8:06

**Vaults**

- Vault Math – 8:25
- Vault – 11:06
- ERC4626 Vault – 1:05:36

**Tokens**

- Rebasing tokens – 5:15
- Synthetix Staking Rewards Contract Explained – Part 0 – 7:36
- Synthetix Staking Rewards Contract Explained – Part 1 – 3:40
- Synthetix Staking Rewards Contract Explained – Part 2 – 6:53
- Synthetix Staking Rewards Contract Explained – Part 3 – 5:22
- Token Bonding curve – 43:42

Total Time: 5 hours 48 minutes 49 seconds

## Assignment

In this assignment, you will implement a complete DeFi system with three core components:

### Deposit Contract

Users deposit an ERC-20 token called **Metana (MTN)** to receive a 1:1 wrapped token, **wMTN**. The deposit contract will have a way to notify and sync the newly added rewards to be streamed over time. It will require a function to be only called by deposit contract on the ERC4626 vault.

### Autocompounding Vault for wMTN

Users stake their wMTN into a standardized ERC-4626 vault to receive aMTN. The vault mints vault shares to represent each user’s proportional claim on the strategy. (Note that, in order to take the advantage of yield earned by deposit contract, wMTN holder needs to stake in autocompounding vault)

### Lending Protocol

The vault deploys the underlying MTN tokens into a custom lending protocol. As the protocol generates interest over time, the vault periodically harvests yield, increasing the total assets backing the vault shares.

### CTF Challenges

- **Ethernaut**
  - Ethernaut 9
  - Ethernaut 22
  - Ethernaut 23

- **Damn Vulnerable Defi**
  - Free Rider
  - Selfie

- **Secureum**
  - [LendingPool](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/3_LendingPool)
  - [BalloonVault](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/5_balloon-vault)
  - [YieldPool](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/6_yieldPool)
  - [Liquidatooor](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/8_oiler)
  - [RescueToken](https://github.com/secureum/AMAZEX-DSS-PARIS/tree/main/src/4_RescuePosi) (Optional)
