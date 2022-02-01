# Vault FAQ

> _We need 10 ONE to register. Is this per registration or once per lifetime per vault?_

**Answer**: The 10 ONE is required for registering your vault. Registration is a one-time process. After registering the vault, you will not be required to contribute additional ONE aside from any collateral you wish to add.

> _Is port 3000 just for administrative access? Can I keep it LAN accessible only? If so are all needed communication created by outgoing connections?_

**Answer**: Correct - port 3000 is purely for administrative access to the vault. If your vault is running on your local LAN, you can keep port 3000 to local access only and block that from inbound connections.

> _If I wanted to switch hosting platforms, can I carry my vault over?_

**Answer**: Yes, you can simply bring your ONE and BTC private keys over to the new hosting platform, reinstall the vault software, and continue servicing bridge transactions.

> _Can a vault co-reside with a validator node on the same machine?_

**Answer**: We have not tested this and strongly recommend against it.

> _How vault selection work for users bridging BTC to 1BTC? When will my vault get selected?_

**Answer**: Vault selection is randomized as of January 31st, 2022. Your vault will be selected randomly through all the other vaults registered at that time. Further, vault selection logic will not choose a vault if the attempted bridge transaction will bring the ONE:BTC pairing below 150% collateral.

Example: Your vault holds $15,000 in ONE as collateral, and no bridged BTC. Next, a user attempts to bridge $10,000 of BTC through the bridge. Your vault can be selected as this brings your collateral to 150%. However, if this user attempted to bridge $10,500 of BTC, your vault will not be eligible for that transaction.

This is for the safety of our vault runners.

> _What is the collateral level where slashing becomes a risk?_

**Answer**:&#x20;

> _Can you delete the environment file after the vault is created?_

**Answer**: Yes, the environment file holding your private keys only needs to be present at start up of the vault. The key is loaded into memory, and the environment file can be safely removed until the next time the vault is restarted.

> _How does liquidation work when the price of ONE vs BTC begins to deviate?_

**Answer**:

> _How can I withdraw my collateral? At what point will I be liquidated when withdrawing?_

**Answer**:
