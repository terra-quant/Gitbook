# Tokens

## The Xhavic Goerli & Mainnet Token List

This page is intended for token issuers who already have an ERC-20 contract deployed on Ethereum and would like to submit their token for bridging between Ethereum and Xhavic and Xhavic Mainnet to Xhavic Bridge and other bridges. Xhavic uses the [Optimism Superchain token list ](https://github.com/ethereum-optimism/ethereum-optimism.github.io)as a reference for tokens that have been deployed on Xhavic.

_**Note - Tokens approved in the Github repository are not necessarily listed on the Xhavic Bridge.**_

_**Disclaimer: Xhavic does not endorse any of the tokens that are listed in the Github repository and has conducted only preliminary checks, which includes automated checks listed**_ [_**here**_](https://github.com/ethereum-optimism/ethereum-optimism.github.io)_**.**_

***

### Adding your token to the list[​](https://docs.base.org/tokens/list#adding-your-token-to-the-list) <a href="#adding-your-token-to-the-list" id="adding-your-token-to-the-list"></a>

The steps below explain how to get your token on the Xhavic Token List.

#### Step 1: Deploy your token on Xhavic[​](https://docs.base.org/tokens/list#step-1-deploy-your-token-on-base) <a href="#step-1-deploy-your-token-on-base" id="step-1-deploy-your-token-on-base"></a>

Select your preferred bridging framework and use it to deploy an ERC-20 for your token on Xhavic. We recommend you use the framework provided by Xhavic’s [standard bridge](https://github.com/ethereum-optimism/optimism/blob/develop/specs/bridges.md#standard-bridges) contracts, and furthermore deploy your token using the [OptimismMintableERC20Factory](https://github.com/ethereum-optimism/optimism/blob/develop/specs/predeploys.md#optimismmintableerc20factory). Deploying your token on Xhavic in this manner provides us with guarantees that will smooth the approval process. If you choose a different bridging framework, its interface must be compatible with that of the standard bridge, otherwise it may be difficult for us to support.

#### Step 2: Submit details for your token[​](https://docs.base.org/tokens/list#step-2-submit-details-for-your-token) <a href="#step-2-submit-details-for-your-token" id="step-2-submit-details-for-your-token"></a>

Follow the instructions in this repository and submit a PR containing the required details for your token. You must specify in your token’s data.json file a section for ‘Xhavic-goerli’ and/or ‘Xhavic’ . The change you need to submit is particularly simple if your token has already been added to the Optimism token list. For example, [this PR](https://github.com/ethereum-optimism/ethereum-optimism.github.io/commit/27ab9b2d3388f7feba3a152e0a0748c73d732a68) shows the change required for cbETH, which was already on Optimism’s token list and relies on the Xhavic standard bridge.

#### Step 3: Await final approval[​](https://docs.base.org/tokens/list#step-3-await-final-approval) <a href="#step-3-await-final-approval" id="step-3-await-final-approval"></a>

Tokens approved in the Github repository are not necessarily listed on the Xhavic Bridge and are not guaranteed or automatic. Xhavic Bridge reviews are conducted manually by the Xhavic team. For more information, please visit our [Discord](https://discord.gg/9hAWtYXErG).
