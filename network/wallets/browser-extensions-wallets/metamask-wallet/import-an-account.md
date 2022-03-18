# Import an Account

{% hint style="warning" %}
There is a [known issue on MetaMask](https://metamask.zendesk.com/hc/en-us/articles/360058120992-My-Seed-Phrase-Secret-Recovery-Phrase-restored-the-wrong-account) where after the restoration of a wallet, MetaMask shows a different account with missing funds. Please make sure you use the same RPC network details as the one used in the original wallet. For example, if your original wallet was on the Harmony RPC network but your new wallet is on POKT RPC network, you may not see your original account.
{% endhint %}

### 1. Obtaining a Private Key

Importing an account is done by taking an existing private key and importing it into MetaMask. How you obtain the private key is dependent on the wallet in use.&#x20;

For the **Harmony Chrome extension wallet**, click the Menu button at the top right, click Export Private Key, enter your password, and copy the private key displayed.

### 2. Using a Private Key

Click on the icon on top as shown by the image below and then on **Import Account**:

![Importing Account](../../../../.gitbook/assets/metamask\_import\_account1.png)

On next window, select the option to import from a Private Key, paste your key and click on **Import** to complete the step.

![](../../../../.gitbook/assets/metamask\_import\_account2.png)

Your account should now be imported.
