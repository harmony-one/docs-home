# Using Node.sh

{% hint style="warning" %}
This option will be **deprecated** and is **not recommended** anymore. Please setup your node [Using Binary CLI](../installing-node/using-binary-cli.md) or [Using AutoNode](../installing-node/using-autonode/) and use the upgrade tutorials accordingly.

If you are still using **Tmux** to run your node or running  **node.sh via Systemd**, we recommend that you migrate as soon as possible to one of the options mentioned above.
{% endhint %}

## 1. Stop Systemd Service

```bash
sudo service harmony stop
```

## 2. Backup Files

Create a folder called "`backup`" in case it does not exist:

```bash
mkdir -p backup
```

Backup both `node.sh` and `harmony` binary file:

```bash
cp {node.sh,harmony} backup
```

## 3. Download Node.sh

Before we proceed to next steps we need to download `node.sh` , extract files into the `staging` folder and then move them into the previous folder:

```bash
curl -LO https://harmony.one/node.sh && chmod +x node.sh
./node.sh -d && mv staging/* ./
```

Check the Binary CLI and node.sh version that was downloaded:

```text
./harmony -V
./node.sh -v
```

## 4. Restart Systemd Service

```bash
sudo service harmony restart
```

