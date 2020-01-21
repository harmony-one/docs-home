# Ledger Nano S With CLI

## Get everything together

Using Harmony hardware wallet on the Ledger Nano S requires a few things. You will need:

* Your Ledger Nano S
* The Harmony app installed on your Nano S
* The [harmony CLI app](https://docs.harmony.one/sdk-wiki/command-line-interface/using-the-harmony-cli-tool) on your computer to talk to the Nano S
* Familiarity with your computer's command-line interface \(CLI\).

## Download CLI 

_Please use the_ [_following instructions_](https://docs.harmony.one/home/wallet-guides/harmony-cli/download-setup) _to download CLI to use  Ledger Nano S ._

## Install Ledger Nano S Firmware In Debugging Mode

_This is ONLY for wallet developers / testers. Other users please download firmware through Ledger Live._

_Please use the_ [_following instructions_](https://docs.harmony.one/home/wallet-guides/ledger/install-and-setup) _to install Ledger Nano S firmware in Debugging mode._ 

## Display the Harmony ONE address for Ledger Nano S

As Ledger Nano S is connected to PC/Mac through USB, super user's permission is needed to open the USB. To use the Ledger Nano S hardware wallet, run harmony CLI **under sudo** and **\*\*use command** keys list --ledger\*\*

```text
./hmy.sh keys list --ledger
```

After running the keys command with --ledger option, the following GUI will be displayed on Ledger Nano S LED screen:

![](../../.gitbook/assets/assets_-llydmt-wp5uywcf_tmw_-lp17w8qgssywueqc8hm_-lp1qqkolza7pg6qmfeo_1assets_-llydmt-wp5uywcf_tmw.jpg)

There are two buttons on top of Ledger Nano, click the right one to continue \(or click the left one to cancel\). After that, the following address will be shown on Ledger Nano S LED screen:‌

![](../../.gitbook/assets/assets_-llydmt-wp5uywcf_tmw_-lp17w8qgssywueqc8hm_-lp1qtqgdj6cr36tkyqq_2.jpg)

As the address is longer than the LED screen, you can use the top two button to shift the address display to the left or side right side. Click both buttons to confirm the address and it should be same as displayed on PC/Mac terminal.‌

The entire process is shown in video below:

{% embed url="https://youtu.be/m5RLYGWosuk" caption="" %}

## Display token balance for Ledger Nano S <a id="display-token-balance-for-ledger-nano-s"></a>

Balance on any Harmony wallet addresses can be displayed using CLI with command **balances** using the following command line options:

```text
./hmy.sh balances --node=[server_address] [address]
```

Here \[server\_address\] is the server address for either Mainnet or Testnet and \[address\] is the Harmony wallet address.‌

**Query balance on Mainnet**

```text
./hmy.sh balances --node="https://api.s0.t.hmny.io" [address]
```

‌**Query balance on Devnet**

```text
./hmy.sh balances --node="https://api.s0.pga.hmny.io" [address]
```

### Query balance on Testnet <a id="query-balance-on-betanet-testnet"></a>

```text
./hmy.sh balances --node="https://api.s0.b.hmny.io" [address]
```

## Token transfer using Ledger Nano S

To send token from Ledger Nano S to another wallet account, we need Ledger Nano S hardware to sign the transaction with private key inside Ledger Nano S hardware. The CLI command **transfer --ledger** should be called with sudo permission:

```d
./hmy.sh transfer --ledger --node=[server_addr] \
  --chain-id=[mainnet|testnet|devnet] --from [from_addr] --to [to_addr] --amount [value] \
  --from-shard [shard_id] --to-shard [shard_id]
```

\[from\_addr\] is the wallet address for Ledger Nano S. Please note that \[from\_addr\] must match with Ledger Nano S's address, otherwise the transaction will fail.  
\[to\_addr\] is the receiver's wallet addresses.  
\[value\] is the amount of ONE tokens to transfer.  
\[shard\_id\] is a numeric value for shard ID, the value depends on Mainnet \(0,1,2,3\) or Testnet\) \(0,1,2\).

Please note that you will need to unlock Ledger Nano S, and confirm the transaction parameters on Ledger Nano S.

The LED display on Nano S is shown as below :‌

Click the right button to start signing the transaction

![](../../.gitbook/assets/assets_-llydmt-wp5uywcf_tmw_-lp1rbqypgiebehfw8of_-lp1fc7z1fvyt5c5rjal_1.jpg)

Check and confirm the transfer to address is correct.

![](../../.gitbook/assets/assets_-llydmt-wp5uywcf_tmw_-lo6dy17b06jv4usf0x9_-lo6eqqlsb2bdwimq2ri_3.jpg)

Check and confirm the amount is correct.

![](../../.gitbook/assets/assets_-llydmt-wp5uywcf_tmw_-lo6dy17b06jv4usf0x9_-lo6ess-qahgw53hl09s_4.jpg)

Check and confirm the source shard ID is correct.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6ewoJRmrEgmFneCVn%2F5.jpg?alt=media&token=691a919a-c841-4d41-bfe9-a3d658ab2e9e)

Check and confirm the destination shard ID is correct.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlYdMT-Wp5uYwcF_tMW%2F-Lo6dy17b06JV4uSf0x9%2F-Lo6eyZo-Z2Dia94jFx3%2F6.jpg?alt=media&token=1da33a34-7a21-4572-8b36-f93e90563a73)

Detailed process is shown in video below:

\_\_



{% embed url="https://youtu.be/feRpGW1seQI" %}

