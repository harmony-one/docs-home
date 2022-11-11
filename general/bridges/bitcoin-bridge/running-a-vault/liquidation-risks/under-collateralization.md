# Under Collateralization

Liquidation (losing your collateral) is a risk to putting your ONE as collateral against bridged Bitcoin.  This serves as a fallback and defense mechanism for those who bridged their BTC in situations where the amount they're holding on your vault cannot be exchanged for a token of equal value.

Let's walk through an example to understand when liquidation occurs.

#### **#1 | SUFFICIENT COLLATERAL**

You create a new vault and offer ONE valued at $27,000. Your vault manages a number of BTC bridge transactions and now holds $15,000 in value of BTC. The vault is in good standing.

![SUFFICIENT COLLATERAL | 150% OR HIGHER COLLATERAL AGAINST LOCKED BTC](<../../../../../.gitbook/assets/image (287) (2).png>)

#### **#2 | 1ST WARNING**

The value of BTC rises and the value of ONE remains the same. Your vault now holds $27,000 of value in ONE while storing BTC valued at $19,200. Your vault is now collateralized at 140%. As you fall below 150% collateral, your vault receives its first warning:

> **"Insufficient collateral, your vault is unable to perform normal operations, add more collateral to return to normal operation mode."**

![1ST WARNING | BELOW 150% COLLATERAL AGAINST LOCKED BTC](<../../../../../.gitbook/assets/image (289) (2).png>)

#### **#3 | 2ND WARNING**

The price of ONE declines as the market takes a turn. Your ONE collateral is now valued at $18,000 while the value of BTC on your vault shifts to $15,000. Your vault's collateral falls below 125% and is issued its second warning:

> **"Insufficient collateral, your vault is unable to perform normal operations, add more collateral to return to normal operation mode."**

![2ND WARNING | BELOW 125% COLLATERAL AGAINST LOCKED BTC](<../../../../../.gitbook/assets/image (286) (2).png>)

#### **#4 | LIQUIDATION**

Due to price fluctuations in the market, the collateral on your vault is now valued at $13,500 while the bridged BTC is valued at $15,000. Your vault is now over collateralized at 99.9% and your ONE is liquidated to ensure users who bridged their BTC are able to recover their bridged assets.

![](<../../../../../.gitbook/assets/image (285) (2).png>)

#### **Q. | What occurs to my collateral this in example of liquidation?**

In this example, the ONE you've served as collateral will be automatically removed from the vault and held in a special liquidation vault. The BTC held in your vault can be withdrawn by the vault operator. The vault will be forever banned.

However, with the locked BTC in the hands of the vault operator, the ecosystem now has more 1BTC than locked BTC. To balance the number of locked BTC with bridged 1BTC (we require a steady 1:1 ratio) bridge users will be incentivized to burn their 1BTC and receive an amount of ONE that is higher in value.

This system provided users with more earnings and incentivizes the burning of 1BTC, lowering the number of 1BTC in rotation. This continues until we have an equal number of 1BTC and locked BTC.
