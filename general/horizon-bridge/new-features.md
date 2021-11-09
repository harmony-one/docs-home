---
description: >-
  This page describes the features released in the first Horizon feature
  release.
---

# New Features

Horizon bridge currently supporting bridging BUSD, LINK, and any ERC20 token from Ethereum to Harmony and back. In this feature release we have added the following three major features:

1. ETH bridging
   * Allows bridging native ETH from Ethereum to receive 1ETH on Harmony
2. ERC721 (NFT on Ethereum) bridging
   * Allows single or in batch bridging of ERC721 (or NFTs) to Harmony to receive HRC721
3. ONE & HRC20 bridging
   * Allows bridging Harmony's native ONE token and any HRC20 issued on Harmony to Ethereum for utilizing Ethereum ecosystem and DApps&#x20;
4. ERC1155 bridging
   * Allows single or in batch bridging of ERC1155 to Harmony to receive HRC1155
5. HRC721 (NFT on Harmony) bridging
   * Allows single or in batch bridging of HRC721 (or NFTs) to Ethereum to receive ERC721
6. HRC1155 bridging
   * Allows single or in batch bridging of ERC1155 to Ethereum to receive ERC1155

## ETH Bridging

For bridging ETH to Harmony, select ETH under ETH > ONE tab enter a valid amount and proceed

![](<../../.gitbook/assets/Screen Shot 2021-01-12 at 6.18.43 PM.png>)

For redeeming your ETH back to Ethereum by burning 1ETH, select ETH under ONE > ETH tab, enter a valid amount and proceed

![](<../../.gitbook/assets/Screen Shot 2021-01-12 at 6.22.11 PM.png>)

## ERC721 Bridging

Over 8000+ ERC721s (NFTs) existing on Ethereum (e.g., Sorare, Unstoppable Domains) can be bridged to Harmony and traded at darn low gas fees.

You can bridge any ERC721 and receive equivalent amount of HRC721. The token metadata in the form of baseURI and tokenURI are preserved.

For bridging ERC721 from Ethereum to Harmony, select ERC721 under ETH > ONE flow tab and select the tokenIds that you want to bridge and proceed. 1 or more tokenIds can be selected for bridging. In the picture below, I am bridging both of my tokens with tokenIds 0 & 1. The tokenIds can be any valid uint256.

![](<../../.gitbook/assets/Screen Shot 2021-01-12 at 6.28.40 PM.png>)

For redeeming your ERC721 back to Ethereum by burning HRC721, select ERC721 under ONE > ETH flow tab and select the tokenIds that you want to bridge back and proceed. In the picture below, I am only bridging back 1 token with tokenId 0.

![](<../../.gitbook/assets/Screen Shot 2021-01-12 at 6.39.18 PM.png>)

## HRC721 Bridging

Over 200+ HRC721s (NFTs) existing on Harmony (e.g., HarmonyOnePunks, Harmoonies) can be bridged to Ethereum and traded in the bigger market.

You can bridge any HRC721 and receive equivalent amount of ERC721. The token metadata in the form of baseURI and tokenURI are preserved.

For bridging HRC721 from Harmony to Ethereum, select HRC721 under ONE > ETH flow tab and select the tokenIds that you want to bridge and proceed. 1 or more tokenIds can be selected for bridging. In the picture below, I am bridging both of my tokens with tokenIds 0 & 1. The tokenIds can be any valid uint256.

![bridging HRC20 to Ethereum](<../../.gitbook/assets/image (286).png>)

For redeeming your HRC721 back to Harmony by burning ERC721, select HRC721 under ETH > ONE flow tab and select the tokenIds that you want to bridge back and proceed. In the picture below, I am only bridging back 1 token with tokenId 0.

![redeeming HRC721 to Harmony ](<../../.gitbook/assets/image (287).png>)

## ERC1155 & HRC1155 Bridging

Bridging ERC1155 and HRC1155 are same as ERC721 and HRC721. just add the amount for token you want to bridging(1 for NFT and above 1 for token)

![](<../../.gitbook/assets/image (285).png>)

After filled token address and token ID of HRC/ERC1155 and select the token. you will see the available token amount.

## ONE & HRC20 Bridging

With this feature, Harmony users can now take their ONE tokens and HRC20s to Ethereum and utilized the ecosystem and DApps available in Ethereum.&#x20;

For bridging ONE tokens from Harmony to Ethereum, select ONE under ONE > ETH flow tab and enter a valid amount of ONE tokens to bridge to Ethereum and proceed.

![](<../../.gitbook/assets/Screen Shot 2021-01-12 at 6.41.12 PM.png>)

For redeeming back the bridged ONE tokens back from Ethereum to Harmony, select ONE under ETH > ONE flow tab and enter a valid amount of 1ONE tokens to bridge back from Ethereum to Harmony and proceed.

![](<../../.gitbook/assets/Screen Shot 2021-01-12 at 6.43.48 PM.png>)

For bridging HRC20 tokens from Harmony to Ethereum, select HRC20 under ONE > ETH flow tab and proceed with entering a valid amount of HRC20 tokens to bridge from Harmony to Ethereum and proceed.

![](<../../.gitbook/assets/Screen Shot 2021-01-12 at 6.47.19 PM.png>)

For redeeming back the bridged HRC20 tokens back from Ethereum to Harmony, select HRC20 under ETH > ONE flow tab and proceed with entering a valid amount of 1HRC20 tokens to bridge back from Ethereum to Harmony and proceed.

![](../../.gitbook/assets/screen-shot-2021-01-12-at-6.48.31-pm.png)

{% hint style="info" %}
Onewallet HRC721 support is under development, an official release can be expected soon. Meanwhile, an alpha version can be found below that supports HRC721.
{% endhint %}
