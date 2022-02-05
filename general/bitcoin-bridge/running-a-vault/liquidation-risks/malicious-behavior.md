# Malicious Behavior

Vault runners should not attempt to extract their ONE collateral while BTC is locked to their vault. Doing so is considered malicious as it signals an attempt to obtain ownership of both their ONE collateral and locked BTC.

When any attempt to extract ONE collateral while BTC is locked to a vault, the malicious behavior is automatically detected and the vault's collateral is immediately transferred to a special liquidation vault. The vault runner has no access to their ONE collateral, the vault is blacklisted. The vault runner only access to the locked BTC, which holds equal or less value than their total collateral since the minimum collateral ratio is 100% or higher.
