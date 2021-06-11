---
description: Using node.sh
---

# Installing & Updating

{% hint style="warning" %}
As per instructions on the [cloud guides](../../cloud-setup/cloud-guides/), the host needs to open up port **9000** for blockchain consensus messages and port **6000** for blockchain state syncing. Other ports are NOT necessary for syncing and should NOT be opened to the internet if you are staking only.
{% endhint %}

* 9000 port is used for blockchain consensus messages \(**base port**\)
* 6000 port is used for blockchain state syncing \(base port - 3000\)
* 9500 port is used for SDK RPC service \(base port + 500\)
* 9800 port is used for Websocket service \(base port + 800\)

The 9500, 9800 ports are only listened by localhost 127.0.0.1 by default. 

