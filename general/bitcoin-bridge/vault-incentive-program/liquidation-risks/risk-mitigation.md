# Risk Mitigation

There are multiple ways to mitigate liquidation of your ONE collateral. Some of these are performed by Harmony at the contract level, others you can prepare for as a vault runner. Below we'll explain each to help you feel safe in providing collateral to your BTC vault.

{% hint style="warning" %}
**Note**: Liquidation is always a risk regardless of what steps one takes to mitigate that risk. Running a BTC vault requires that operators pay attention to their collateral periodically .&#x20;
{% endhint %}

### Protection Against Liquidation &#x20;

### Contract-Level

Harmony has implemented a handful of mechanisms at the contract level to help protect BTC vault runners against liquidation.&#x20;

**#1 | Vault Selection Logic**

Vaults are selected randomly when using BTC bridge front-end. However, the selection logic will exclude your vault if the attempted transaction will reduce your collateral ratio below 150%.

This protects your vault from liquidation at the vault selection level; your collateral ratio is left with an additional 50% buffer to account for price deviation due to market fluctuations.

**#2 | Protection Against Spikes in Price Deviation**

Significant price deviations due to price feed data can increase risk for liquidation. We have implemented logic in the smart contract which will drastically reduce this risk.&#x20;

This logic compares the latest price feed data with the price obtained in the previous feed. Time between price data feeds is usually measured in seconds, sometimes minutes. If the price has a 10% difference in comparison to previous data, the transaction will not be processed as it's considered an unnatural price change due to invalid price data.

**#3 | Delays in BTC Issuing Process**

Bridging BTC for 1BTC can take upwards of 20 to 30 minutes to complete due to speed at which BTC finalizes the transaction. This delay significantly reduces risk of liquidation due to:

a) Temporary sharp deviation in price and...

b) Arbitration bots taking advantage of that different, putting your vault at liquidation risk.

### Suggestions for Vault Runners

**#1 | Monitor Your Vault**

We suggestion for vault runners to check their vault's collateral ration every few days to ensure they are aware of where they stand. Vault runners who aren't aware of their collateral ratio cannot take action to prevent liquidation.

**#2 | Holding ONE in Reserves**

If your collateral ratio is ever in the initial warning range (<150% - 125%), we strongly suggest adding additional collateral before reaching the second range (<125% - 100%). Keeping a reserve of ONE specifically to serve as collateral would help ensure you're always prepared to return your ratio to a healthy, sufficient level (>150%).

