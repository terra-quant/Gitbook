---
description: Deploying a Smart Contract using Remix
---

# Using Remix

[Remix](https://remix.ethereum.org/) is an online IDE that you can use to rapidly develop and deploy smart contracts. If you're new to smart contracts, it's a great tool that lets you jump right in without needing to configure a local editor or struggle through environment configuration issues before getting started.

Remix contains a simulation of a blockchain that you can use to rapidly deploy and test your contracts. This simulation only exists within your browser, so you can't share it with others or use external tools or a front end to interact with it. However, you can also deploy to a variety of testnets from within Remix. Doing so will allow you to share your contract with others, at the cost of making it public.

In this article, we'll give you an overview of Remix, and show you how to deploy a contract to Xhavic **Goerli** testnet.

{% hint style="info" %}
INFO

For production / mainnet deployments the steps below in this guide will be almost identical, however, you'll want to ensure that you've selected Xhavic (mainnet) as the network rather than Xhavic `Goerli` (testnet).
{% endhint %}

If you're already familiar with Remix, you probably want to jump down to [here](https://github.com/Xhavicchain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md).

***

## Objectives[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#objectives" id="objectives"></a>

By the end of this lesson you should be able to:

* List the features, pros, and cons of using Remix as an IDE
* Deploy and test the Storage.sol demo contract in Remix
* Use Remix to deploy a contract to the Xhavic @ Goerli testnet and interact with it in Etherscan

***

## Remix Window Overview[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#remix-window-overview" id="remix-window-overview"></a>

Begin by opening a browser window and navigating to \[remix.ethereum.org]. Click through the introductory tips, then review the editor. It is divided into three areas, which should look familiar.

### Editor Pane[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#editor-pane" id="editor-pane"></a>

The editor pane loads with the Remix home screen, which contains news, helpful links, and warnings about common scams. You can close the home tab if you'd like, then open `1_Storage.sol`, located inside the `contracts` folder of the `default_workspace`.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

You'll edit your code in the editor pane. It also has most of the features you're expecting, such as syntax and error highlighting. Note that in Remix, errors are not underlines. Instead, you'll see an❗to the left of the line number where the error is present.

At the top, you'll see a big green arrow similar to the _Run_ button in other editors. In Solidity, this compiles your code, but it does not run it because you must first deploy your code to the simulated blockchain.

### Terminal/Output[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#terminaloutput" id="terminaloutput"></a>

Below the editor pane, you'll find the terminal.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

You'll primarily use this panel to observe transaction logs from your smart contracts. It's also one way to access Remix's powerful debugging tools.

### Left Panel[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#left-panel" id="left-panel"></a>

As with many other editors, the left panel in Remix has a number of vertical tabs that allow you to switch between different tools and functions. You can explore the files in your current workspace, create and switch between workspaces, search your code, and access a number of plugins.

***

## Plugins[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#plugins" id="plugins"></a>

Most of the features in Remix are plugins and the ones you'll use the most are active by default. You can view and manage plugins by clicking the plug button in the lower-left corner, right above the settings gear. You can turn them off and on by clicking activate/deactivate, and some, such as the _Debug_ plugin will be automatically activated through other parts of the editor.

### Solidity Compiler[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#solidity-compiler" id="solidity-compiler"></a>

The first default plugin (after the search function) is the _Solidity Compiler_. Be sure to check the `Auto compile` option. Smart contracts are almost always in very small files, so this shouldn't ever cause a performance problem while editing code.

The `Compile and Run script` button in this plugin is a little misleading. This is **not** how you will usually run your contract through testing. You can click the `I` button for more information on this feature.

Finally, if you have errors in your contracts, the complete text for each error will appear at the bottom of the pane. Try it out by introducing some typos to `1_Storage.sol`.

### Deploy & Run Transactions[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#deploy--run-transactions" id="deploy--run-transactions"></a>

The _Deploy & Run Transactions_ plugin is what you'll use to deploy your contracts and then interact with them. At the top are controls to select which virtual machine to use, mock user wallets with test Ether, and a drop down menu to select the contract you wish to deploy and test.

Fix any errors you introduced to `1_Storage.sol` and click the orange `Deploy` button. You'll see your contract appear below as _STORAGE AT \\\<address>_.

{% hint style="danger" %}
CAUTION

There are a couple gotchas that can be very confusing with deploying contracts in Remix.

First, every time you hit the Deploy button, a new copy of your contract is deployed, but the previous deployments remain. Unless you are comparing or debugging between different versions of a contract, or deploying multiple contracts at once, you should click the `Trash` button to erase old deployments before deploying again.

Second, if your code will not compile, **clicking the deploy button will not generate an error!** Instead, the last compiled version will be deployed. Visually check and confirm that there are no errors indicated by a number in a red circle on top of the Compiler plugin.
{% endhint %}

***

## Prepare for Deployment[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#prepare-for-deployment" id="prepare-for-deployment"></a>

Testnets operate in a similar, **but not exactly the same** manner as the main networks they shadow. You need a wallet with the appropriate token to interact with them by deploying a new contract or calling functions in a deployed contract.

### Set Up a Wallet[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#set-up-a-wallet" id="set-up-a-wallet"></a>

If you already have a wallet set up **exclusively for development**, you can skip to the next section. Otherwise, now is the time to jump in!

First, add the [Metamask](https://metamask.io/) wallet to your browser, and [set up](https://www.youtube.com/watch?v=CZDgLG6jpgw) a new wallet. As a developer, you need to be doubly careful about the security of your wallet! Many dApps grant special powers to the wallet address that is the owner of the contract, such as allowing the withdrawal of all the Ether that customers have paid to the contract, or changing critical settings.

Once you've completed wallet setup, enable developer settings and turn on testnets ([Metamask Settings](https://support.metamask.io/hc/en-us/articles/13946422437147-How-to-view-testnets-in-MetaMask).

### Add the Xhavic Goerli Network to your Wallet[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#add-the-base-goerli-network-to-your-wallet" id="add-the-base-goerli-network-to-your-wallet"></a>

For this guide, you will be deploying a contract to the Xhavic Goerli test network. You can fund your wallet with Xhavic Goerli ETH using the following options:

* [Xhavic Faucet](https://xhavicfaucet.io/)
* [Xhavic Bridge](https://xhavicledger.io/bridge/deposit/)

***

## Deploying to Testnet[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#deploying-to-testnet" id="deploying-to-testnet"></a>

Once you have testnet Ether, you can deploy the `Storage` contract!

### Selecting the Environment[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#selecting-the-environment" id="selecting-the-environment"></a>

Open the _Deploy & Run Transactions_ tab. Under _Environment_, select _Injected Provider_. It will list _Metamask_, or any other wallet you have activated here.

![](<../../.gitbook/assets/image (7).png>)

The first time you do this, your wallet will ask you to confirm that you want to connect this dApp (Remix) to your wallet.

Once you are connected, you'll see the name of the network below the _Environment_ dropdown.

![](<../../.gitbook/assets/image (8).png>)

For Xhavic Goerli, you should see `Custom (8900) network.`

If you don't see the correct network, change the active network in your wallet.

### Deploy the Contract[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#deploy-the-contract" id="deploy-the-contract"></a>

Click the orange _Deploy_ button. Because it costs gas to deploy a contract, you'll be asked to review and confirm a transaction.

![](<../../.gitbook/assets/image (9).png>)

After you click the _Confirm_ button, return to Remix and wait for the transaction to deploy. Copy its address and navigate to [testnet-Xhavicscan.io](https://testnet-xhavicscan.io/). **Note:** If you deployed to mainnet, you'll navigate to [Xhavicscan.io](https://xhavicscan.io/) instead.

### Verify the Contract[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#verify-the-contract" id="verify-the-contract"></a>

You can interact with your deployed contract using Remix, the same as before, but it's also possible to interact with it through Etherscan. Paste your address in the search field to find it.

On this page, you can review the balance, information about, and all the transactions that have ever occurred with your contract.

Click the _Contract_ tab in the main panel. If you've deployed a unique contract, at the top is a message asking you to _Verify and Publish_ your contract source code.

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Verifying your contract maps the names of your functions and variables to the compiled byte code, which makes it possible to interact with the contract using a human-readable interface.

Click the link. Your contract address is already entered.

Under _Please select Compiler Type_ choose \_Solidity (Single file)

For _Please Select Compiler Version_ select the version matching the `pragma` at the top of your source file. Our examples are currently using _v0.8.17+commit.8df45f5f_.

For _Please select Open Source License Type_ pick the license that matches what you selected for your contract as the `SPDX-License-Identifier`. Pick _None_ if you followed the Solidity-recommended practice of using `UNLICENSED`.

On the next page, copy and paste your source code in the window. Verify that you are not a robot, and click _Verify and Publish_. You should see a success message.

Click the linked address to your contract to return to the contract page. You'll now see your code!

### Interact with the Contract[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#interact-with-the-contract" id="interact-with-the-contract"></a>

You can now interact with your contract using Etherscan. Click the _Read Contract_ button. Both of your functions will be listed here and can be tested using the web interface.

You won't have anything under _Write Contract_ because this contract doesn't have any functions that save data to state.

***

## Conclusion[​](https://github.com/slicechain/Gitbook/blob/main/docs/guides/deploying-a-smart-contract/broken-reference/README.md) <a href="#conclusion" id="conclusion"></a>

You now have the power to put smart contracts on the blockchain! You've only deployed to a test network, but the process for real networks is exactly the same - just more expensive!

***
