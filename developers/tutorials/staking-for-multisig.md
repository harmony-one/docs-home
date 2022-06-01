---
description: >-
  This documentation explains how to do staking via your multisig safe using
  https://multisig.harmony.one.
---

# Staking for Multisig

### Pre-requisites

* Navitate to https://multisig.harmony.one
* Load your safe
* Have enough funds to stake
* Note down the validator address to which you plan on staking/unstaking

### Delegation (Staking)

1\. Navigate to "New Transaction" and select "Contract Interaction"

![](<../../.gitbook/assets/Screen Shot 2022-06-01 at 8.22.39 AM.png>)

2\. Enter `0x00000000000000000000000000000000000000FC` into the "Contract Address" field of the Contract Interaction form.

3\. Copy paste the text below into the ABI field in the Contract Interaction form

```
[
    {
      "inputs": [
        {
          "internalType": "address",
          "name": "delegatorAddress",
          "type": "address"
        },
        {
          "internalType": "address",
          "name": "validatorAddress",
          "type": "address"
        },
        {
          "internalType": "uint256",
          "name": "amount",
          "type": "uint256"
        }
      ],
      "name": "Delegate",
      "outputs": [],
      "stateMutability": "nonpayable",
      "type": "function"
    }
]
```

4\. Select "Delegate" from the drop-down.&#x20;

5\. Enter the delegator address (your multisig safe address) and validator address. Note that these have to be in the `0x` format and not `one1`. You can easily get the `0x` formatted address of your `one1` from [https://explorer.harmony.one](https://explorer.harmony.one) "Address Format" toggle on the top.

6\. Enter the amount of ONE to stake. Note that, you have to append 18 zeros to your number as the amount is expected in the `wei` units and not `ONE`. For example, if you want to stake 100 ONE, you will write 100000000000000000000 (notice the 18 zeros after 100).

![](<../../.gitbook/assets/Screen Shot 2022-06-01 at 8.41.24 AM.png>)

7\. Click on "Review", "Submit", and sign the transaction. Rest of the steps are usual multisig signing where all required parties sign this transaction.

### Undelegation (Unstaking)

1\. Navigate to "New Transaction" and select "Contract Interaction"

2\. Enter `0x00000000000000000000000000000000000000FC` into the "Contract Address" field of the Contract Interaction form.

3\. Copy paste the text below into the ABI field in the Contract Interaction form

```
[
    {
      "inputs": [
        {
          "internalType": "address",
          "name": "delegatorAddress",
          "type": "address"
        },
        {
          "internalType": "address",
          "name": "validatorAddress",
          "type": "address"
        },
        {
          "internalType": "uint256",
          "name": "amount",
          "type": "uint256"
        }
      ],
      "name": "Undelegate",
      "outputs": [],
      "stateMutability": "nonpayable",
      "type": "function"
    }
]
```

4\. Select "Delegate" from the drop-down.&#x20;

5\. Enter the delegator address (your multisig safe address) and validator address. Note that these have to be in the `0x` format and not `one1`. You can easily get the `0x` formatted address of your `one1` from [https://explorer.harmony.one](https://explorer.harmony.one) "Address Format" toggle on the top.

6\. Enter the amount of ONE to stake. Note that, you have to append 18 zeros to your number as the amount is expected in the `wei` units and not `ONE`. For example, if you want to stake 100 ONE, you will write 100000000000000000000 (notice the 18 zeros after 100).

![](<../../.gitbook/assets/Screen Shot 2022-06-01 at 8.47.17 AM (1).png>)

7\. Click on "Review", "Submit", and sign the transaction. Rest of the steps are usual multisig signing where all required parties sign this transaction.

### Collect Rewards

1\. Navigate to "New Transaction" and select "Contract Interaction"

2\. Enter `0x00000000000000000000000000000000000000FC` into the "Contract Address" field of the Contract Interaction form.

3\. Copy paste the text below into the ABI field in the Contract Interaction form

```
[
    {
        "inputs": [
          {
            "internalType": "address",
            "name": "delegatorAddress",
            "type": "address"
          }
        ],
        "name": "CollectRewards",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
      }
]
```

4\. Select "CollectRewards" from the drop-down.&#x20;

5\. Enter the delegator address (your multisig safe address)

![](<../../.gitbook/assets/Screen Shot 2022-06-01 at 8.50.49 AM.png>)

6\. Click on "Review", "Submit", and sign the transaction. Rest of the steps are usual multisig signing where all required parties sign this transaction.
