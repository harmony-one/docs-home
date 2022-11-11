# Register the Vault

#### Registering your vault in btc bridge

There are two ways:

1\) Running a `curl` command on vault server

```
curl http://localhost:3000/api/vault-client/register -H 'Content-Type: application/json' -X POST --data '{"collateral":"11"}'
```

{% hint style="info" %}
Note that, you will need at least 11 ONE (10 ONE for registering your vault and 1 ONE for some gas). Higher value is okay. You can also register with smaller values and later increase your collateral from the admin page.
{% endhint %}

2\) Navigate to vault admin page (upon running the vault client in the above step): http://localhost:3000/.&#x20;

{% hint style="info" %}
If you are using a remote server and accessing vault admin page from outside, navigate to the appropriate URL with your remote server address, for example: http://your-server-address:3000/. Note that, if you using AWS or other server instances, you may need to allow inbound access to your machine that is trying to load the BTC bridge admin page.
{% endhint %}

Upon navigating, you should see the page that prompts to register the vaults and your wallet addresses.

![](<../../../../../.gitbook/assets/Untitled-3 (1).png>)

Click `Register your vault` to successfully complete this step.&#x20;

{% hint style="info" %}
Note that, you should have at least 11 ONE tokens in your Harmony wallet that is being registered to successfully completing the registration step.
{% endhint %}

Upon successfully registering you will be navigated to vault details page as shown below with all the relevant information regarding the registered vaults.

![](../../../../../.gitbook/assets/Untitled-4.png)

It is recommended to wait until the vault synchronization (as shown below) reaches 100%. This usually takes about 10-20 minutes after registering your vault. This is is final step and now your vault is ready to facilitate BTC transfers.

![](../../../../../.gitbook/assets/Untitled-5.png)

