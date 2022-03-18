# How to bridge back an incorrectly bridged token

There are cases when a token was bridged with the wrong settings and wrapped in a way that it lost its liquidity (1bscDAI, bsc1UST, etc). In this situation, you need to bridge your tokens back to remove an extra wrap. For example, if you bridge ONE as BEP20, you get bscONE token instead of Native ONE.

It also can happen if you bridge your token to the wrong network. For example, you can’t get a liquid token on Binance from [BUSD](https://explorer.harmony.one/address/0xE176EBE47d621b984a73036B9DA5d834411ef734?activeTab=3) which originated from the Ethereum, and bscBUSD won’t be liquid on Ethereum: token will get an extra wrap.

If you have an incorrectly bridged token that has more than one wrap, you need to remove them step by step: one operation for each wrap.

To remove the wrap you need to undo the last operation: bridge your tokens back to the network where they were before the wrap. Use the same token type you used in the operation that resulted in this wrap and the address of the token you had before the wrap.

For example, you bridged Binance ONE to Harmony as BEP20 and received bscONE. You need to bridge it back as BEP20 and use for custom address the address of Binance ONE you had before.

If you don’t remember the last operation details, pay attention to:

1. Prefix: bsc\*\*\* or 1\*\*\* (only the very first if you have more than one wrap)
2. Where are tokens now: Harmony, Ethereum or Binance

You will also need to find an address of a mapped token in a target network - it’s the token that you had before the operation ended in the wrap (and it’s the same token you gonna receive after the unwrap operation). You can find it in the lock/burn transaction of that operation.

Depending on it and the network your token is now and the prefix, choose settings for the unwrap bridge operation:

* For **bsc**\*\*\* on Harmony: Harmony \*\*\*\*to **Binance** type: **BEP20** custom address = address of a mapped token in **Binance** network. Token symbol on Binance is the same but without “bsc” prefix
* For **1**\*\*\* on **Harmony**: Harmony \*\*\*\*to **Ethereum** type: **ERC20** custom address = address of a mapped token in **Ethereum** network - it’s the token on Ethereum without the “1” prefix in the symbol
* For **1**\*\*\* on **Binance**: **Binance** to **Harmony** type: **HRC20** custom address = address of a mapped token in **Harmony** network - it’s the token on Harmony without the “1” prefix in the symbol
* For **1**\*\*\* on Ethereum: Ethereum to **Harmony** type: **HRC20** custom address = address of a mapped token in **Harmony** network - it’s the token on Harmony without the last “1” prefix in the symbol

### Examples

One extra wrap:

[bscOne](../../../horizon-bridge/assets/bscOne.md)

[1bscDAI](../../../horizon-bridge/assets/1bscDAI.md)

[1bscUSDT](../../../horizon-bridge/assets/1bscUSDT.md)

[1BUSD](../../../horizon-bridge/assets/1BUSD.md)

Two or more extra wraps:

[bsc1bsc1bscONE](../../../horizon-bridge/assets/bsc1bsc1bscONE.md)

[bsc1bscDAI](../../../horizon-bridge/assets/bsc1bscDAI.md)

[1bsc1BUSD](../../../horizon-bridge/assets/1bsc1BUSD.md)

[bsc1bscUSDT](../../../horizon-bridge/assets/bsc1bscUSDT.md)

[bsc1bsc11USDC](../../../horizon-bridge/assets/bsc1bsc11USDC.md)

[bsc1bscWBNB](../../../horizon-bridge/assets/bsc1bscWBNB.md)

[1bsc1UST](../../../horizon-bridge/assets/1bsc1UST.md)

You can follow the example instruction if you have the same token in the same network. If you have the same token with fewer wraps than the example, start with the step corresponding to your token symbol. For example, if you have 1bscONE, start [bsc1bsc1bscONE](how-to-bridge-back-an-incorrectly-bridged-token.md) from the 1bscONE → bscONE step.

During the operation, you probably will see alerts about a token address. The reason is that you made a mistake before and now you have to break some rules to undo it. Press “Use address anyway” and then confirm. Please ignore these alerts only if you are bridging back incorrectly bridged tokens.

There is no need to add any token address in your wallet. You’ll see the amount on the operation page after the setup.

If your case is not listed, you can try to do unwrap it at your own risk. Please be very careful. If you don’t understand what to do, you can ask advanced users in community groups for help or send a support request.
