# web3.js

[web3.js](https://web3js.readthedocs.io/) is a JavaScript library that allows developers to interact with EVM-compatible blockchain networks.

You can use web3.js to interact with smart contracts deployed on the Xhavic network.

***

## Install[​](https://github.com/slicechain/Gitbook/blob/main/docs/clients/broken-reference/README.md) <a href="#install" id="install"></a>

To install web3.js run the following command:

## Setup[​](https://github.com/slicechain/Gitbook/blob/main/docs/clients/broken-reference/README.md) <a href="#setup" id="setup"></a>

Before you can start using web3.js, you need to import it into your project.

Add the following line of code to the top of your file to import web3.js:

```
const Web3 = require('web3');
```

## Connecting to Xhavic[​](https://github.com/slicechain/Gitbook/blob/main/docs/clients/broken-reference/README.md) <a href="#connecting-to-base" id="connecting-to-base"></a>

You can connect to Xhavic by instantiating a new web3.js `Web3` object with a RPC URL of the Xhavic network:

```
const Web3 = require('web3');

const web3 = new Web3('https://testrpc.Xhavic.io/');
```

## Accessing data[​](https://github.com/slicechain/Gitbook/blob/main/docs/clients/broken-reference/README.md) <a href="#accessing-data" id="accessing-data"></a>

Once you have created a provider, you can use it to read data from the Xhavic network.

For example, you can use the `getBlockNumber` method to get the latest block:

```
async function getLatestBlock(address) {
  const latestBlock = await web3.eth.getBlockNumber();
  console.log(latestBlock.toString());
}
```

## Deploying contracts[​](https://github.com/slicechain/Gitbook/blob/main/docs/clients/broken-reference/README.md) <a href="#deploying-contracts" id="deploying-contracts"></a>

Before you can deploy a contract to the Xhavic network using web3.js, you must first create an account.

You can create an account by using `web3.eth.accounts`:

```
const privateKey = “PRIVATE_KEY”;
const account = web3.eth.accounts.privateKeyToAccount(privateKey);
```

{% hint style="info" %}
INFO

`PRIVATE_KEY` is the private key of the wallet to use when creating the account.
{% endhint %}

## Interacting with smart contracts[​](https://github.com/slicechain/Gitbook/blob/main/docs/clients/broken-reference/README.md) <a href="#interacting-with-smart-contracts" id="interacting-with-smart-contracts"></a>

You can use web3.js to interact with a smart contract on Xhavic by instantiating a `Contract` object using the ABI and address of a deployed contract:

```
const abi = [
… // ABI of deployed contract
];

const contractAddress = "CONTRACT_ADDRESS"

const contract = new web3.eth.Contract(abi, contractAddress);
```

Once you have created a `Contract` object, you can use it to call desired methods on the smart contract:

```
async function setValue(value) {
  // write query
  const tx = await contract.methods.set(value).send();
  console.log(tx.transactionHash);
}

async function getValue() {
  // read query
  const value = await contract.methods.get().call();
  console.log(value.toString());
}
```
