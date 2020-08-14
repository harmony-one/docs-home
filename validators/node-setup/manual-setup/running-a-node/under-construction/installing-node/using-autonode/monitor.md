---
description: Track your node's status with AutoNode.
---

# Monitor

{% hint style="success" %}
If any of the commands activates a monitoring screen,  you can always exit using `Ctrl+C`.
{% endhint %}

### **1\) Harmony Monitor**

View live updates \(at 8 seconds intervals\) of your node's status \(block height, EPOS status, etc..\) with the following command:

```bash
auto-node monitor log
```

### 2\) TUI

View an overview of your validator and node with a text-based user interface. You can start it with the following command:

```bash
auto-node tui run
```

![Sample of TUI](../../../../../../../.gitbook/assets/image%20%2887%29.png)

### 3\) Harmony Node

You can view the status of the harmony node with the following command:

```text
auto-node node status
```

You can also view the logs from the node as it was initialized with the following command:

```text
auto-node node log
```

## Extra

### 1. Restart monitor

Should the monitor crash or timeout, you can restart it with the following command:

```text
auto-node monitor restart
```

### 2. Update TUI

You can update the TUI to the latest release with the following command:

```text
auto-node tui update
```

