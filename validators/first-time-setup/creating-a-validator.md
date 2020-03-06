# Creating A Validator

## Getting ONE Tokens <a id="getting-one-tokens"></a>

In order to continue and create your validator, you will need to have ONE tokens in your Shard 0 balance. To get tokens from our Faucet smart contract, use the following command:

```text
curl -X GET https://faucet.os.hmny.io/fund?address=[ONE ADDRESS]
```

The faucet will fund 10,000 ONE tokens on Shard 0, per account, per hour.

## Creating a Validator <a id="creating-a-validator"></a>

```text
./hmy --node="https://api.s0.os.hmny.io" staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 10 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name [NAME] --identity [IDENTITY] --details "DETAILS" \
    --security-contact CONTACT --website YOUR-WEBSITE.COM \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100 --min-self-delegation 10 --passphrase
```

{% hint style="info" %}
Copy the entire command. Extra white spaces in the command could cause errors.
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

`--min-self-delegation` has to be at least 1 ONE.
{% endhint %}

### When does the validator become active? <a id="when-does-the-validator-become-active"></a>

On the Open Staking Testnet, a validator will be set to active at the next epoch. You can see the time until the next epoch on the [Staking Explorer](https://staking.harmony.one/portfolio).

Once your validator is active and has been elected, the validator will receive rewards and you will be able to see "BINGO" in the logs.

```text
tail latest/zerolog-validator-*.log | grep -i BINGO
```

Example output below:

```text
{"level":"info","port":"9000","ip":"213.136.79.89","blockNum":3916,"epochNum":26,"ViewId":3916,"blockHash":"0xca71fc9aa92f694f664aa34d7e3e82cf9b678e3a062d3bbbabebfbc5f0598d84","numTxns":0,"numStakingTxns":0,"caller":"/mnt/jenkins/workspace/harmony-release/harmony/node/node_handler.go:359","time":"2019-12-11T14:49:08.983338784+01:00","message":"BINGO !!! Reached Consensus"}
```

## Checking Validator Information <a id="checking-validator-information"></a>

Use the below command to check your validator information

```text
./hmy --node=https://api.s0.os.hmny.io/ blockchain validator information [ONE ADDRESS]
```

Example output below:

```text
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "active": true,
    "address": "one1tnnncpjdqdjyk7y4d9gaxrg9qk927ueqptmptz",
    "availability": {
      "num-blocks-signed": 2683,
      "num-blocks-to-sign": 2685
    },
    "banned": false,
    "bls-public-keys": [
      "6706f27d2a28d167f85d54c7fd8ee1f6177cde266f0e1669e0e90d8cb377937135fc5daa0950f339c6e9b0177f326c84"
    ],
    "creation-height": 181,
    "delegations": [
      {
        "amount": 9e+22,
        "delegator-address": "one1tnnncpjdqdjyk7y4d9gaxrg9qk927ueqptmptz",
        "reward": 5.726533846121452e+22,
        "undelegations": []
      }
    ],
    "details": "Shard0Validator",
    "identity": "J",
    "last-epoch-in-committee": 39,
    "max-change-rate": "0.100000000000000000",
    "max-rate": "0.500000000000000000",
    "max-total-delegation": 2e+23,
    "min-self-delegation": 1000000000000000000,
    "name": "R",
    "rate": "0.100000000000000000",
    "security-contact": "J",
    "update-height": 181,
    "website": "harmony.one"
  }
}
```

{% hint style="warning" %}
If your validator does not sign 66% of the blocks in an Epoch, the validator will be removed from the pool of eligible validators.

In order to be included in the pool again, you will have to use send an [Edit Validator transaction]() with `--active true`.
{% endhint %}

