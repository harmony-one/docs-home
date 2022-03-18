# Sending & Receiving

{% hint style="info" %}
You can receive transactions to addresses starting with both **one1** and **0x**. However, Metamask does not allow you to send transactions to addresses starting with **one1.** You will need its' equivalent **0x** address as the destination address. For that, follow the procedures below.
{% endhint %}

### Retrieving the 0x Equivalent Address

* For mainnet, go to [https://explorer.harmony.one/#/](https://explorer.harmony.one/#/) (Mainnet). For testnet, go to [https://explorer.pops.one/#/](https://explorer.pops.one/#/).
* Search for your one1 address at the top.
* At top of the screen, toggle the address format from ONE to ETH.

![Address Format](../../../../.gitbook/assets/metamask\_sending\_transactions1.png)

* Copy the **0x** address format by clicking on the small icon right to the address

![](<../../../../.gitbook/assets/image (288).png>)

**You now have the 0x address which corresponds to your one1 address.**

### Sending a Regular Transaction

To send a transaction on MetaMask, click on **Send** button and on next window paste the destination address starting with **0x**, fill the amount you want to send, click on **Next,** and then click on **Confirm**.

{% hint style="info" %}
If your transaction fails due to insufficient gas, set the Gas Limit to 25000, and for **all transactions** you need set Gas Price more than **30 GWEI**.
{% endhint %}

![](<../../../../.gitbook/assets/image (289) (1) (1).png>)

### Receiving a Regular Transaction

In order to receive a transaction, simply share the **0x** address format with the sender.
