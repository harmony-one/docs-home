# Malicious Behavior

Vault runners will be unable to extract their ONE collateral below the required 150% collateral via GUI. However, attempts to bypass this by other means is considered malicious as it signals an attempt to obtain ownership of both their ONE collateral and locked BTC.

Attempts to bypass the GUI restrictions of withdrawing below 150% collateral will be automatically detected, and the vault's collateral will be immediately transferred to a special liquidation vault. The vault runner has no access to their ONE collateral once this occurs and the vault is blacklisted. At this point, the vault runner only access to the locked BTC, which holds equal or less value than their total collateral since the minimum collateral ratio is 100% or higher.
