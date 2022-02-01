# Liquidation Risks

Liquidation (losing your collateral) is a risk to putting your ONE as collateral against bridged Bitcoin.  This serves as a fallback and defense mechanism for those who bridged their BTC in situations where the amount they're holding on your vault cannot be exchanged for a token of equal value.

Let's walk through an example to understand when liquidation occurs.

**#1 | SUFFICIENT COLLATERAL**

You create a new vault and offer ONE valued at $27,000. Your vault manages a number of BTC bridge transactions and now holds $15,000 in value of BTC. The vault is in good standing.

![](<../../../../.gitbook/assets/image (286).png>)

**#2 | 1ST WARNING**

The value of BTC rises and the value of ONE remains the same. Your vault now holds $27,000 of value in ONE while storing BTC valued at $19,200. Your vault is now collateralized at 140%. As you fall below 150% collateral, your vault receives its first warning:

> **"Insufficient collateral, your vault is unable to perform normal operations, add more collateral to return to normal operation mode."**

![Your vault's collateral falls below 150% and is issued its first warning.](<../../../../.gitbook/assets/image (287).png>)

**#3 | 2ND WARNING**

The price of ONE declines as the market takes a turn. Your ONE collateral is now valued at $18,000 while the value of BTC on your vault shifts to $15,000. Your vault's collateral falls below 125% and is issued its second warning:

> **"Insufficient collateral, your vault is unable to perform normal operations, add more collateral to return to normal operation mode."**

![Your vault's collateral falls below 125% and is issued its second warning.](<../../../../.gitbook/assets/image (289).png>)

**#4 | LIQUIDATION**

Due to price fluctuations in the market, the collateral on your vault is now valued at $13,500 while the bridged BTC is valued at $15,000. Your vault is now over collateralized at 90% and your ONE is liquidated to ensure users who bridged their BTC are able to recover their bridged coins.

![Your ONE collateral is liquidated to ensure BTC bridge users can recover their funds.](<../../../../.gitbook/assets/image (292).png>)
