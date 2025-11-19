---
description: Deploying a Smart Contract using Hardhat
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Using Hardhat

This section will guide you through deploying an NFT smart contract (ERC-721) on the Slice test network using [Hardhat](https://hardhat.org/).

Hardhat is a developer tool that provides a simple way to deploy, test, and debug smart contracts.

***

## Objectives[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#objectives" id="objectives"></a>

By the end of this guide you should be able to do the following:

* Setup Hardhat for Slice
* Create an NFT smart contract for Slice
* Compile a smart contract for Slice
* Deploy a smart contract to Slice
* Interact with a smart contract deployed on Slice

***

## Prerequisites[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#prerequisites" id="prerequisites"></a>

#### Node v18+[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#node-v18" id="node-v18"></a>

This guide requires you have Node version 18+ installed.

* Download [Node v18+](https://nodejs.org/en/download/)

If you are using `nvm` to manage your node versions, you can just run `nvm install 18`.

## Metamask Wallet[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#coinbase-wallet" id="coinbase-wallet"></a>

In order to deploy a smart contract, you will first need a web3 wallet. You can create a wallet by downloading the Metamask Wallet browser extension.

* Download [Metamask Wallet](https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn)

## Wallet funds[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#wallet-funds" id="wallet-funds"></a>

Deploying contracts to the blockchain requires a gas fee. Therefore, you will need to fund your wallet with ETH to cover those gas fees.

For this guide, you will be deploying a contract to the Slice Goerli test network. You can fund your wallet with Slice Goerli ETH using the following options:

* [Slice Faucet](https://slicefaucet.io/)
* [Slice Bridge](https://sliceledger.io/bridge/deposit/)

***

## Creating a project[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#creating-a-project" id="creating-a-project"></a>

Before you can begin deploying smart contracts to Slice, you need to set up your development environment by creating a Node.js project.

To create a new Node.js project, run:

Next, you will need to install Hardhat and create a new Hardhat project

To install Hardhat, run:

```
npm install --save-dev hardhat
```

To create a new Hardhat project, run:

Select `Create a TypeScript project` then press _enter_ to confirm the project root.

Select `y` for both adding a `.gitignore` and loading the sample project. It will take a moment for the project setup process to complete.

***

## Configuring Hardhat with Slice[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#configuring-hardhat-with-base" id="configuring-hardhat-with-base"></a>

In order to deploy smart contracts to the Slice network, you will need to configure your Hardhat project and add the Slice network.

To configure Hardhat to use Slice, add Slice as a network to your project's `hardhat.config.ts` file:

```brightscript
import { HardhatUserConfig } from 'hardhat/config';
import '@nomicfoundation/hardhat-toolbox';

require('dotenv').config();

const config: HardhatUserConfig = {
  solidity: {
    version: '0.8.17',
  },
  networks: {

    // for testnet
    'slice-goerli': {
      url: 'https://testrpc.sliceledger.io/',
      accounts: [process.env.WALLET_KEY as string],
      gasPrice: 1000000000,
    },
    // for local dev environment
    'slice-local': {
      url: 'http://localhost:8545',
      accounts: [process.env.WALLET_KEY as string],
      gasPrice: 1000000000,
    },
  },
  defaultNetwork: 'hardhat',
};

export default config;
```

### Install Hardhat toolbox[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#install-hardhat-toolbox" id="install-hardhat-toolbox"></a>

The above configuration uses the `@nomicfoundation/hardhat-toolbox` plugin to bundle all the commonly used packages and Hardhat plugins recommended to start developing with Hardhat.

To install `@nomicfoundation/hardhat-toolbox`, run:

```
npm install --save-dev @nomicfoundation/hardhat-toolbox
```

### Loading environment variables[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#loading-environment-variables" id="loading-environment-variables"></a>

The above configuration also uses [dotenv](https://www.npmjs.com/package/dotenv) to load the `WALLET_KEY` environment variable from a `.env` file to `process.env.WALLET_KEY`. You should use a similar method to avoid hardcoding your private keys within your source code.

To install `dotenv`, run:

```
npm install --save-dev dotenv
```

Once you have `dotenv` installed, you can create a `.env` file with the following content:

```
WALLET_KEY=<YOUR_PRIVATE_KEY>
```

Substituting `<YOUR_PRIVATE_KEY>` with the private key for your wallet.

{% hint style="danger" %}
CAUTION

`WALLET_KEY` is the private key of the wallet to use when deploying a contract. For instructions on how to get your private key from Metamask Wallet, visit the [Metamask Wallet documentation](https://support.metamask.io/hc/en-us/articles/360015289632-How-to-export-an-account-s-private-key). **It is critical that you do NOT commit this to a public repo**
{% endhint %}

***

## Compiling the smart contract[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#compiling-the-smart-contract" id="compiling-the-smart-contract"></a>

Below is a simple NFT smart contract (ERC-721) written in the Solidity programming language:

```brightscript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/utils/Counters.sol";

contract NFT is ERC721 {
    using Counters for Counters.Counter;
    Counters.Counter private currentTokenId;

    constructor() ERC721("NFT Name", "NFT") {}

    function mint(address recipient)
        public
        returns (uint256)
    {
        currentTokenId.increment();
        uint256 tokenId = currentTokenId.current();
        _safeMint(recipient, tokenId);
        return tokenId;
    }
}
```

The Solidity code above defines a smart contract named `NFT`. The code uses the `ERC721` interface provided by the [OpenZeppelin Contracts library](https://docs.openzeppelin.com/contracts/4.x/) to create an NFT smart contract. OpenZeppelin allows developers to leverage battle-tested smart contract implementations that adhere to official ERC standards.

To add the OpenZeppelin Contracts library to your project, run:

```
npm install --save @openzeppelin/contracts
```

In your project, delete the `contracts/Lock.sol` contract that was generated with the project and add the above code in a new file called `contracts/NFT.sol`. (You can also delete the `test/Lock.ts` test file, but you should add your own tests ASAP!).

To compile the contract using Hardhat, run:

***

## Deploying the smart contract[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#deploying-the-smart-contract" id="deploying-the-smart-contract"></a>

Once your contract has been successfully compiled, you can deploy the contract to the Slice Goerli test network.

To deploy the contract to the Slice Goerli test network, you'll need to modify the `scripts/deploy.ts` in your project:

```brightscript
import { ethers } from 'hardhat';

async function main() {
  const nft = await ethers.deployContract('NFT');

  await nft.waitForDeployment();

  console.log('NFT Contract Deployed at ' + nft.target);
}

// We recommend this pattern to be able to use async/await everywhere
// and properly handle errors.
main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

You'll also need testnet ETH in your wallet. See the [prerequisites ](using-hardhat.md#prerequisites)if you haven't done that yet. Otherwise, the deployment attempt will fail.

Finally, run:

```
npx hardhat run scripts/deploy.ts --network slice-goerli
```

The contract will be deployed on the Slice Goerli test network. You can view the deployment status and contract by using a [block explorer](https://testnet-slicescan.io) and searching for the address returned by your deploy script. If you've deployed an exact copy of the NFT contract above, it will already be verified and you'll be able to read and write to the contract using the web interface.

{% hint style="info" %}
INFO

If you'd like to deploy to mainnet, you'll modify the command like so:

```
npx hardhat run scripts/deploy.ts --network slice-mainnet
```
{% endhint %}

Regardless of the network you're deploying to, if you're deploying a new or modified contract, you'll need to verify it first.

***

## Verifying the Smart Contract[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#verifying-the-smart-contract" id="verifying-the-smart-contract"></a>

If you want to interact with your contract on the block explorer, you, or someone, needs to verify it first. The above contract has already been verified, so you should be able to view your version on a block explorer already. For the remainder of this guide, we'll walk through how to verify your contract on Slice Goerli testnet.

In `hardhat.config.ts`, configure Slice Goerli as a custom network. Add the following to your `HardhatUserConfig`:

* Slicescan

<pre class="language-brightscript"><code class="lang-brightscript">etherscan: {
   apiKey: {
    "slice-goerli": "PLACEHOLDER_STRING"
   },
   customChains: [
     {
       network: "slice-goerli",
       chainId: 8900,
       urls: {
        apiURL: "https://scan.sliceledger.io/api",
        browserURL: "
<strong>        https://scan.sliceledger.io/"
</strong>       }
     }
   ]
 },
</code></pre>

{% hint style="info" %}
INFO

When verifying a contract with Slicescan on testnet (Goerli), an API key is not required. You can leave the value as `PLACEHOLDER_STRING`.
{% endhint %}

```
npx hardhat verify --network slice-goerli <deployed address>
```

## Interacting with the Smart Contract[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#interacting-with-the-smart-contract" id="interacting-with-the-smart-contract"></a>

If you verified on Slicescan, you can use the `Read Contract` and `Write Contract` tabs to interact with the deployed contract. You'll need to connect your wallet first, by clicking the Connect button.

***
