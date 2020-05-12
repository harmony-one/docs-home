# Ledger with HMY CLI

## Download & Setup HMY

To interact with your Ledger device using the HMYC CLI, please click [here](https://docs.harmony.one/home/wallets/harmony-cli/download-setup) to download and configure it first.

## Interacting with Ledger

{% hint style="success" %}
When using Ledger with HMY CLI, the only difference here is that you have to add parameter `--ledger`on every command.
{% endhint %}

With that in mind, you can run any other command via HMY CLI using your Ledger.

{% hint style="warning" %}
Make sure HMY CLI is being run with super user permissions when interacting with Ledger.
{% endhint %}

Below, are a few practical examples on how to interact with your Ledger device.

### 1. Displaying your Address

For example, if you want to show your Ledger address you would simply run:

#### Using the Binary:

```text
./hmy keys list --ledger
```

#### Using the Shell Wrapper:

```text
./hmy.sh -- keys list --ledger
```

### 2. Displaying your Balance

#### Using the Binary:

```bash
./hmy balances --node="<endpoint-address>" <ONE-address> --ledger
```

#### Using the Shell Wrapper:

```bash
./hmy.sh -- balances --node="<endpoint-address>" <ONE-address> --ledger
```

### 3. Sending Transactions

#### Using the Binary:

```bash
./hmy transfer --node="<endpoint_address>" \
 --from <ONE_address> --to <ONE_address> \
 --from-shard <shard> --to-shard <shard> \
 --amount <amount> --chain-id <chain-id> --passphrase --ledger
```

#### Using the Shell Script:

```bash
./hmy.sh -- transfer --node="<endpoint_address>" \
 --from <ONE_address> --to <ONE_address> \
 --from-shard <shard> --to-shard <shard> \
 --amount <amount> --chain-id <chain-id> --passphrase --ledger
```

For a complete reference of all commands available, please check the HMY CLI [cookbook](https://docs.harmony.one/home/wallets/harmony-cli/cookbook).

