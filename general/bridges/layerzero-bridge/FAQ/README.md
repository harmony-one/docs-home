# FAQ

## What is LayerZero bridge?
LayerZero is a cross-chain bridge that allows exchange of crypto assets
(e.g., fungible/non-fungible tokens, stablecoins) between Ethereum or
Binance Smart Chain and Harmony blockchains.

The Bridge is used to migrate assets from one chain to another.
If you have assets on Ethereum or Binance Smart Chain, you can use the bridge to move them to Harmony blockchain and get corresponding assets on
Harmony. LayerZero also allows redemption of the exchanged assets back at any time.

<br />
LayerZero Bridge is accessible 
<a href="https://bridge.harmony.one/" target="_blank">
here.
</a>


## Is there a tutorial explaining how to use LayerZero?
There is bridge process [step-by-step explanation](../bridging-tutorial.md)

## What account can I use to receive bridged tokens?
You need to be able to open your wallet in the network you sent your tokens to.
Check that there are no network restrictions that prevents you from it.
Also check if there is no limitations on a token type you can receive.
<br>**Never send tokens to an exchange account!**

## Can I bridge tokens to the contract address? 
No, bridging to contract address directly is not supported. 
It might result in permanent loss of your tokens.

## What kind of assets can be bridged using LayerZero?
<b> Oracle 1LINK</b><br/>

<b>Natives</b>
<li>1ONE (Wrapped ONE on Ethereum) - no redeploy required</li>
<li>bscONE (Wrapped ONE on BSC) - no redeploy required</li>
<li>ETH </li>
<li>1ETH</li>
<li>bscONE (Wrapped ONE on BSC) - no redeploy required</li>
<li>BNB</li>
<li>bscBNB (Wrapped BnB on Harmony)</li>
<li>1WBTC</li>

<b>Stablecoins</b>
<li>1USDC</li>
<li>1USDT</li>
<li>1DAI</li>
<li>1BUSD</li>
<li>bscBUSD</li>


<b>Partners</b>
<li>1AAG - no token redeploy</li>
<li>1FRAX</li>
<li>1FXS</li>
<li>1SUSHI</li>
<li>xSUSHI</li>
<li>1AAVE</li>

You can find the list the bridged assets 
<a href="https://bridge.harmony.one/tokens" target="_blank">
here
</a>

## How are assets mapped between blockchains?
Assets are mapped 1:1. For example, 10 BUSD on Ethereum after
bridging will be available as 10 1BUSD on Harmony. Here, “1BUSD“ is
the token symbol of the token on Harmony corresponding to “BUSD“ token symbol on Ethereum.

Same 1:1 mapping holds true for Binance Smart Chain. However, the
assets from two different parent chains (Ethereum or Binance Smart
Chain) after bridging will be represented using different bridged
assets on Harmony. For instance, 5 Binance Smart Chain BUSD after
bridging will be available as 5 bscBUSD on Harmony. Here, “bscBUSD”
is the token symbol of the token issued on Harmony corresponding to
“BUSD” token symbol on Binance Smart Chain.

And, the 1BUSD and bscBUSD on Harmony chain are not interchangeable, meaning one
cannot bridge BUSD from Ethereum to Harmony and then withdraw it on
Binance Smart Chain. Same for other tokens.

## What token will I get after bridging?
Please refer to [this page](bridged-tokens.md) to find out.

## Can I bridge as many tokens as I want, or is there a limit?
There is no limit on the amount of tokens that can be bridged.

## Can I send my bridged tokens back?
Yes: you can bridge tokens back and receive back the same amount of the original token there.
For example, you bridged USDC from Ethereum to Harmony and got 1USDC token on Harmony. 
At any time you can bridge 1USDC back to Ethereum and receive USDC token.

## Can I send the Ethereum bridged tokens to Binance?
No, Ethereum bridged tokens can only be sent back to Ethereum. 
Same applies for Binance bridged tokens.

## Can I send bridged tokens from Harmony blockchain to other blockchains or exchanges?
No, do **NOT** send bridged tokens directly to other blockchains or exchanges. 
This will not work and might result in permanent loss of your tokens. 
Bridged tokens can only be used on Harmony network. The only way to send them out is bridging them back.

## Are bridged tokens transferable?
Yes. You can transfer the bridged tokens to other users, and they can
redeem them back to their Ethereum or Binance accounts. This is possible because
when you lock your token, it gets pooled into a bridge smart contract
from which any redeem request can be serviced without tying the locked
tokens and redemption to a specific user account.

## What happens to my original tokens after I bridge them to Harmony?
Once you use LayerZero to transfer your original tokens to 
Harmony, the original tokens get stored and locked in the LayerZero
contracts: you do not own those tokens on Ethereum or Binance anymore. 
You receive the same amount of tokens on the Harmony blockchain.

## Does the token supply increase when using LayerZero?
No: The supply of the original token never change as a result of using
LayerZero: LayerZero bridge locks a certain amount of a token on Ethereum
blockchain (essentially taking it out of circulation) and mints the
exact same amount of tokens on the Harmony blockchain, that represents
in all respects the original token (i.e. regenerating the locked
supply). As a result, the circulating supply of the original token will
stay the same: it's just split across two different blockchains instead
of one.

## Which coins do I need to pay the transaction fees on the bridge?
It depends on which blockchain you want transfer assets from. If it is from Harmony blockchain, you need ONE tokens, if it is from Ethereum you need ETH tokens, from Binance Smart Chain (BSC) BNB tokens and so on.

## What’s the cost of using the bridge?
Cost of the bridge operation consists of the LayerZero bridge fee and costs of transactions. 
You'll see the page with the fee information that you need to confirm before the operation.
<br />
Transaction fee depends on the chain gas prices and are confirmed in Metamask before the transaction.
<br />
LayerZero fees are calculated dynamically based on Oracle and Relayer prices for the destination chain.
They are transferred in the same transaction as the bridges amount. 
Fees are paid in native tokens of the first chain, so if you transfer any token from Ethereum, you pay fees by ETH token, ONE for Harmony and BNB for Binance.

