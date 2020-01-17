# Trustwallet

![](../.gitbook/assets/screen-shot-2020-01-15-at-8.42.26-am.png)

## IMPORTANT DISCLAIMER

Please note that Trustwallet does not support sharded network architecture yet, and all transactions originated from Trustwallet goes through Shard-0. This means that you can only view and access your funds in Shard-0. 

### Incoming transactions

The funds that are sent within Shard-0 will be viewed correctly in Trustwallet. \[From: Shard-0, To: Shard-0\]

If you receive funds in a shard other than Shard-0 \[e.g., From: Shard-2, you will not see the transaction receipt in Trustwallet app. Since your account balance will only show the funds in Shard-0, your total balance will not change. 

### Outgoing transactions

Since there is no shard selection in Trustwallet UI, all transactions will be sent from Shard-0 to Shard-0. 



### **Please see all possible scenarios for Trustwallet**

1. **Sender uses CLI or Mathwallet** \(aka. has access to all shards\)
2. **Recipient uses Trustwallet**

![](../.gitbook/assets/image%20%2812%29.png)

\*\*\*\*

\*\*\*\*

1. **Sender uses Trustwallet**
2. **Recipient uses CLI or Mathwallet** \(aka. has access to all shards\)

![](../.gitbook/assets/image%20%2839%29.png)





1. **Sender uses Trustwallet**
2. **Recipient uses Trustwallet**

![](../.gitbook/assets/image%20%2830%29.png)

