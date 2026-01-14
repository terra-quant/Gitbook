# Fees on Xhavic

Xhavic is designed to significantly reduce transaction costs compared to Ethereum while maintaining compatibility with the Ethereum execution environment.\
Transaction fees on Xhavic follow the **OP Stack fee model**, which separates execution costs on Xhavic from data availability costs on Ethereum.

***

### Fee components

A transaction fee on Xhavic is composed of two primary components:

#### 1. L2 execution fee

The **L2 execution fee** covers the cost of executing a transaction on the Xhavic network itself.\
This includes:

* EVM execution
* State reads and writes
* Contract deployment and function calls

This fee is paid in **ETH on Xhavic** and is generally much lower than executing the same transaction directly on Ethereum.

***

#### 2. L1 data fee

The **L1 data fee** covers the cost of publishing transaction data to **Ethereum L1** for security and data availability.\
This fee depends on:

* The size of the transaction calldata
* Current Ethereum gas prices

Because transaction data must ultimately be posted to Ethereum, this portion of the fee fluctuates with Ethereum network conditions.

***

### Fee calculation overview

The total transaction fee on Xhavic can be summarized as:

```
Total Fee = L2 Execution Fee + L1 Data Fee
```

While the L2 execution fee is relatively stable and low, the L1 data fee may vary based on Ethereum congestion.

***

### Gas limits and gas price

* Xhavic uses the same **gas model** as Ethereum for transaction execution
* Gas limits must be specified for transactions and contract deployments
* Gas prices on Xhavic are dynamically adjusted based on network conditions

Most Ethereum tooling (such as MetaMask, Hardhat, and Foundry) automatically estimates appropriate gas values when interacting with Xhavic.

***

### Contract deployment costs

Deploying smart contracts on Xhavic is significantly cheaper than on Ethereum L1.\
However, deployment fees are still affected by:

* Contract bytecode size
* Constructor complexity
* L1 data costs at the time of deployment

Developers deploying large or complex contracts should be aware that calldata-heavy deployments increase the L1 data fee component.

***

### Fee payments

* All fees on Xhavic are paid in **ETH**
* No separate gas token is required
* The same ETH balance is used for transactions, deployments, and contract interactions

***

### Fee estimation

Before submitting a transaction, developers can:

* Use standard Ethereum RPC methods (e.g. `eth_estimateGas`)
* Rely on wallet-based gas estimation (e.g. MetaMask)
* Simulate transactions using local development tools

Estimated fees include both L2 execution costs and L1 data costs where applicable.

***

### Fee behavior on testnet

On **Xhavic Testnet**, fees behave similarly to mainnet but use **test ETH** with no real-world value.\
Fee values on testnet should not be used as a direct benchmark for mainnet costs.

***

### Important considerations for developers

* Ethereum gas price spikes directly affect L1 data fees
* Calldata size has a measurable impact on total transaction cost
* Highly optimized calldata can reduce overall fees
* Fee mechanics may evolve as the OP Stack is upgraded
