# Validator Info Doc

This page introduces main terms about validator infos in the [harmony-mainnet-tracker spreadsheet](https://docs.google.com/spreadsheets/d/1AyYHWSkKOCzMY0ZvoT049DapIDvkEhpnfbA1WidJm3o/edit?usp=sharing), you can also read some of the terms in [staking dashboard](https://staking.harmony.one/validators).

## APR

APR represents the annual percentage rate of the last epoch _**the validator is elected**_. You can also get the data from the performance section on the validator page in staking dashboard website. 

![apr / latest expected return example](../.gitbook/assets/image%20%28191%29.png)

{% hint style="info" %}
This field is different from the _**expected return**_ on the dashboard main page. The _**expected return**_ on dashboard list is the average aprs in last `min(30, epochs you were elected)`epochs.
{% endhint %}

{% hint style="info" %}
This filed reflects the data of the last epoch this validator elected, but not the latest epoch. For example, one validator was only elected in epoch 186, and his apr is 50% in that epoch, if later he was never elected, his apr will not reduce, still show 50%.
{% endhint %}

## Uptime

Uptime = signed blocks / to-sign blocks. There are two types of data, _**"None"**_ or a number.

Based on the definition, if the validator is never elected, his uptime will show as _**None.**_ In the staking dashboard, he will have empty result in the main page, and in the validator page, the uptime will be 0.00%.

![uptime example](../.gitbook/assets/image%20%28190%29.png)

{% hint style="info" %}
Only those validators who are elected will have to-sign blocks. So similar to apr, if the validator is only elected in epoch 186 and his uptime is 100% in epoch 186. If later he is not elected, his uptime will still show as 100%.
{% endhint %}

## Epos-status

There are five types of data in this field: 

* eligible to be elected next epoch
* not eligible to be elected next epoch
* currently elected
* doubleSigningBanned
* unknown

Epos status is based on the validator's active status. The validator's active status will be controlled either by user or system \(if detected low uptime or 0 self-stake\). However if the validator is never elected, as long as he set the validator status as active, he will always be shown as "eligible to be elected next epoch".

## Boot-status

There are five types of the data in this field: 

* NotBooted: if the validator was never selected/signed blocks. 
* LostEPoSAuction
* TurnedInactiveOrInsufficientUptime
* BannedForDoubleSigning
* None: when the validator is currently elected

