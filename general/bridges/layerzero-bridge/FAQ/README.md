# FAQ

## What is LayerZero bridge?

LayerZero is a cross-chain bridge that allows exchange of crypto assets (e.g., fungible/non-fungible tokens, stablecoins) between Ethereum or Binance Smart Chain and Harmony blockchains.

The Bridge is used to migrate assets from one chain to another. If you have assets on Ethereum or Binance Smart Chain, you can use the bridge to move them to Harmony blockchain and get corresponding assets on Harmony. LayerZero also allows redemption of the exchanged assets back at any time.

\
LayerZero Bridge is accessible [here.](https://bridge.harmony.one/)

## Is there a tutorial explaining how to use LayerZero?

There is bridge process [step-by-step explanation](../../../layerzero-bridge/bridging-tutorial.md)

## What account can I use to receive bridged tokens?

You need to be able to open your wallet in the network you sent your tokens to. Check that there are no network restrictions that prevents you from it. Also check if there is no limitations on a token type you can receive.\
**Never send tokens to an exchange account!**

## Can I bridge tokens to the contract address?

No, bridging to contract address directly is not supported. It might result in permanent loss of your tokens.

## What token will I get after bridging?

Please refer to [this page](../../../layerzero-bridge/faq/bridged-tokens.md) to find out.

## Bridge transfer completed but I can't see in metamask?

You will need identify the contract address of the asset your just bridged looking at [https://bridge.harmony.one/tokens](https://bridge.harmony.one/tokens) and add it into metamask&#x20;

## What kind of assets can be bridged using LayerZero?

**Oracle 1LINK**\


**Natives**

* 1ONE (Wrapped ONE on Ethereum) - no redeploy required
* bscONE (Wrapped ONE on BSC) - no redeploy required
* ETH
* 1ETH
* bscONE (Wrapped ONE on BSC) - no redeploy required
* BNB
* bscBNB (Wrapped BnB on Harmony)
* 1WBTC

**Stablecoins**

* 1USDC
* 1USDT
* 1DAI
* 1BUSD
* bscBUSD

**Partners**

* 1AAG - no token redeploy
* 1FRAX
* 1FXS
* 1SUSHI
* xSUSHI
* 1AAVE

You can find the list the bridged assets [here](https://bridge.harmony.one/tokens)

## How are assets mapped between blockchains?

Assets are mapped 1:1. For example, 10 BUSD on Ethereum after bridging will be available as 10 1BUSD on Harmony. Here, “1BUSD“ is the token symbol of the token on Harmony corresponding to “BUSD“ token symbol on Ethereum.

Same 1:1 mapping holds true for Binance Smart Chain. However, the assets from two different parent chains (Ethereum or Binance Smart Chain) after bridging will be represented using different bridged assets on Harmony. For instance, 5 Binance Smart Chain BUSD after bridging will be available as 5 bscBUSD on Harmony. Here, “bscBUSD” is the token symbol of the token issued on Harmony corresponding to “BUSD” token symbol on Binance Smart Chain.

And, the 1BUSD and bscBUSD on Harmony chain are not interchangeable, meaning one cannot bridge BUSD from Ethereum to Harmony and then withdraw it on Binance Smart Chain. Same for other tokens.

## Can I bridge as many tokens as I want, or is there a limit?

There is no limit on the amount of tokens that can be bridged.

## Can I send my bridged tokens back?

Yes: you can bridge tokens back and receive back the same amount of the original token there. For example, you bridged USDC from Ethereum to Harmony and got 1USDC token on Harmony. At any time you can bridge 1USDC back to Ethereum and receive USDC token.

## Can I send the Ethereum bridged tokens to Binance?

No, Ethereum bridged tokens can only be sent back to Ethereum. Same applies for Binance bridged tokens.

## Can I send bridged tokens from Harmony blockchain to other blockchains or exchanges?

No, do **NOT** send bridged tokens directly to other blockchains or exchanges. This will not work and might result in permanent loss of your tokens. Bridged tokens can only be used on Harmony network. The only way to send them out is bridging them back.

## Are bridged tokens transferable?

Yes. You can transfer the bridged tokens to other users, and they can redeem them back to their Ethereum or Binance accounts. This is possible because when you lock your token, it gets pooled into a bridge smart contract from which any redeem request can be serviced without tying the locked tokens and redemption to a specific user account.

## What happens to my original tokens after I bridge them to Harmony?

Once you use LayerZero to transfer your original tokens to Harmony, the original tokens get stored and locked in the LayerZero contracts: you do not own those tokens on Ethereum or Binance anymore. You receive the same amount of tokens on the Harmony blockchain.

## Does the token supply increase when using LayerZero?

No: The supply of the original token never change as a result of using LayerZero: LayerZero bridge locks a certain amount of a token on Ethereum blockchain (essentially taking it out of circulation) and mints the exact same amount of tokens on the Harmony blockchain, that represents in all respects the original token (i.e. regenerating the locked supply). As a result, the circulating supply of the original token will stay the same: it's just split across two different blockchains instead of one.

## Which coins do I need to pay the transaction fees on the bridge?

It depends on which blockchain you want transfer assets from. If it is from Harmony blockchain, you need ONE tokens, if it is from Ethereum you need ETH tokens, from Binance Smart Chain (BSC) BNB tokens and so on.

## What’s the cost of using the bridge?

Cost of the bridge operation consists of the LayerZero bridge fee and costs of transactions. You'll see the page with the fee information that you need to confirm before the operation.\
Transaction fee depends on the chain gas prices and are confirmed in Metamask before the transaction.\
LayerZero fees are calculated dynamically based on Oracle and Relayer prices for the destination chain. They are transferred in the same transaction as the bridges amount. Fees are paid in native tokens of the first chain, so if you transfer any token from Ethereum, you pay fees by ETH token, ONE for Harmony and BNB for Binance.

## How to find out what's with my bridge operation?

You can find the operation details on your operation page. It's the page you see when you perform the operation on [the LayerZero bridge site. ](https://bridge.harmony.one/)Every bridge operation is associated with a unique operation id, which is shown on the page. You can find links to transactions of the operation steps and the status of each step.\
Also, you can always find your operation in the [bridge operation explorer.](https://bridge.harmony.one/explorer) Use "My transaction" option to see only operations for your connected Metamsk account.

## Transaction pending for too long

If your transaction is pending for too long, you can manage it via your wallet. We can’t make it faster or cancel it. If the transaction is on Harmony side, make sure you use [recommended settings ](https://docs.harmony.one/home/general/wallets/browser-extensions-wallets/metamask-wallet/adding-harmony)for Harmony network.

## Operation in progress for too long

Normally it takes less than 20 minutes per each step of the bridge operation. Delays are also possible, but they won't affect your funds.\
If your operation is in progress for **more than an hour**, you can fill in the [support form ](https://bridge.harmony.one/support)and include you problem description. Note that your request will be ignored if you send it earlier.

## Operation status is success, but I can’t find my tokens

Bridge does not swap tokens, it only provides wrapped tokens. For the token that you bridged, you have received wrapped token to your account. To find out which one, you can refer to [this page](../../../layerzero-bridge/faq/token-address.md).\


* Note that:
* Bridge is not a swap, and you won't receive ONE if you weren't bridging ONE token.
* A token address is never the same in the different networks, even when a symbol is the same.

\
If you don't see that token in your account, and add it to your wallet to see the correct balance as shown [here.](https://docs.harmony.one/home/general/wallets/browser-extensions-wallets/metamask-wallet/adding-custom-harmony-tokens)\
If you have problems with finding or adding a token, please ask for help in community groups.\


* If you added a token and tokens aren’t shown, check that:
* You added a token to the receiver wallet of your operation.
* The receiver address of your operation is correct. If you found out that you made a mistake in the address, we can’t help you with that. You can reach your funds only if you have access to the wallet.
* The receiver wallet is connected to the correct network. For example, if you bridged tokens to Harmony, you need to be connected to Harmony mainnet.
* You’ve added a token that you really received. Check the transaction data.
* Tokens haven’t been transferred after the bridge.

\
If a correct balance isn’t shown after you added a token, and you have double-checked everything, fill in the [support form](https://bridge.harmony.one/support) and include you problem description. It’s required to include a token address you added and a wallet you added it to.

## Bridge error, funds lost

Please fill in the [support form](https://bridge.harmony.one/support) and include you problem description.

## I can’t bridge because of an error

There can be many possible causes. Sometimes the reason is clear from the error message (for example, low balance, not enough tokens to cover gas).\
Often there is a problem with the wallet connection. Try these steps to solve it:

* Make sure your browser and the wallet extension are updated to the latest version
* Make sure that your browser doesn’t block pop-up windows.
* Try to clear the cache and relogin.
* Check [here ](https://docs.harmony.one/home/general/wallets/browser-extensions-wallets/metamask-wallet/adding-harmony)if your wallet is set up correctly.
* Try using another browser or/and wallet extension.
* If you use a mobile version, try it on the desktop.

If you’ve checked your settings, but you still have errors, please share your problem in the #support or #bridge [Discord](https://discord.com/invite/YJ6kgEZ5ed) channel.

## By mistake sent tokens to an exchange wallet (e.g. Binance exchange)

Unfortunately, your tokens are permanently lost and not recoverable.

## I sent tokens to a wallet that doesn’t support the network I used

If you can’t open your wallet in the network where your tokens were sent, we can’t assist. You can try to reach a support of the service that gave you this account.

## By mistake sent tokens to a wrong address or a token address

Unfortunately, we can't help in such case. We don't have access needed to transfer tokens between accounts.

## I have a question about the LayerZero bridge

You can address your question to Harmony community in Discord or Telegram. Please beware of scammers. Remember, admins never DM you first. Please refer to our [FAQ ](https://docs.harmony.one/home/general/bridges/layerzero-bridge/faq)first.
