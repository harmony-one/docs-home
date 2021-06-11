# Using Node Binary

## 1. Backup Files

Create a folder called "`backup`" in case it does not exist:

```bash
mkdir -p backup
```

Backup the `harmony` binary file:

```bash
cp harmony backup
```

## 2. Download Node Binary

Before we proceed to next steps we need to download the node binary first:

{% tabs %}
{% tab title="Mainnet" %}
```bash
curl -LO https://harmony.one/binary && mv binary harmony && chmod +x harmony
```
{% endtab %}

{% tab title="Testnet" %}
```bash
curl -LO https://harmony.one/binary_testnet && mv binary_testnet harmony && chmod +x harmony
```
{% endtab %}
{% endtabs %}

Check the node binary version that was downloaded:

```text
./harmony -V
```

## 3. Restart Systemd Service

```bash
sudo service harmony restart
```

To check your node follow instructions on [Checking A Node](../checking-node-status.md).

