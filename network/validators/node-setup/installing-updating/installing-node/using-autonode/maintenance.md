---
description: Steps for maintaining your node with AutoNode.
---

# Maintenance

## Edit Validator config

After your validator is created, you can edit your validator config with the following command:

```bash
auto-node edit-config
```

> This will open up a Nano session to edit the config. After you do your edits, save it by pressing `Ctrl+X `then `Y`.

After you finish editing, you will be asked to update the config on-chain. If you say yes, AutoNode will send an edit validator transaction to update your validator.&#x20;

{% hint style="warning" %}
Note that the following are the **ONLY** fields that can be edited on-chain:\
`"details", "identity", "name", "security-contact", "website", "max-total-delegation", "min-self-delegation", "rate"`
{% endhint %}

## Deactivate Validator

You can deactivate your validator if you would like to not get elected the following epoch. You can do so with the following command:

```bash
auto-node deactivate
```

## Activate Validator

When you are ready to get elected and sign the following epoch, you can activate your validator with the following command:

```bash
auto-node activate
```

## Inspect the Harmon Node logs

Node logs are saved in the following directory: `$HOME/harmony_node/latest`

You can view the logs with the following command:

```bash
vim $HOME/harmony_node/latest/zero*.log
```

## Inspect the Harmony Node service logs

The Harmony Node is ran as a [service](https://www.linux.com/news/introduction-services-runlevels-and-rcd-scripts/#:\~:text=A%20Linux%20service%20is%20an,services%20until%20you%20need%20them.\&text=This%20is%20the%20most%20common%20Linux%20init%20system.), you can inspect the logs for the service with the following command:

```bash
auto-node node journal -e
```

## Inspect the AutoNode monitor service logs

Similar to the Harmony Node, the monitor is ran as a service and you can inspect the logs for the service with the following command:

```bash
auto-node monitor journal -e
```
