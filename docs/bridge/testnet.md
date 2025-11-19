# Testnet

## Xhavic Bridge (Testnet)[​](https://docs.base.org/tools/bridges-testnet#base-bridge-testnet) <a href="#base-bridge-testnet" id="base-bridge-testnet"></a>

The [Xhavic Bridge](https://xhavicledger.io/bridge/deposit/) for testnet allows you to bridge ETH from Ethereum Goerli to Xhavic Goerli and vice versa.

To bridge to or from Xhavic Goerli:

1. Visit [Xhavic Bridge](https://xhavicledger.io/bridge/deposit/)
2. Click **Connect wallet**
3. Connect your wallet
4. Choose the amount of ETH (or the asset of your choice that's available) you'd like to deposit or withdraw

## Portal Proxy Contract[​](https://docs.base.org/tools/bridges-testnet#portal-proxy-contract) <a href="#portal-proxy-contract" id="portal-proxy-contract"></a>

You can bridge ETH from Ethereum Goerli to Xhavic Goerli by sending Goerli ETH to the following contract address:

[0xE1BD4bc68917a3e6F266d5ae77C3f8994f28E825](https://goerli.etherscan.io/address/0xe1bd4bc68917a3e6f266d5ae77c3f8994f28e825)

{% hint style="info" %}
INFO

By default, bridging ETH will result in a `SELF` transaction on the L2, with the `from` and `to` addresses equal to the address performing the bridge on the L1. This will also increase that address' L2 nonce. **If you are bridging for the purpose of a deterministic contract deploy that depends on a zero nonce, please bridge using a different address first, and transfer to the contract deployment address on the L2 after bridging.**
{% endhint %}

{% hint style="warning" %}
CAUTION

**Do not send any asset other than ETH to the portal proxy contract.** The proxy contract only supports receipt of ETH and sending any other asset will result in unrecoverable loss of the asset.
{% endhint %}

