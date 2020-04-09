# Creating A Validator

{% hint style="info" %}
Wait for your node to sync before creating a validator.

Check your current block height with `./hmy blockchain latest-header`.

Check chain block height with `./hmy blockchain latest-header --node=[endpoint]`.
{% endhint %}

## Getting ONE Tokens <a id="getting-one-tokens"></a>

In order to continue and create your validator, you will need to have ONE tokens in your **Shard 0** balance. To get tokens from our Faucet smart contract, use the following command:

{% tabs %}
{% tab title="Open Staking Testnet" %}
```bash
curl https://faucet.os.hmny.io/fund?address=[ONE ADDRESS]
```
{% endtab %}

{% tab title="Partner Testnet" %}
```bash
curl -X GET https://faucet.ps.hmny.io/fund?address=[ONE ADDRESS]
```
{% endtab %}
{% endtabs %}

The faucet will fund 11,000 ONE tokens on Shard 0, per account, per hour.

**Other option to get tokens is to use the faucet:** [https://faucet.os.hmny.io/](https://faucet.os.hmny.io/)

## Creating a Validator <a id="creating-a-validator"></a>

{% tabs %}
{% tab title="Open Staking Testnet" %}
```bash
./hmy --node=https://api.s0.os.hmny.io staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 10000 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name "[NAME]" --identity "[IDENTITY]" --details "DETAILS" \
    --security-contact "CONTACT" --website "YOUR-WEBSITE.COM" \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100000000 --min-self-delegation 100000 --passphrase
```
{% endtab %}

{% tab title="Partner Testnet" %}
```bash
./hmy --node=https://api.s0.ps.hmny.io staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 100000 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name "[NAME]" --identity "[IDENTITY]" --details "DETAILS" \
    --security-contact "CONTACT" --website "YOUR-WEBSITE.COM" \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100000000 --min-self-delegation 100000 --passphrase
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Copy the entire command. **Extra white spaces in the command could cause errors.**

Name, identity, details, security-contact and website need to be put in double quotes if there are more than one word separated by space \(example --name "John the validator"\).
{% endhint %}

The CLI will prompt you to enter your BLS key file password.

`--validator-addr` is the address that will receive the rewards

`--amount` is the initial amount you want to stake

`--bls-pubkeys` takes a comma-separated list of BLS public keys \(not files\)

`--name` will be the name displayed on the Staking Explorer

`--identity` is additional information for the validator

`--details` is the description of the validator

`--security-contact` is additional information for the validator

`--website` will be displayed on the Staking Explorer

`--max-change-rate` is the maximum increase the validator can add to their commission rate

`--max-rate` is the maximum commission rate that the validator can set

`--rate` is the starting commission rate of the validator

`--max-total-delegation` is the maximum amount that can be delegated to this validator

`--min-self-delegation` is the minimum amount of stake the validator must delegate to itself

{% hint style="danger" %}
`--max-rate` and `--max-change-rate` cannot be changed later.

`--min-self-delegation` has to be at least 10,000 ONE.
{% endhint %}

### When does the validator become active? <a id="when-does-the-validator-become-active"></a>

On the Open Staking Testnet, a validator will be set to active at the next epoch. You can see the time until the next epoch on the [Staking Explorer](https://staking.harmony.one/portfolio).

Once your validator is active and has been elected, the validator will receive rewards and you will be able to see "BINGO" in the logs.

```text
tail -n 1000 latest/zerolog-validator-*.log | grep -i BINGO
```

Example output below:

```text
{"level":"info","port":"9000","ip":"213.136.79.89","blockNum":3916,"epochNum":26,"ViewId":3916,"blockHash":"0xca71fc9aa92f694f664aa34d7e3e82cf9b678e3a062d3bbbabebfbc5f0598d84","numTxns":0,"numStakingTxns":0,"caller":"/mnt/jenkins/workspace/harmony-release/harmony/node/node_handler.go:359","time":"2019-12-11T14:49:08.983338784+01:00","message":"BINGO !!! Reached Consensus"}
```

## Checking Validator Information <a id="checking-validator-information"></a>

Use the below command to check your validator information

{% tabs %}
{% tab title="Open Staking Testnet" %}
```bash
./hmy --node="https://api.s0.os.hmny.io" blockchain validator information [ONE ADDRESS]
```
{% endtab %}

{% tab title="Partner Testnet" %}
```bash
./hmy --node="https://api.s0.ps.hmny.io" blockchain validator information [ONE ADDRESS]
```
{% endtab %}
{% endtabs %}

Example output below:

```text
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "current-epoch-signing-percent": {
      "current-epoch-signed": 0,
      "current-epoch-to-sign": 2,
      "percentage": "0.000000000000000000"
    },
    "current-epoch-voting-power": [
      {
        "effective-stake": "9665865000000000000000.000000000000000000",
        "shard-id": 0,
        "voting-power-adjusted": "0.044606060606060606",
        "voting-power-raw": "0.139393939393939394"
      }
    ],
    "validator": {
      "address": "one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd",
      "availability": {
        "num-blocks-signed": 0,
        "num-blocks-to-sign": 75
      },
      "bls-public-keys": [
        "bf3c6ec088cd66fdb540860bd6505b272230164b0510d5f470042d47118d4c8bbe005d28e5de5e489fa22e4ca450c080"
      ],
      "creation-height": 3675,
      "delegations": [
        {
          "amount": 2.5e+22,
          "delegator-address": "one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd",
          "reward": 0,
          "undelegations": []
        }
      ],
      "details": "Soph P-OPS Validator node",
      "epos-eligibility-status": "active",
      "identity": "Soph",
      "last-epoch-in-committee": 50,
      "max-change-rate": "0.050000000000000000",
      "max-rate": "0.900000000000000000",
      "max-total-delegation": 1e+24,
      "min-self-delegation": 2000000000000000000,
      "name": "Soph P-OPS Validator node",
      "rate": "0.100000000000000000",
      "security-contact": "Soph",
      "update-height": 3675,
      "website": "soph.harmony.one"
    }
  }
}
```

{% hint style="warning" %}
If your validator does not sign 66% of the blocks in an epoch, the validator will be removed from the pool of eligible validators.

In order to be included in the pool again, you will have to use send an [Edit Validator transaction](creating-a-validator.md) with `--active true`.
{% endhint %}

