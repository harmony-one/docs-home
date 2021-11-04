---
description: Definition of validator information terms
---

# Validator Information Terms

This page introduces main terms about validator infos in the [harmony-mainnet-tracker spreadsheet](https://docs.google.com/spreadsheets/d/1AyYHWSkKOCzMY0ZvoT049DapIDvkEhpnfbA1WidJm3o/edit?usp=sharing), you can also read some of the terms in [staking dashboard](https://staking.harmony.one/validators).

## APR

Annual Percentage Return (APR) is the percent return of rewards for the last epoch that _**the validator was last elected**_.&#x20;

{% hint style="warning" %}
This field reflects the data of the last epoch this validator elected, not the current epoch.&#x20;

For example, if a validator was elected in epoch 186 with 50% APR and they were never elected again, they will still display 50% APR.
{% endhint %}

### Latest Expected Return

![Example Validator Profile](<../../.gitbook/assets/Screen Shot 2020-07-25 at 9.37.37 PM.png>)

Latest expected return is the validator's APR for the latest epoch.

![Example Validator List](<../../.gitbook/assets/Screen Shot 2020-07-25 at 9.34.32 PM.png>)

The Expected Return field here is average of the validator's APR for the past 30 epochs that they were elected.

## Uptime

Validator uptime is calculated as:

$$
s / b * 100
$$

Where s is the number of blocks signed by the validator and b is the number of blocks in the epoch so far.

If a validator has never been elected, their uptime will display as _**None **_in the tracking spreadsheet_**. **_In the staking dashboard, their uptime will be 0.00%.

![Example of a validate that has never been elected](<../../.gitbook/assets/Screen Shot 2020-07-25 at 11.18.51 PM.png>)

{% hint style="warning" %}
Similarly to APR, uptime is also only updated if the validator is currently elected.&#x20;

For example, if the same validator was elected in epoch 186 with 100% uptime and they were never elected again, they will still have 100% uptime displayed.
{% endhint %}

&#x20;

## Epos-status

There are five types of data in this field:&#x20;

* eligible to be elected next epoch
* not eligible to be elected next epoch
* currently elected
* doubleSigningBanned
* unknown

Epos status is based on the validator's active status. The validator's active status will be controlled either by user or system (if detected low uptime or 0 self-stake). However if the validator is never elected, as long as he set the validator status as active, he will always be shown as "eligible to be elected next epoch".

## Boot-status

There are five types of the data in this field:&#x20;

* NotBooted: if the validator was never selected/signed blocks.&#x20;
* LostEPoSAuction
* TurnedInactiveOrInsufficientUptime
* BannedForDoubleSigning
* None: when the validator is currently elected
