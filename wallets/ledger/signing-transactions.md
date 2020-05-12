# Using HMY CLI

## Download & Setup HMY

To interact with your Ledger device using the HMYC CLI, please click [here](https://docs.harmony.one/home/wallets/harmony-cli/download-setup) to download and configure it first.

## Interacting with Ledger

{% hint style="success" %}
When using Ledger with HMY CLI, the only difference here is that you have to add parameter `--ledger`on every command.
{% endhint %}

With that in mind, you can run any other command like [sending transactions](https://docs.harmony.one/home/wallets/harmony-cli/send-tx), [querying balances](https://docs.harmony.one/home/wallets/harmony-cli/querying-balances) or [querying the blockchain](https://docs.harmony.one/home/wallets/harmony-cli/querying-the-blockchain) via HMY CLI using your Ledger.

{% hint style="warning" %}
Make sure HMY CLI is being run with super user permissions when interacting with Ledger.
{% endhint %}

Below, are two practical examples on how to interact with your Ledger device.

### Displaying your Ledger Wallet Address

For example, if you want to show your Ledger address you would simply run:

#### Using the Binary:

```text
./hmy keys list --ledger
```

#### Using the Shell Wrapper:

```text
./hmy.sh -- keys list --ledger
```

### Displaying your Ledger Wallet Balance

#### Using the Binary:

```bash
./hmy balances --node="<endpoint-address>" <ONE-address> --ledger
```

#### Using the Shell Wrapper:

```bash
./hmy.sh -- balances --node="<endpoint-address>" <ONE-address> --ledger
```

For a complete reference of all commands available, please check the HMY CLI [cookbook](https://docs.harmony.one/home/wallets/harmony-cli/cookbook).

