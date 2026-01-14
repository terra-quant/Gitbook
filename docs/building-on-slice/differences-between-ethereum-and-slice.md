# Differences between Ethereum and Xhavic

Xhavic is built on the **Bedrock release of the OP Stack**, which is designed to closely match Ethereum’s execution environment. As a result, most Ethereum-based tooling, contracts, and development workflows work on Xhavic with little or no modification.

However, there are a few **important differences** between Ethereum and Xhavic that developers should be aware of when building and deploying applications.

***

#### Key differences

The primary differences between Ethereum and Xhavic include:

* **Opcodes**
* **Block production and timing**
* **Network specifications**
* **Transaction costs and fee mechanics**

Each of these differences may affect low-level behavior, gas estimation, or assumptions made by advanced smart contracts and tooling.

***

#### Opcode support

> **Important**

Xhavic Mainnet and Testnet do **not currently support the `PUSH0` opcode** introduced with the Ethereum Shanghai upgrade.

Because `PUSH0` is the default compilation target for **Solidity v0.8.20 and later**, developers should use **Solidity v0.8.19 or lower** when deploying contracts to Xhavic until this opcode is fully supported.

Failing to do so may result in deployment or execution errors.

***

#### Summary

* Xhavic aims to be **Ethereum-equivalent**, but is not yet **Ethereum-identical**
* Most applications will work without changes
* Low-level or highly optimized contracts should account for the documented differences
* Compiler version selection is important until full opcode parity is achieved
