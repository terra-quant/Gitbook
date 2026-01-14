---
description: >-
  The Xhavic testnet provides a safe environment for developers to test
  contracts, bridges, and dApp integrations on Xhavic without using real assets.
---

# Testnet

### Xhavic Bridge (Testnet)

The **Xhavic Testnet Bridge** allows developers to transfer ETH between **Ethereum** and **Xhavic**.\
This bridge is intended for testing purposes only and supports bidirectional ETH transfers.\
<br>

### Bridging ETH to and from Xhavic

To bridge ETH between Ethereum and Xhavic:

1. Visit the **Xhavic Bridge**
2. Click **Connect Wallet**
3. Connect an Ethereum-compatible wallet (e.g., MetaMask)
4. Select the amount of ETH (or any supported testnet asset) to deposit or withdraw
5. Confirm the transaction in your wallet

## Portal Proxy Contract[​](https://docs.base.org/tools/bridges-testnet#portal-proxy-contract) <a href="#portal-proxy-contract" id="portal-proxy-contract"></a>

You can bridge ETH from Ethereum to Xhavic by sending ETH to the following contract address:

0x9efd6ea3d18dee98698150c7df369fcd2efea3be

### Important behavior (ETH deposits)

By default, bridging ETH will result in a **SELF transaction on Xhavic (L2)**, where:

* The sender and recipient addresses on L2 are the same as the sender address on L1
* The L2 nonce of that address is incremented

If you are bridging ETH for the purpose of a **deterministic contract deployment** that requires a **zero L2 nonce**, you should:

1. Bridge ETH using a different address
2. Transfer ETH to the deployment address on Xhavic after the bridge completes

***

#### ⚠️ Caution

Do **not** send any asset other than **ETH** to the Portal Proxy Contract.\
The contract does **not** support ERC-20 or other asset types, and sending unsupported assets will result in **permanent and unrecoverable loss**.

