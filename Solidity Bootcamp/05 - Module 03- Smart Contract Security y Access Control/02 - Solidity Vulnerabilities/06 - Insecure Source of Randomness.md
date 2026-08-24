# Insecure Source of Randomness

Shows what are insecure source of randomness (blockhash and block timestamp).

An example contract using insecure randomness and how to exploit it

[Video: Insecure Source of Randomness | Hack Solidity (0.6)](https://www.youtube.com/watch?v=8FF3IBTMeK0)

**Disclaimer:** In this video, ganache-cli is used as the local blockchain environment. Please note that ganache-cli is now deprecated. For modern development, it is recommended to use alternatives like **hardhat node** or **foundry anvil**.

**Transcript for the AI**

Hello everyone, in this video, we’ll explore why generating secure random numbers in Solidity is challenging, particularly when using block.hash and block.timestamp as sources of randomness, which may seem reliable but are vulnerable to exploitation. Suppose you’re building a program, like a lottery, that requires randomness to pick a winner. In languages like JavaScript or Python, generating random numbers is straightforward, but in Solidity, it’s extremely difficult. I’ll explain why block.hash and block.timestamp are not secure for randomness, walk through a vulnerable contract, demonstrate an exploit in Remix, and highlight the key lesson. Consider a contract called GuessTheRandomNumber, where guessing the correct random number rewards you with 1 ETH. The guess function generates a random number by hashing the previous block’s hash (blockhash(block.number – 1)) and the current block’s timestamp (block.timestamp) using a cryptographic hash function, then converting the result to a uint. If your guess matches this number, you win 1 ETH. At first glance, these variables seem random: block.timestamp reflects the future time when the transaction is included in a block, unknown when you call guess, and block.hash produces a hard-to-predict hash of the previous block’s data. Since the current block’s hash (blockhash(block.number)) depends on the block’s transactions, including the one executing guess, it’s unavailable during execution, so the contract uses the previous block’s hash.

However, these variables are easily accessible to other smart contracts, making them exploitable. To demonstrate, we create an Attack contract that targets GuessTheRandomNumber. It takes the target contract’s address as input, computes the random number using the same formula (blockhash(block.number – 1) and block.timestamp), and calls guess with the result. The key insight is that when Eve calls Attack’s attack function, both the attack and guess functions execute in the same block, so they use the same block.timestamp and blockhash(block.number – 1). This ensures the computed number in Attack matches the one in GuessTheRandomNumber, guaranteeing a win every time. The Attack contract includes a payable fallback function to receive the 1 ETH reward and a helper function to check its balance. To test this in Remix, we need a local blockchain because Remix’s JavaScript VM doesn’t support blockhash. We install Ganache CLI (npm i ganache-cli), run it (ganache-cli) on localhost:8545, and configure Remix to use the Web3 provider at this URL. Alice deploys GuessTheRandomNumber with 1 ETH, and Eve deploys Attack with the game contract’s address. Normally, guessing the number has a 1 in 2^256 chance, but Eve calls Attack’s attack function, which computes the correct number and wins 1 ETH, confirmed by checking Attack’s balance (1 ETH) and the game contract’s balance (0 ETH).

This exploit shows that block.hash and block.timestamp, despite appearing random, are predictable within the same block by another contract. The lesson is that achieving secure randomness in smart contracts is difficult, and these variables are not safe sources. Thanks for watching, and see you later!

## Links

- [Insecure Source of Randomness | Hack Solidity (0.6)](https://www.youtube.com/watch?v=8FF3IBTMeK0)
