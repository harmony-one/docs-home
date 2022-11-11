# Liquidation Risks

Liquidation (losing your ONE collateral) is an inherent risk when putting your ONE as collateral against bridged Bitcoin. This serves as a defense mechanism for those who bridged their BTC, and helps ensure users can redeem their 1BTC for equal or higher value.&#x20;

Losing your collateral through liquidation occurs in one of two ways:

**a. Under collateralized**

Price fluctuates with the market and your ONE collateral becomes worth less than the BTC locked to your vault. As your collateral ratio lowered, you, the vault runner, failed to increase collateral to stay above 100%. Your ONE collateral is liquidated when collateralized at 99.9%.

**b. Malicious Behavior / Theft**

The vault runner attempts to remove their ONE collateral maliciously while BTC is still locked to their vault. The network will detect this attempt, immediately liquidate the vault's collateral, and blacklist the vault forever.

Let's walk through these scenarios to better understand when liquidation occurs.

****
