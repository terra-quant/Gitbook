# ethers.js

[ethers.js](https://docs.ethers.org/v5/) is a JavaScript library that allows developers to interact with EVM-compatible blockchain networks.

You can use ethers.js to interact with smart contracts deployed on the Slice network.

***

## Install[​](https://docs.base.org/tools/ethers#install) <a href="#install" id="install"></a>

To install ethers.js run the following command:

```css
npm install --save ethers
```

## Setup[​](https://docs.base.org/tools/ethers#setup) <a href="#setup" id="setup"></a>

Before you can start using ethers.js, you need to import it into your project.

Add the following line of code to the top of your file to import ethers.js:

```css
const ethers = require('ethers');
```

## Connecting to Xhavic[​](https://docs.base.org/tools/ethers#connecting-to-base) <a href="#connecting-to-base" id="connecting-to-base"></a>

You can connect to Xhavic by instantiating a new ethers.js `JsonRpcProvider` object with a RPC URL of the Xhavic network:

```css
const ethers = require('ethers');

const url = 'https://testrpc.sliceledger.io/';
const provider = new ethers.providers.JsonRpcProvider(url);
```

## Reading data from the blockchain[​](https://docs.base.org/tools/ethers#reading-data-from-the-blockchain) <a href="#reading-data-from-the-blockchain" id="reading-data-from-the-blockchain"></a>

Once you have created a provider, you can use it to read data from the Slice network.

For example, you can use the `getBlockNumber` method to get the latest block:

```css
async function getLatestBlock() {
  const latestBlock = await provider.getBlockNumber();
  console.log(latestBlock);
}
```

## Writing data to the blockchain[​](https://docs.base.org/tools/ethers#writing-data-to-the-blockchain) <a href="#writing-data-to-the-blockchain" id="writing-data-to-the-blockchain"></a>

In order to write data to the Xhavic network, you need to create a `Signer`.

You can create a `Signer` by instantiating a new ethers.js `Wallet` object, providing it with a private key and `Provider`.

```css
const privateKey = 'PRIVATE_KEY';
const signer = new ethers.Wallet(privateKey, provider);
```

{% hint style="info" %}
INFO

`PRIVATE_KEY` is the private key of the wallet to use when creating the signer.
{% endhint %}

## Interacting with smart contracts[​](https://docs.base.org/tools/ethers#interacting-with-smart-contracts) <a href="#interacting-with-smart-contracts" id="interacting-with-smart-contracts"></a>

You can use ethers.js to interact with a smart contract on Slice by instantiating a `Contract` object using the ABI and address of a deployed contract:

```css
const abi = [
… // ABI of deployed contract
];

const contractAddress = "CONTRACT_ADDRESS"

// read only
const contract = new ethers.Contract(contractAddress, abi, provider);
```

For write-only contracts, provide a `Signer` object instead of a `Provider` object:

```css
// write only
const contract = new ethers.Contract(contractAddress, abi, signer);
```

{% hint style="info" %}
INFO

`CONTRACT_ADDRESS` is the address of the deployed contract.
{% endhint %}

Once you have created a `Contract` object, you can use it to call desired methods on the smart contract:

```css
async function setValue(value) {
  const tx = await contract.set(value);
  console.log(tx.hash);
}

async function getValue() {
  const value = await contract.get();
  console.log(value.toString());
}
```
