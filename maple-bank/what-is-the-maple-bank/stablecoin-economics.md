---
description: Keeping the peg!
---

# Stablecoin Economics

### What is MUSD (Maple Dollar)?

MUSD is a stablecoin backed by collateral tokens via the Maple Bank which is decentralized and non-custodial.

### How can I get MUSD?

MUSD can be minted when users borrow from the Maple Bank by locking a collateral of their choosing in order to back the value of MUSD borrowed. You may follow the step by step instructions detailed in our [How to Borrow MUSD](how-to-borrow-musd.md#step-by-step-guide) page.

Your minted MUSD can be found in your wallet and you may have to add MUSD as a custom token to be able to see it in your browser extension wallet.&#x20;

### How is the peg maintained?

The peg is maintained via **Liquidations** and **Dynamic Collateral Ratio** which are detailed below:

Liquidation ensures that every MUSD is backed by its collateral value in the bank. When a user's collateral fall below the liquidation ratio, they can be partially/fully liquidated. This means that some of the user's debt is repaid by a liquidator, and in return the liquidator will receive some of the user's collateral. The initial liquidation ratio will be set at 130%-150%, which is subject to change by community proposals/voting.

The bank is overcollateralized by 130-150%, depending on the asset, to ensure that the stablecoins minted are backed by its value. As the overall value of the collateral, more stablecoins can be issued from the effect of rising prices which can increase a user's collateral to debt ratio.&#x20;

On the other hand, if the value of the collateral falls, fewer stablecoins can be issued and some existing ones can be liquidated. This is implemented to maintain the minimum collateral to debt ratio of each bank.

### Can MUSD be bought "off the shelf"?

Yes, we will be using other decentralized exchanges to offer MUSD. However, the list of protocols that will be offering this is still being finalized.
