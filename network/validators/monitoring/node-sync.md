---
description: Verifying your node's chain synchronization
---

# Node Sync

### The /node-sync endpoint

To check whether your node is synchronized with the leader, there's a built-in endpoint at port `5000` called `/node-sync`.  It returns a boolean flag `true` or `false` to indicate whether your node is caught up to the latest block, on par with the majority node-runners.

This endpoint can be used to feed into your favorite dashboard metrics (Grafana, CloudWatch, etc.) and trigger alarms (Healthchecks.io, UptimeRobot, PagerDuty, webhooks into Discord, etc.) that can to help monitor your node operations.  If you're running a node service to host the RPC endpoint on port `9500`, this will be a great way to check the health of your nodes behind a load balancer and take unhealthy nodes out of rotation.
