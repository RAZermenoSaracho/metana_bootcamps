# 📑 Assignment M13

### Tokenizing Real-World Assets with Chainlink Oracles

Build a smart contract that represents a real-world asset on-chain (such as gold, real estate, or stocks), and use Chainlink Price Feeds to fetch the real-time price of that asset from the external world.

You are tasked with building a smart contract that does the following:

1. Tokenizes a real-world asset (e.g., Gold, AAPL stock, or ETH).
   - You can use a basic ERC20-like structure.
   - For example, 1 token = 1 ounce of gold or 1 share of a stock.
2. Fetches the current real-world price of the asset using a Chainlink Oracle.
   - Use Chainlink Price Feeds (e.g., XAU/USD for gold or ETH/USD for Ethereum).
   - You can use the testnet addresses from Chainlink docs.
3. Includes a function to display the current asset price in USD, fetched live from Chainlink.
   - Includes a minting condition — for example:
   - Allow users to mint tokens only if the asset price is below a certain threshold.
   - Or dynamically price the token mint cost based on current value.
4. Implement an “oracle trigger”:
   - Use Chainlink Automation or a simple time check to update the price every X minutes
   - Add a priceHistory array to track price changes over time

**Capstone Task:** Implement oracles for the capstone project, if applicable.
