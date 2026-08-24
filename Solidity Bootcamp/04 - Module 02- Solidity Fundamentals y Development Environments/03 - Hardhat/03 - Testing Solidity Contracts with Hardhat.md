# Testing Solidity Contracts with Hardhat

This tutorial demonstrates how to test smart contracts using Hardhat, a leading IDE for smart contract development and testing. Mastering Hardhat and writing thorough tests is essential for becoming an advanced blockchain developer and ensuring your contracts are reliable.

[Video: How to test your Solidity Smart Contracts with Hardhat using Javascript, Mocha, and Chai libraries.](https://www.youtube.com/watch?v=uF-lA8dDE3o)

**Transcript for the AI**

In this tutorial, we are testing a basic ERC20 token smart contract licensed under the MIT License. The contract is compiled using Solidity version 0.8.22 and imports two key OpenZeppelin libraries: ERC20 and Ownable. The contract is named Token, and it inherits from both imported libraries. It defines a maximum supply of one million tokens, each with 18 decimal places, which is the standard for ERC20 tokens. The contract includes an event to log minting actions, capturing the minter’s address, the receiver, and the amount of tokens minted.

The constructor takes the token’s name and symbol as parameters. It initializes both the Ownable and ERC20 contracts. A mint function is implemented that allows only the contract owner to mint new tokens. This function takes the receiver’s address and the amount to mint. It includes a check to ensure the total supply after minting does not exceed the maximum supply. Upon successful execution, it mints the tokens and emits the defined event.

When testing this contract using Remix, we initialize the token by providing its name and symbol (e.g., “MyToken” and “MTK”) and deploy it. We can then interact with various functions—checking decimals (returns 18), name, owner, symbol, and total supply (initially zero). For more complex interactions, such as minting and transferring, we simulate minting 1,000 tokens to a secondary address, switching to a new account, and transferring half of the tokens back. However, any redeployment resets the state, losing all prior interactions. To address this, we shift to Hardhat for more robust and automated testing.

Welcome to Dapp Dojo! If you find this content helpful, please like, subscribe, and click the bell icon. To learn more, visit courses.doo.com and check out the “Mastering Web3, Bitcoin and Blockchain” course—currently free with a 100% off coupon. This course is ideal for beginners and blockchain enthusiasts aiming to deepen their understanding of Ethereum, smart contracts, and Web3 development.

Moving into the Hardhat environment, if you need guidance on installation and setup, refer to our previous video. For this test, we copied the token contract file into the Hardhat project and installed the OpenZeppelin libraries. We created a Token.js test file inside the test directory. The test uses fixtures to initialize and reuse the same state across multiple tests. We import network helpers and use Chai for assertions.

Within the fixture setup, we define key constants such as ZERO, ONE, ONE\_MILLION, and the zero address. We use ethers.getSigners() to create three accounts: the owner, a sender, and a receiver. Then we deploy the contract using ethers.getContractFactory(“Token”) and mint one token (1 ether unit with 18 decimals) to the sender. We assert that this operation does not revert, confirming the contract logic is valid for the owner.

In the first test suite, we validate that the deployment sets the correct owner. Using asynchronous calls with await, we retrieve and assert the deployed owner matches the expected signer. We then test balances: the owner’s balance should be zero, and the sender’s balance should be one token. These assertions confirm the contract state matches expectations after minting.

Next, we verify that minting more than the max supply fails. Since we already minted one token, trying to mint another one million should revert with the message “Max supply reached.” Similarly, minting to the zero address should fail, as should minting zero tokens. We added require validations in the contract to enforce these rules, ensuring better security and predictable behavior.

We then ensure that only the owner can mint tokens. Attempting to mint from a non-owner address triggers a custom OpenZeppelin error, OwnableUnauthorizedAccount, which we assert using .to.be.revertedWithCustomError(). This confirms that the onlyOwner modifier is correctly enforced.

Further, we test that the Mint event is emitted correctly when tokens are minted, asserting that the event includes the proper owner, recipient, and amount values. We also validate the transfer function by sending one token from the sender to the receiver and checking that balances are updated accordingly using changeTokenBalances().

In another example, we demonstrate how to test ether transfers using changeEtherBalances() to ensure ether values are correctly subtracted from the sender and added to the receiver. This method is useful for verifying ETH payments and balances during contract execution.

To test allowances and approvals, we begin by attempting a transferFrom() without prior approval, which should fail. Then we approve the owner to spend on behalf of the sender and validate a successful transfer. The balances of the sender and receiver update correctly, confirming that allowance logic is working as expected.

Throughout these tests, we apply a variety of techniques, each targeting a specific aspect of contract behavior. Whether testing deployment, minting restrictions, event emissions, token transfers, ether transactions, or approval mechanisms, each test ensures that the smart contract behaves reliably and securely. Given the financial implications of smart contracts, thorough and well-structured testing is essential. Thank you for following along with Dapp Dojo, and we encourage you to take the time to write comprehensive tests for your own contracts.

## Links

- [How to test your Solidity Smart Contracts with Hardhat using Javascript, Mocha, and Chai libraries.](https://www.youtube.com/watch?v=uF-lA8dDE3o)
