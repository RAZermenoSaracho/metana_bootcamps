# Master Hardhat in Minutes

This tutorial covers setting up Hardhat, running a local Ethereum blockchain, compiling and deploying smart contracts, interacting with them, and writing automated tests—all while showing why Hardhat is a more powerful alternative to Remix.

[Video: Master Hardhat in MINUTES | The Best Solidity Dev Tool Explained](https://www.youtube.com/watch?v=rxK3UXld8xY)

**Transcript for the AI**

Welcome back to Crypto University! If you’re diving into Solidity smart contract development, it’s essential to understand Hardhat—a powerful framework for building, testing, and deploying smart contracts. Unlike Remix, which we covered in earlier videos, Hardhat provides a complete development environment with greater flexibility. It allows you to compile contracts, spin up local Ethereum nodes, run unit tests, and deploy contracts to real or test networks.

To get started, make sure you have Visual Studio Code (VS Code) and Node.js installed. You can check if Node.js is installed by running `node -v` in your terminal. If not, download and install it from the official site. Next, create a new folder for your project—for example, `my-first-hardhat-project`—and initialize a Node.js project inside it by running `npm init -y`. Then, install Hardhat using the command `npm install --save-dev hardhat`. Once installed, run `npx hardhat init` and select “Create a TypeScript project” when prompted. Accept the default structure and let it install the Hardhat Toolbox.

After setup, you’ll see a few key folders in your project. The `contracts` folder contains a sample contract called `Lock.sol`, which locks ETH until a specified unlock time. The `ignition/modules` folder includes `Lock.ts`, which defines how the contract is deployed—including arguments like `unlockTime` and `lockedAmount`. You’ll also have a `test` folder with TypeScript unit tests to verify that the contract behaves correctly. Additionally, you’ll notice standard files like `package.json` and a `node_modules` directory for dependencies.

To test your contract, first run `npx hardhat node` to start a local blockchain. Then, in another terminal window, deploy your contract by running `npx hardhat ignition deploy ./ignition/modules/Lock.ts --network localhost`. After deployment, you’ll get a contract address. You can interact with the contract by launching the Hardhat console with `npx hardhat console --network localhost`. Inside the console, use ethers.js to load your deployed contract like this: `const Lock = await ethers.getContractFactory("Lock"); const lock = await Lock.attach("DEPLOYED_CONTRACT_ADDRESS");`. Now you can call contract methods, such as `await lock.unlockTime()` or `await lock.owner()`.

Finally, to run unit tests and confirm your contract works as expected, simply execute `npx hardhat test`. The test suite will validate things like whether the unlock time is set correctly and whether the contract owner is the expected address.

That’s it—you’ve now created a full Hardhat project, deployed a Solidity contract to a local blockchain, interacted with it, and verified it with tests. Keep experimenting and building, and stay tuned for more tutorials from Crypto University!

## Links

- [Master Hardhat in MINUTES | The Best Solidity Dev Tool Explained](https://www.youtube.com/watch?v=rxK3UXld8xY)
