# Required Collateral

### How much collateral is required to launch a vault?  <a href="#docs-internal-guid-052b0226-7fff-8910-e0c1-08301e9cd0a1" id="docs-internal-guid-052b0226-7fff-8910-e0c1-08301e9cd0a1"></a>

There is no limit on the amount of collateral (in ONE) that any vault can initially put down to take custody of users bitcoins and facilitate 1BTC issuing. However, vaults are expected to maintain a collateral ratio of 150% in terms of the dollar amount. \
\
Example scenarios below assume a ONE price of $0.34 and BTC price of $43,000.

**Example 1:**

Collateral: 200,000 ONE\
Equivalent dollar amount: $68,000\
Allowed Issuing: 1.054 1BTC | Equal to $45,333

**Example 2:**

Collateral: 2,000,000 ONE\
Equivalent dollar amount: $680,000\
Allowed Issuing: 10.54 1BTC | Equal to $453,333

_<mark style="color:red;">Allowed Issuing = ONE Collateral Dollar Amount / 1.5</mark>_

Note that an automated system is deployed to ensure that vaults are sufficiently collateralized at all times. If a vault’s collateralize ratio falls below the minimum threshold, the vault is issued a warning and after a predefined period of time, the vault’s collateral will be liquidated. How much is liquidated is defined by the bridge protocol parameters which will be detailed before launch of the BTC Bridge.&#x20;

We will provide a vault dashboard to manage all the notifications and activities. Also, there will be automated tools to manage all these in the background.
