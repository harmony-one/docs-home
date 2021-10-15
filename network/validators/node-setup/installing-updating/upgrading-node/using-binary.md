# Using Node Binary

## Validator Nodes

### 1. Backup Files

Create a folder called "`backup`" in case it does not exist:

```bash
mkdir -p backup
```

Backup the `harmony` binary file:

```bash
cp harmony backup
```

### 2. Download Node Binary

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

```
./harmony -V
```

### 3. Restart Systemd Service

```bash
sudo service harmony restart
```

To check your node follow instructions on [Checking A Node](../checking-node-status.md).

## Non-Validating/Explorer Nodes

{% hint style="warning" %}
Requirements for Explorer Nodes have changed. Check [here](../../../server-setup/requirements.md#explorer-node-recommendation) before going forward.
{% endhint %}

### 1. Download New Explorer DB

```bash
wget https://s3.us-west-1.amazonaws.com/pub.harmony.one/mainnet.archival/harmony_storage_db_0/explorer_storage_s0.tar.gz
```

### 2. Backup Files

```bash
mkdir -p backup
cp harmony backup
```

### 3. Download Node Binary and Stop Service

```bash
curl -LO https://harmony.one/binary && mv binary harmony && chmod +x harmony
sudo service harmony stop
```

### 4. Backup Old Explorer DB

```bash
mv explorer_storage_0.0.0.0_9000 explorer_storage_0.0.0.0_9000.backup
```

### 5. Extract New DB

```bash
tar xvzf explorer_storage_s0.tar.gz
```

### 6. Change RPC Rate Limit

Change `harmony.conf` file and add make sure the RPC Rate Limit is set to at least 50000:

```bash
[RPCOpt]
  RequestsPerSecond = 50000
```

### 7. Start Systemd Service

```bash
sudo service harmony start
```

{% hint style="info" %}
DB migration should take no more than a few hours to conclude.
{% endhint %}
