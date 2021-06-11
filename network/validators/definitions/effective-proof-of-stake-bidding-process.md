# Effective Proof-of-Stake

{% embed url="https://www.youtube.com/watch?v=Q\_LacFZOly8&list=PLAzkb1vJXQOR3ZEl25MKiz5-CMw6xVkaW&index=5" %}

{% embed url="https://www.youtube.com/watch?v=2riHPsh2yYM&list=PLAzkb1vJXQOR3ZEl25MKiz5-CMw6xVkaW&index=4" %}



Effective stake is a new measure introduced in EPoS in order to prevent stake centralization and still provide capitalistic fairness. For exactly how it achieves that, [here](https://medium.com/harmony-one/introducing-harmonys-effective-proof-of-stake-epos-2d39b4b8d58) is the design rationale behind it.

Let’s call the bid price of the elected BLS keys the _raw stake_. The effective stake of an elected BLS key is a bounded value on its raw stake with a threshold around the median bidder’s raw stake \(denoted as median\_stake in the picture below\). The upper threshold is 115% of the median\_stake and the lower threshold is 85% of the median\_stake. For a key with raw stake that’s out of bound of the threshold, its effective stake will be bounded by the corresponding threshold, otherwise, the effective stake is the same as the raw stake.

The effective stake of each BLS key is determined at the last block of an epoch during the election process and will stay the same throughout the next epoch.

![](../../../.gitbook/assets/image%20%2852%29.png)

![](../../../.gitbook/assets/screen-shot-2020-03-26-at-4.17.57-pm.png)

![](../../../.gitbook/assets/screen-shot-2020-03-26-at-4.18.02-pm.png)



![](../../../.gitbook/assets/screen-shot-2020-03-26-at-4.18.07-pm.png)

![](../../../.gitbook/assets/screen-shot-2020-03-26-at-4.18.10-pm.png)

