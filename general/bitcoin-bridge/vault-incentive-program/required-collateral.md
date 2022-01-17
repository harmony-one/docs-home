# Required Collateral

### How much collateral is required to launch a vault?  <a href="#docs-internal-guid-052b0226-7fff-8910-e0c1-08301e9cd0a1" id="docs-internal-guid-052b0226-7fff-8910-e0c1-08301e9cd0a1"></a>

There is no limit on the amount of collateral (in ONE) that any vault can initially put down to take custody of users bitcoins and facilitate 1BTC issuing. However, vaults are expected to maintain a collateral ratio of 150% in terms of the dollar amount. \
\
Some example scenarios are described below.

**Example 1:**

Collateral provided by vault operator: 200,000 ONE\
Equivalent dollar amount: $68,000 (at $0.34 /ONE)\
Allowed dollar amount for 1BTC issuing: $45,333 (0.66 \* dollar amount)\
Allowed 1BTC issuing: up to 0.52 1BTC (calculated at $43,000 /BTC)

**Example 2:**

Collateral provided by vault operator: 2,000,000 ONE\
Equivalent dollar amount: $680,000 (at $0.34 /ONE)\
Allowed dollar amount for 1BTC issuing: $453,333 (0.66 \* dollar amount)\
Allowed 1BTC issuing: up to 10.54 1BTC (calculated at $43,000 /BTC)

Note that an automated system is deployed to ensure that vaults are sufficiently collateralized at all times. If a vault’s collateralize ratio falls below the minimum threshold, the vault is issued a warning and after a predefined period of time, the vault’s collateral will be liquidated. How much is liquidated is defined by the bridge protocol parameters. We will provide a vault dashboard to manage all the notifications and activities. Also, there will be automated tools to manage all these in the background.
