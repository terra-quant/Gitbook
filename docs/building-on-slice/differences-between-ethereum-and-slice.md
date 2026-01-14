# Differences between Ethereum and Xhavic (Ethereum compatibility notes)

Xhavic is built on the **Bedrock release of the OP Stack**, which is designed to closely match Ethereum’s execution environment. As a result, most Ethereum-based tooling, contracts, and development workflows work on Xhavic with little or no modification.

However, there are a few **important differences** between Ethereum and Xhavic that developers should be aware of when building and deploying applications.

***

#### The following differences are high-level categories. Detailed behavior may vary depending on the OP Stack configuration and network upgrades.

* **Opcodes**
* **Block production and timing**
* **Network specifications**
* **Transaction costs and fee mechanics**

The following differences are high-level categories. Detailed behavior may vary depending on the OP Stack configuration and network upgrades.

***

#### Opcode support

⚠️ Important\
Xhavic Mainnet and Testnet do not currently support the PUSH0 opcode introduced with the Ethereum Shanghai upgrade.

Because PUSH0 is the default compilation target for Solidity v0.8.20 and later, developers must use Solidity v0.8.19 or lower when deploying contracts to Xhavic until this opcode is fully supported.

Failing to do so may result in contract deployment failures or unexpected execution errors.

Recommended tooling configuration

To ensure compatibility when developing on Xhavic, developers should follow these guidelines:

* Solidity compiler version: v0.8.19 or lower
* EVM target: London
* Standard Ethereum tooling (Hardhat, Foundry, Remix) is supported
* Avoid assumptions about Ethereum L1 block timing and finality

These recommendations will be updated as Xhavic progresses toward full opcode parity with Ethereum.

Who is affected by these differences

Most application-level smart contracts, including DeFi, NFTs, and standard dApps, are not affected by these differences.

Developers building low-level EVM tooling, gas-optimized contracts, or opcode-dependent logic should carefully review the documented differences before deployment.

***

#### Summary

* Xhavic aims to be **Ethereum-equivalent**, but is not yet **Ethereum-identical**
* Most applications will work without changes
* Low-level or highly optimized contracts should account for the documented differences
* Compiler version selection is important until full opcode parity is achieved
