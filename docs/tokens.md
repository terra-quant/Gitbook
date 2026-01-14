---
description: >-
  Bring your ERC-20 tokens to Xhavic Mainnet using seamless L1–L2 bridging, low
  fees, and full EVM compatibility.
---

# Tokens on Xhavic

### Tokens on Xhavic Mainnet

The Xhavic Token List enables developers and token issuers to register ERC-20 tokens that are deployed on Ethereum and bridged to **Xhavic Mainnet**.\
This list is used by Xhavic tooling and interfaces (including the Xhavic Bridge) to identify supported tokens.

Xhavic aligns its token listing process with the **Optimism Superchain Token List** to maintain consistency across the OP Stack ecosystem.

The Xhavic Token List acts as a canonical source of truth for supported bridged assets across the Xhavic ecosystem.

***

### Token listing process

The following steps describe the required process to add a token to the Xhavic Token List.<br>

#### Step 1: Deploy an ERC-20 token on Xhavic <a href="#adding-your-token-to-the-list" id="adding-your-token-to-the-list"></a>

Token issuers must deploy an ERC-20 token on Xhavic that represents their Ethereum L1 asset using a supported bridging framework.&#x20;

This approach ensures that token supply on Xhavic is always backed by canonical L1 deposits.

For full compatibility, Xhavic recommends using the **Standard Bridge contracts** and deploying via the **OptimismMintableERC20Factory**.\
\
This deployment method ensures:

* Compatibility with the Xhavic Bridge
* Standardized mint/burn behavior
* Easier review and long-term support

Tokens deployed using non-standard bridging frameworks **must expose interfaces compatible with the Standard Bridge**. Tokens that do not meet these requirements may not be supported.

***

#### Step 2: Submit token metadata

Token metadata must be submitted through the official **GitHub repository** via a **Pull Request (PR)**.\
This process ensures transparency, version control, and community review of all listed assets.

The submission must include:

* A `data.json` entry for **Xhavic**
* Correct token addresses for both Ethereum and Xhavic
* Token decimals, symbol, and name

If the token already exists in the **Optimism Token List**, only minimal changes are required.\
Refer to the **cbETH example PR**, which demonstrates a standard submission using the Xhavic Standard Bridge.

***

#### Step 3: Review and approval

Merging a token into the GitHub repository **does not automatically list** the token on the Xhavic Bridge and Xhavic reserves the right to delay or reject listings that pose security, legal, or ecosystem risks.

All bridge listings are subject to a **manual review** by the Xhavic team, which includes:

* Contract validation
* Bridge compatibility checks
* Basic security and consistency verification

Only tokens that pass this review are enabled on the Xhavic Bridge.

For review status, questions, or support, developers should use the **Xhavic Discord**.
