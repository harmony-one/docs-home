---
description: Reasons why your validator is not elected & how to get elected.
---

# My validator is not elected

## How is the committee chosen?

Harmony operates with Effective Proof of Stake \(EPoS\) to keep the network security from collecting in the hands of a few validators. You can find our full Medium article on EPoS [here](https://harmony.one/epos)!

TL;DR Validators are elected based on their **effective** stake, instead of their absolute stake. The effective stake is calculated based on the median stake in the network. The top 480 BLS keys with the highest effective stake will be elected for the epoch.

## **Why am I not elected?**

Non election in the EPOS committee are caused by two main issues :

1. Your validator profile needs to have satisfactory conditions
   1. current total stake has to be among the 320 highest stake before the change of next epoch
   2. Active flag needs to be true
   3. The numbers of block signed per epoch needs to be above 66%
2. Your node needs to be functional
   1. Fully synced
   2. Signing blocks

## **Validator profile need to satisfy the below**

### Bidding for a place in the EPOS committee

#### Verify the median stake

{% tabs %}
{% tab title="CLI" %}
```bash
 ./hmy --node="https://api.s0.t.hmny.io" blockchain median-stake | grep median
    "epos-median-stake": "1550000000000000000000000.000000000000000000",

```
{% endtab %}

{% tab title="Staking Explorer" %}
go to : [https://staking.harmony.one/validators](https://staking.harmony.one/validators)  


![https://staking.harmony.one/validators](../../.gitbook/assets/image%20%28144%29.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The value returned by the CLI is in Atto, which is equivalent to Gwei in Ethereum.
{% endhint %}

#### Total delegation is above the median stake

Visit [https://staking.harmony.one/validators/](https://staking.harmony.one/validators/)&lt;youroneaccount&gt; 

Example : [https://staking.harmony.one/validators/one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd](https://staking.harmony.one/validators/one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd)

![Validator Total stake](https://lh4.googleusercontent.com/NLgZVG_11gM5bVMv-17Rwsjc8-TG7nTfXuDs6tdxtUbVFgtD0uNbx39GIDoGcUXEkJhmu9s2pDTBk88ZdrdVj_N5Lz_TVDHvivMBVOlrbwV1l2Kubs1NRTvnLMi5qXlCm79sP__k)

Your current total stake has to be among the 320 highest stake slots before the change of next epoch. For that, one way to make sure of it is to be near / above the median stake.

Being just above the last bidder would ensure your a place but it is risky as you might be outbid during the next election. 

If you are not above the median stake then time to ask for more delegation or delegate yourself more ONE token following this doc on [how to delegate more ONE token](../managing-your-validator/delegating-to-a-validator.md).

{% hint style="info" %}
Make sure your max-total-delegation is high enough and above the median stake so your added delegation work
{% endhint %}

#### **Your validator node** epos-eligibility-status **flag needs to be active**

Issue the command   
./hmy -n https://api.s0.t.hmny.io blockchain validator information \[VALIDATOR-ACCOUNT\] \| grep epos-status

```bash
./hmy --node="https://api.s0.t.hmny.io" blockchain validator information  one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd | grep epos-status
    "epos-status": "currently elected",      
```

If **not eligible**, update it to active via the command   
./hmy -n https://api.s0.t.hmny.io staking edit-validator --validator-addr &lt;ONE\_VALIDATOR\_ACCOUNT&gt; --active true --passphrase

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" staking edit-validator --validator-addr one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd --active true --passphrase
```
{% endtab %}
{% endtabs %}

**Finally check your signed blocked**

using the command  
./hmy -n https://api.s0.t.hmny.io blockchain validator information &lt;ONE\_VALIDATOR\_ACCOUNT&gt;

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" blockchain validator information one1u6c4wer2dkm767hmjeehnwu6tqqur62gx9vqsd
```
{% endtab %}
{% endtabs %}

and search for :

```text
    "current-epoch-performance": {
      "current-epoch-signing-percent": {
        "current-epoch-signed": 50,
        "current-epoch-signing-percentage": "0.500000000000000000",
        "current-epoch-to-sign": 100,
        "num-beacon-blocks-until-next-epoch": 28
      }
    },

```

For your validator to stay elected, you wanna make sure the current-epoch-signing-percentage is above 66% \(0.66\). 

To fix the above, we have to make sure the node is working correctly and below are few pointers

### Your node needs to be functional

#### Fully synced node

Compare your block height

```bash
 ./hmy blockchain latest-headers | grep block-number
```

{% hint style="danger" %}
If the above doesn’t work and you have an error message similar to this: _commit: v304-0e26945, error: dial tcp4 127.0.0.1:9500: connect: connection refused_   
It means the harmony node binary is not running. Please follow this documentation on [how to run the node](https://docs.harmony.one/validators/validator/first-time-setup/download-node-script).
{% endhint %}

and the network block height

{% tabs %}
{% tab title="Mainnet" %}
```bash
./hmy --node="https://api.s0.t.hmny.io" blockchain latest-headers | grep blockNumber 
```
{% endtab %}
{% endtabs %}

Make sure network height and your current height are very close or equal. Additionally if your node is validating for a

{% hint style="info" %}
the above command is for network height on shard 0, change s0 to s1, s2, .. to match yours in the api URL
{% endhint %}

When you are fully synced and your validator profile is satisfactory you should start having BINGOs in your validator log file at **epoch change**.

You can check BINGOs via this command

```bash
tail -f latest/zero*.log | grep BINGO
```

And you’ll notice in your validator information that you started signing blocks

```text
    "current-epoch-performance": {
      "current-epoch-signing-percent": {
        "current-epoch-signed": 60,
        "current-epoch-signing-percentage": "1.000000000000000000",
        "current-epoch-to-sign": 60,
        "num-beacon-blocks-until-next-epoch": 28
      }
    },
```

**If you fail** to sign blocks, verify your machine/vps doesn't have CPU/memory/hard disk/internet issues. When you fail to sign more than 66% of the blocks in an epoch, you’ll be kicked out from the committee

