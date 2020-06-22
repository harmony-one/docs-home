---
description: Some steps for troubleshooting your AutoNode
---

# Troubleshoot

{% hint style="success" %}
If you encounter any issue you cannot solve, feel free to reach out to us at **autonode@harmony.one**.
{% endhint %}

## Inspect AutoNode logs

All AutoNode generated logs are saved in `$HOME/.hmy` when you execute the following command:

```bash
ls $HOME/.hmy/*.log
```

You should see 2 files, `autonode_monitor.log` and `autonode_node.log`. Inspect those two files with your favorite command-line editor \(i.e: `vim`\) to see where things might have gone wrong. 

You might also find it useful to inspect the Harmony Node logs. You can do so with the following command:

```bash
vim $HOME/harmony_node/latest/zero*.log
```

> You can change the `vim` part of the command for your favorite text editor.

## Node failed to start

A symptom of this is seeing an error to connect to `http://localhost:9500/`.   
You can inspect what went wrong with the following command:

```bash
auto-node node log
auto-node node status
```

A common issue is that your machine will not have enough disk space.   
You can check your disk space usage with the following command:

```bash
df -H 
```

> If your `use%` is at 95-100% and your node failed to start, you probably have insufficient disk space. Look into how to increase your disk space on your cloud provider.

You can also try to reboot your AutoNode with:

```bash
auto-node kill
auto-node run <params>
```

> Substitute `<params>` with whatever run params you want to use

## Fixing Signing Issues

Sometimes the Harmony Node may have some signing issues. In this case, we have found it best to just restart the Node. You can do so by first killing AutoNode:

```bash
auto-node kill
```

Then restarting AutoNode with whatever your initial run command was. For example, one could run it with:

```bash
auto-node run --expose-rpc
```

{% hint style="warning" %}
**DO NOT** re-run with the `--clean` or `--fast-sync` options as they will most likely _regress_ your block height to the last snapshotted DB.
{% endhint %}

## Restart the Harmony Node

You can restart the Harmony Node service with the following command:

```bash
auto-node node restart
```

You can check the status of the service with the following command:

```bash
auto-node node status
```

You can fetch the Harmony Node version with the following command:

```bash
auto-node node version
```

## Restart the AutoNode Monitor

You can restart the monitor service with the following command:

```bash
auto-node monitor restart
```

You can check the status of the service with the following command:

```bash
auto-node monitor status
```

## Re-Authenticating your validator wallet

If your encrypted passphrase for your validator is ever invalidated, you can re-encrypt and save it with the following command:

```bash
auto-node auth-wallet
```

## Optimize Operating System

You can choose to optimize your operating system for running a harmony node. The optimizations, or tunes, are made to keep your node safe but also lifts some default restrictions. Here is the command to tune your OS with AutoNode:

```bash
auto-node tune kernel --save
```

> This will tune the kernel and the `--save` option will make it persistant. If you do not have the `--save` option, the tunes will only last untill the system is rebooted \(by you or your VPS\).  
>   
> Note that all the tunes will be displayed and confirmation asked before applying the tunes.

You can also tune/optimize your network settings with the following command:

```bash
auto-node tune network --save
```

## Restoring Operating System from Optimization

If you want to revert the optimization/tune applied by AutoNode, you can do so by running the following command:

```bash
auto-node tune restore
```

> Note that you can run the command muliple times to restore previous tunes chronologically. Moveover, the restored tunes will be displayed and a confirmation will be asked before applying the restoreation.

## Fresh Install

First, remove all of the AutoNode files. You can do so with the following command:

```bash
auto-node kill
systemctl --user disable autonoded@node.service
systemctl --user disable autonoded@monitor.service
rm -rf ~/.hmy
rm -rf ~/harmony_node
rm -rf ~/harmony_wallet_pass
rm -f ~/harmony_validator_config.json
rm -f ~/bin/auto-node
rm -f ~/bin/autonode-service.py
```

After, you can re-install AutoNode from fresh using the steps in the Install & Run section.







