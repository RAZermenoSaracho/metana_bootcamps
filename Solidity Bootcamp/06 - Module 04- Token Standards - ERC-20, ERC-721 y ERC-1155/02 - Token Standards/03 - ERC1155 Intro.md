# ERC1155 Intro

Provides an introduction to the ERC-1155 multi-token standard. Explains the motivation for ERC1155 (which can handle multiple token types in one contract, both fungible and non-fungible) and prepares the viewer for implementing or understanding an ERC1155 by outlining how it works at a high level.

[Video: ERC1155 Intro](https://www.youtube.com/watch?v=Ai7A-_umm08)

**Transcript for the AI**

Our ERC-1155 contract is designed to manage multiple tokens within a single contract. To illustrate this, let’s compare a contract managing multiple ERC-20 tokens with an ERC-1155 contract that also handles multiple tokens in a single contract, using Uniswap V3 and Uniswap V4 as examples. In Uniswap V3, suppose I want to swap DAI for WETH, and for simplicity, we assume there are only two pools: a DAI/USDC pool and a USDC/WETH pool. To perform this swap, I would first transfer my DAI into the DAI/USDC pool to receive USDC, then transfer that USDC to the USDC/WETH pool to trade for WETH, ultimately receiving WETH. This process involves multiple token transfers across different pools, characteristic of how Uniswap V3 handles ERC-20 token swaps. Now, let’s examine Uniswap V4, which operates as an ERC-1155 contract.

As mentioned, an ERC-1155 contract can manage multiple tokens within a single contract. In this case, both the DAI/USDC pool and the USDC/WETH pool are contained within the same Uniswap V4 contract. This allows token transfers to occur internally, reducing gas costs compared to Uniswap V3. For example, if a user wants to swap DAI for WETH in Uniswap V4, they transfer DAI into the Uniswap V4 contract. Unlike Uniswap V3, where tokens move in and out of separate pools, here the transfer from DAI to USDC happens internally within the contract, followed by an internal trade from USDC to WETH. Finally, the user receives WETH. The key difference between Uniswap V3 and V4 is that V3 relies on multiple external token transfers across different pools, while in V4, all token transfers are managed internally within the ERC-1155 contract, making the process more gas-efficient.

## Links

- [ERC1155 Intro](https://www.youtube.com/watch?v=Ai7A-_umm08)
