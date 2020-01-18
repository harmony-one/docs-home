# Trust Wallet

![](../../.gitbook/assets/screen-shot-2020-01-15-at-8.42.26-am.png)

Trust Wallet is a mobile cryptocurrency wallet. Please visit [https://trustwallet.com](https://trustwallet.com) with your mobile device to download the app.

## IMPORTANT DISCLAIMER

Please note that Trustwallet does not support sharded network architecture yet, and all transactions originated from Trustwallet goes through Shard-0. This means that you can only view and access your funds in Shard-0. 

### Incoming transactions

The funds that are sent within Shard-0 will be viewed correctly in Trustwallet. \[From: Shard-0, To: Shard-0\]

If you receive funds in a shard other than Shard-0 \[e.g., From: Shard-2, you will not see the transaction receipt in Trustwallet app. Since your account balance will only show the funds in Shard-0, your total balance will not change. 

### Outgoing transactions

Since there is no shard selection in Trustwallet UI, all transactions will originate from Shard-0 and will be sent to Shard-0.

## **For more details, please see example cross-shard transaction scenarios using Trust Wallet:**

![](../../.gitbook/assets/image%20%2833%29.png)



### What to do if you receive funds in a shard other than shard 0 when using Trust Wallet?

You will need to import the account in which you receive the funds in another wallet such as CLI or Mathwallet.

**Using Mathwallet:**

1. Go to Trust Wallet under settings -&gt; Wallets -&gt; Multi Coin Wallet 1 -&gt; press the 3 dots -&gt; show recovery phase \(this gives the 12 character mnemonic\)
2. Go into MathWallet Chrome Extension -&gt; Select Harmony -&gt; Press the + button -&gt; Import wallet -&gt; import by mnemonic -&gt; enter the 12 workds previously exported from trust wallet -&gt; give the wallet a meaningful name \(e.g. Trust Wallet - Account 1\) 
3. From here you can now open mathwallet and access the funds





