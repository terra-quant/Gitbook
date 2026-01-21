---
description: >-
  The Xhavic Bridge securely enables bidirectional asset transfers between
  Ethereum and Xhavic with full EVM compatibility.
---

# Bridge

#### Supported assets

The Xhavic Bridge supports ERC-20 tokens that are compatible with the Xhavic Standard Bridge.

Supported assets include:

* ETH
* ERC-20 tokens deployed using the OptimismMintableERC20 standard
* Tokens listed in the official Xhavic Token List

Only reviewed and approved tokens are enabled by default on the Xhavic Bridge.

***

#### Bridge architecture

Xhavic Bridge is built on the OP Stack Standard Bridge architecture.

This design uses:

* Canonical L1 and L2 bridge contracts
* Mint and burn mechanics for ERC-20 representations
* A fraud-proof-based withdrawal system

This ensures compatibility with Optimism tooling and long-term support across the Superchain ecosystem.

***

#### Transfers are typically completed within a few minutes

* **Ethereum → Xhavic** \
  Deposits are typically completed within a few minutes, though finality is not guaranteed and depends on Ethereum network conditions.<br>
* **Xhavic → Ethereum:**\
  Withdrawals require two transactions — one to initiate the withdrawal on Xhavic and one to finalize it on Ethereum after the challenge period.

Developers and users who require faster withdrawals may choose to use **third-party bridges**, which provide shorter finality times at their own risk.

***

#### Withdrawing assets from Xhavic

Limitations

* Withdrawals from Xhavic to Ethereum are not instant due to the challenge period
* Third-party bridges may introduce additional trust assumptions
* Users are responsible for verifying official bridge URLs and contracts

***

#### Fees

Using the Xhavic Bridge requires paying standard **network gas fees** on:

* Ethereum
* Xhavic

Xhavic does **not charge additional protocol-level fees** for bridge usage beyond normal network costs.

***

#### Benefits of bridging to Xhavic

By bridging assets from Ethereum to Xhavic, users and developers gain access to:

* Lower transaction costs
* Faster transaction execution
* Scalable infrastructure
* dApps and protocols deployed natively on Xhavic

***

#### dApp interaction

Once assets are bridged to Xhavic, they can be used to interact with **all dApps deployed on the Xhavic network**, including DeFi protocols, NFTs, and other smart contracts.

***

#### Security considerations

While Xhavic Bridge is designed with security as a priority, all blockchain transactions involve inherent risk.\
Users and developers should:

* Verify contract addresses
* Understand bridge mechanics
* Follow standard security best practices

***

#### Support

For questions, issues, or developer support, visit the **Xhavic Discord community**, where assistance is available from the team and community members.
