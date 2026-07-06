---
description: The Harmony CLI tool is used to interact with the Harmony blockchain.
---

# 1. HMY CLI Download

{% hint style="danger" %}
Make sure **NOT** to run the Node Setup with the `root` user. We recommend creating a new user called `harmony` for the Node Setup and giving it root level access.
{% endhint %}

{% hint style="info" %}
Throughout this guide, we will use the following syntax:

* `./hmy`:  This is the CLI program
* `./hmy.sh` -- : This is the command to use the CLI with a shell wrapper (for macOS)
* `<argument>`: This is a required argument
* `[argument]`: This is an optional argument
* `/` : This is a line break, used to break up a line while writing a command
{% endhint %}

## Download Harmony CLI tool

### 0. Check you CPU architecture and operation system

{% code expandable="true" %}
```bash
uname -ms
```
{% endcode %}

Based on the output go to the appropriate section of this manual:

* `x86_64 Linux` -> [#id-1.-gnu-linux-on-the-amd64-platform](hmy-cli-download.md#id-1.-gnu-linux-on-the-amd64-platform "mention")
* `arm64 Darwin` -> [#id-2.-gnu-linux-and-macos-on-the-arm64-platform](hmy-cli-download.md#id-2.-gnu-linux-and-macos-on-the-arm64-platform "mention")
* `aarch64 Linux` ->  [#id-2.-gnu-linux-and-macos-on-the-arm64-platform](hmy-cli-download.md#id-2.-gnu-linux-and-macos-on-the-arm64-platform "mention")
* `x86_64 Darwin` ->  [#id-2.-for-macos](hmy-cli-download.md#id-2.-for-macos "mention")

### 1. GNU/Linux on the amd64 platform

{% code title="Old way, backward compatible" %}
```bash
curl -LO https://harmony.one/hmycli && \
    mv hmycli hmy && \
    chmod +x hmy && \
     ./hmy cookbook
```
{% endcode %}

{% code title="New way, directly from the repo " expandable="true" %}
```bash
# set it to the tag value, if need
# TAG="v2026.0.0" && \
TAG="${TAG:-latest}" && \
curl -LO "https://github.com/harmony-one/go-sdk/releases/${TAG}/download/hmy-amd64" && \
    mv hmy-amd64 hmy && \
    chmod 744 hmy &&
    ./hmy cookbook
```
{% endcode %}

### 2. GNU/Linux and MacOS on the arm64 platform

```bash

TAG="${TAG:-latest}" && \
curl -LO "https://github.com/harmony-one/go-sdk/releases/${TAG}/download/hmy-arm64" && \
    mv hmy-arm64 hmy && \
    chmod 744 hmy &&
    ./hmy cookbook
```

### 3. MacOS on Intel based chips <a href="#id-2.-for-macos" id="id-2.-for-macos"></a>

```bash
curl -O https://raw.githubusercontent.com/harmony-one/go-sdk/master/scripts/hmy.sh
chmod u+x hmy.sh
./hmy.sh -d
```

Now you can use `hmy.sh` as a wrapper over `hmy` and you should assume that all references to `hmy` in these documents refer to `hmy.sh`. For example, the command `./hmy` becomes `./hmy.sh --` .

{% hint style="warning" %}
Note that since `hmy` is not statically linked, you cannot arbitrarily move `hmy.sh` to anywhere on your filesystem like you could with a single binary.
{% endhint %}

## Run the hmy cli

On the GNU/Linux, calling the `cookbook` would look like this:

```bash
./hmy --node="https://api.s0.t.hmny.io" cookbook
```

And on the **Intel** MacOS would look like:

```bash
./hmy.sh -- --node="https://api.s0.t.hmny.io" cookbook
```

## Cookbook output

```bash
Cookbook of Usage

Note:

1) Every subcommand recognizes a '--help' flag
2) If a passphrase is used by a subcommand, one can enter their own passphrase interactively
   with the --passphrase option. Alternatively, one can pass their own passphrase via a file
   using the --passphrase-file option. If no passphrase option is selected, the default
   passphrase of '' is used.
3) These examples use Shard 0 of Mainnet as argument for --node

Examples:

1.  Check account balance on given chain
./hmy --node=https://api.s0.t.hmny.io balances <SOME_ONE_ADDRESS>

2.  Check sent transaction
./hmy --node=https://api.s0.t.hmny.io blockchain transaction-by-hash <SOME_TX_HASH>

3.  List local account keys
./hmy keys list

4.  Sending a transaction (waits 40 seconds for transaction confirmation)
./hmy --node=https://api.s0.t.hmny.io transfer \
    --from <SOME_ONE_ADDRESS> --to <SOME_ONE_ADDRESS> \
    --from-shard 0 --to-shard 1 --amount 200 --passphrase

5.  Sending a batch of transactions as dictated from a file (the `--dry-run` options still apply)
./hmy --node=https://api.s0.t.hmny.io transfer --file <PATH_TO_JSON_FILE>
Check README for details on json file format.

6.  Check a completed transaction receipt
./hmy --node=https://api.s0.t.hmny.io blockchain transaction-receipt <SOME_TX_HASH>

7.  Import an account using the mnemonic. Prompts the user to give the mnemonic.
./hmy keys recover-from-mnemonic <ACCOUNT_NAME> --passphrase

8.  Import an existing keystore file
./hmy keys import-ks <PATH_TO_KEYSTORE_JSON>

9.  Import a keystore file using a secp256k1 private key
./hmy keys import-private-key <secp256k1_PRIVATE_KEY>

10. Export a keystore files secp256k1 private key
./hmy keys export-private-key <ACCOUNT_ADDRESS> --passphrase

11. Generate a BLS key then encrypt and save the private key to the specified location.
./hmy keys generate-bls-key --bls-file-path <PATH_FOR_BLS_KEY_FILE>

12. Create a new validator with a list of BLS keys
./hmy --node=https://api.s0.t.hmny.io staking create-validator --amount 10 --validator-addr <SOME_ONE_ADDRESS> \
    --bls-pubkeys <BLS_KEY_1>,<BLS_KEY_2>,<BLS_KEY_3> \
    --identity foo --details bar --name baz --max-change-rate 0.1 --max-rate 0.1 --max-total-delegation 10 \
    --min-self-delegation 10 --rate 0.1 --security-contact Leo  --website harmony.one --passphrase

13. Edit an existing validator
./hmy --node=https://api.s0.t.hmny.io staking edit-validator \
    --validator-addr <SOME_ONE_ADDRESS> --identity foo --details bar \
    --name baz --security-contact EK --website harmony.one \
    --min-self-delegation 0 --max-total-delegation 10 --rate 0.1\
    --add-bls-key <SOME_BLS_KEY> --remove-bls-key <OTHER_BLS_KEY> --passphrase

14. Delegate an amount to a validator
./hmy --node=https://api.s0.t.hmny.io staking delegate \
    --delegator-addr <SOME_ONE_ADDRESS> --validator-addr <VALIDATOR_ONE_ADDRESS> \
    --amount 10 --passphrase

15. Undelegate to a validator
./hmy --node=https://api.s0.t.hmny.io staking undelegate \
    --delegator-addr <SOME_ONE_ADDRESS> --validator-addr <VALIDATOR_ONE_ADDRESS> \
    --amount 10 --passphrase

16. Collect block rewards as a delegator
./hmy --node=https://api.s0.t.hmny.io staking collect-rewards \
    --delegator-addr <SOME_ONE_ADDRESS> --passphrase

17. Check elected validators
./hmy --node=https://api.s0.t.hmny.io blockchain validator elected

18. Get current staking utility metrics
./hmy --node=https://api.s0.t.hmny.io blockchain utility-metrics

19. Check in-memory record of failed staking transactions
./hmy --node=https://api.s0.t.hmny.io failures staking

20. Check which shard your BLS public key would be assigned to as a validator
./hmy --node=https://api.s0.t.hmny.io utility shard-for-bls <BLS_PUBLIC_KEY>

21. Vote on a governance proposal on https://snapshot.org
./hmy governance vote-proposal --space=[harmony-mainnet.eth] \
	--proposal=<PROPOSAL_IPFS_HASH> --proposal-type=[single-choice] \
	--choice=<VOTING_CHOICE(S)> --app=[APP] --key=<ACCOUNT_ADDRESS_OR_NAME>
PS: key must first use (hmy keys import-private-key) to import

22. Enter console
./hmy command --net=testnet
```

## Troubleshooting <a href="#troubleshooting" id="troubleshooting"></a>

Frequently encountered errors:

```bash
./hmy cookbook

-bash: ./hmy: cannot execute binary file: Exec format error
​#Make sure you downloaded the right version for your OS.
```
