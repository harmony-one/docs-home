# Using Node.sh \(deprecated\)

{% hint style="warning" %}
This option is **deprecated** and is **not supported** anymore. Please update your node [Using Node Binary](using-binary.md).
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

Before we proceed to next steps we need to download the necessary files:

{% tabs %}
{% tab title="Mainnet" %}
```bash
curl -LO https://harmony.one/node.sh && chmod +x node.sh
./node.sh -d && mv staging/* ./
```
{% endtab %}

{% tab title="Testnet" %}
```bash
curl -LO https://harmony.one/node.sh && chmod +x node.sh
./node.sh -d -N testnet && mv staging/* ./
```
{% endtab %}
{% endtabs %}

Check the Binary CLI and node.sh version that was downloaded:

```text
./harmony -V
./node.sh -v
```

## 4. Restart Systemd Service

```bash
sudo service harmony restart
```

To check your node follow instructions on [Checking A Node](../checking-node-status.md).

