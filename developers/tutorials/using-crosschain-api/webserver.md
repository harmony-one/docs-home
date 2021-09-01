# Webserver

This is a webserver using `node` and `express`, in order to start it you need to run the following commands in the terminal:

* `npm install`
* `node index.js`

We assume that it will run in port 3000 but feel free to change it. Don't forget to update the scritps accordingly though.

## Endpoints

The general architecture of the API is the following

* Endpoints that receive signed transactions as inputs and they will complete the required transactions. This allow you to sign the transactions of the front end and it is safe to use on a production server because the private key is never sent to the endpoints. To sign the transactions you can see the examples in the scripts folder of this repo.
* You can make and end-to-end swap using the `/swap` endpoints. But this is a multi-step process that will fail if one of the single steps fails. It uses Harmony's Horizon Bridge and Viper DEX, so for example, the bridging part can work but if there is no liquidity in the pool so the who transaction will fail. Therefore use this enpoint only if you are sure that Viper's LPs have enough liquidity.
* If you prefer to do it setp-by-step, you should use the following end-points in the specified order:
  * `/swap/bridge-in` - Bridges `BUSD` in ethereum to Harmony's `BUSD`
  * `/swap/viper/` - Swaps Harmony's `BUSD` to `bscBUSD` \(Both are bridged assets in the Harmony network\)
  * `/swap/bridge-out` - Bridges `bscBUSD` into Binance's `BUSD`

Right now the following endpoints are enabled, but we will keep adding more reguarly, so remember to pull once in a while.

### **`POST /swap`**

This endpoint will swap balances between Ethereum BUSD and Binance BUSD, the body for this request should look like this:

{% tabs %}
{% tab title="Request" %}
```text
{
    "amount" : amount,
    "oneAddress" : oneAddress,
    "ethAddress" : ethAddress
    "lockApproveTxnHash" : approveTxnHash
    "lockTxnHash" : lockTxnHash
    "burnApproveTxnHash" : approveTxnHash
    "depositTxnHash" : depositTxnHash
    "burnTxnHash" : burnTxnHash
    "routerContract" : routerContract
    "fromTokenContract" : fromTokenContract
}
```
{% endtab %}

{% tab title="Response" %}
```text
{ 
    trx: "swap", 
    success: bool, 
    error_message: message, 
    error_body: body
}
```
{% endtab %}
{% endtabs %}

* `amount`: this is a string with the amount in decimals \(e.g. "10.50"\) that you want to swap
* `oneAddress`: this is a string with the address of the wallet owned by the private key in the Harmony wallet format i.e. `oneaxxxxxxxx`
* `ethAddress`: this is a string with the address of the wallet owned by the private key in the Ethereum wallet format i.e. `Oxaxxxxxxxx`
* `lockApproveTxnHash` : this is a string with the hash of the contract manager's approval for the lock transaction
* `lockTxnHash` : this is a string with the hash of the lock transaction
* `burnApproveTxnHash` : this is a string with the hash of the contract manager's approval for the burn transaction
* `depositTxnHash` : this is a string with the hash of the deposit transaction
* `burnTxnHash` : this is a string with the hash of the burn transaction
* `routerContract` : This is a string with the writing approval for Viper's swap router contract
* `fromTokenContract` : This is a string with the transaction approval for the account swapping in Viper

### **`POST /swap/bridge-in`**

This enpoint will bridges `BUSD` in ethereum to Harmony's `BUSD`, it is the first step of the step-by-step swap, the body for this request should look like this:

{% tabs %}
{% tab title="Request" %}
```text
{
    "amount" : amount,
    "oneAddress" : oneAddress,
    "ethAddress" : ethAddress,
    "lockApproveTxnHash" : approveTxnHash,
    "lockTxnHash" : lockTxnHash
}
```
{% endtab %}

{% tab title="Response" %}
```text
{ 
    trx: "bridge", 
    success: bool, 
    error_message: message, 
    error_body: body
}
```
{% endtab %}
{% endtabs %}

* `amount`: this is a string with amount in decimals \(e.g. "10.50"\) that you want to swap
* `oneAddress`: the address of the wallet owned by the private key in the Harmony wallet format i.e. `oneaxxxxxxxx`
* `ethAddress`: the address of the wallet owned by the private key in the Ethereum wallet format i.e. `Oxaxxxxxxxx`
* `lockApproveTxnHash` : this is a string with the hash of the contract manager's approval for the lock transaction
* `lockTxnHash` : this is a string with the hash of the lock transaction

_You can see an example of this call in the `bridge_eth_to_one.js` file in the_ [_scripts folder_](https://github.com/harmony-one/crosschain-api/tree/main/scripts) _of the repo_

### **`POST /swap/viper`**

This enpoint will swap Harmony's `BUSD` to `bscBUSD` \(Both are bridged assets in the Harmony network\), it is the second step of the step-by-step swap, the body for this request should look like this:

{% tabs %}
{% tab title="Request" %}
```text
{
    "amount" : amount,
    "oneAddress" : oneAddress,
    "ethAddress" : ethAddress
    "routerContract" : routerContract
    "fromTokenContract" : fromTokenContract
}
```
{% endtab %}

{% tab title="Response" %}
```text
{ 
    trx: "viper", 
    success: bool, 
    error_message: message, 
    error_body: body
}
```
{% endtab %}
{% endtabs %}

* `amount`: this is a string with amount in decimals \(e.g. "10.50"\) that you want to swap
* `wallet`: this is the private key of the wallets with the funds, please use an `.env` or equivalent to store this key, never put it in your code
* `oneAddress`: the address of the wallet owned by the private key in the Harmony wallet format i.e. `oneaxxxxxxxx`
* `routerContract` : This is a string with the writing approval for Viper's swap router contract
* `fromTokenContract` : This is a string with the transaction approval for the account swapping in Viper

_You can see an example of this call in the `viper_swap.js` file in the_ [_scripts folder_](https://github.com/harmony-one/crosschain-api/tree/main/scripts) _of the repo_

### **`POST /swap/bridge-out`**

{% tabs %}
{% tab title="Request" %}
```text
{
    "amount" : amount,
    "oneAddress" : oneAddress,
    "ethAddress" : ethAddress,
    "burnApproveTxnHash" : approveTxnHash,
    "depositTxnHash" : depositTxnHash,
    "burnTxnHash" : burnTxnHash
}
```
{% endtab %}

{% tab title="Response" %}
```text
{ 
    trx: "bridge", 
    success: bool, 
    error_message: message, 
    error_body: body
}
```
{% endtab %}
{% endtabs %}

* `amount`: this is a string with amount in decimals \(e.g. "10.50"\) that you want to swap
* `oneAddress`: the address of the wallet owned by the private key in the Harmony wallet format i.e. `oneaxxxxxxxx`
* `ethAddress`: the address of the wallet owned by the private key in the Ethereum wallet format i.e. `Oxaxxxxxxxx`
* `burnApproveTxnHash` : this is a string with the hash of the contract manager's approval for the burn transaction
* `depositTxnHash` : this is a string with the hash of the deposit transaction
* `burnTxnHash` : this is a string with the hash of the burn transaction

_You can see an example of this call in the `bridge_one_to_bsc.js` file in the_ [_scripts folder_](https://github.com/harmony-one/crosschain-api/tree/main/scripts) _of the repo_

## Local Endpoints

### **`POST /local/swap`**

This enpoint will swap balances between Ethereum BUSD and Binance BUSD, the body for this request should look like this:

{% tabs %}
{% tab title="Request" %}
```text
{
    "amount" : amount,
    "wallet" : wallet,
    "oneAddress" : oneAddress,
    "ethAddress" : ethAddress
}
```
{% endtab %}

{% tab title="Response" %}
```
{ 
    trx: "swap", 
    success: bool, 
    error_message: message, 
    error_body: body
}
```
{% endtab %}
{% endtabs %}

* `amount`: this is a string with amount in decimals \(e.g. "10.50"\) that you want to swap
* `wallet`: this is the private key of the wallets with the funds, please use an `.env` or equivalent to store this key, never put it in your code
* `oneAddress`: the address of the wallet owned by the private key in the Harmony wallet format i.e. `oneaxxxxxxxx`
* `ethAddress`: the address of the wallet owned by the private key in the Ethereum wallet format i.e. `Oxaxxxxxxxx`

_You can see an example of this call in the `swap.js` file in the_ [_testing folder_](https://github.com/harmony-one/crosschain-api/tree/dev/testing) _of the repo_

### **`POST /local/swap/bridge-in`**

This enpoint will bridges `BUSD` in ethereum to Harmony's `BUSD`, it is the first step of the step-by-step swap, the body for this request should look like this:

{% tabs %}
{% tab title="Request" %}
```text
{
    "amount" : amount,
    "wallet" : wallet,
    "oneAddress" : oneAddress,
    "ethAddress" : ethAddress
}
```
{% endtab %}

{% tab title="Response" %}
```
{ 
    trx: "bridge", 
    success: bool, 
    error_message: message, 
    error_body: body
}
```
{% endtab %}
{% endtabs %}

* `amount`: this is a string with amount in decimals \(e.g. "10.50"\) that you want to swap
* `wallet`: this is the private key of the wallets with the funds, please use an `.env` or equivalent to store this key, never put it in your code
* `oneAddress`: the address of the wallet owned by the private key in the Harmony wallet format i.e. `oneaxxxxxxxx`
* `ethAddress`: the address of the wallet owned by the private key in the Ethereum wallet format i.e. `Oxaxxxxxxxx`

_You can see an example of this call in the `bridge-lock.js` file in the_ [_testing folder_](https://github.com/harmony-one/crosschain-api/tree/dev/testing) _of the repo_

### **`POST /local/swap/viper`**

This enpoint will swap Harmony's `BUSD` to `bscBUSD` \(Both are bridged assets in the Harmony network\), it is the second step of the step-by-step swap, the body for this request should look like this:

{% tabs %}
{% tab title="Request" %}
```text
{
    "amount" : amount,
    "wallet" : wallet,
    "oneAddress" : oneAddress,
}
```
{% endtab %}

{% tab title="Response" %}
```
{ 
    trx: "viper", 
    success: bool, 
    error_message: message, 
    error_body: body
}
```
{% endtab %}
{% endtabs %}

* `amount`: this is a string with amount in decimals \(e.g. "10.50"\) that you want to swap
* `wallet`: this is the private key of the wallets with the funds, please use an `.env` or equivalent to store this key, never put it in your code
* `oneAddress`: the address of the wallet owned by the private key in the Harmony wallet format i.e. `oneaxxxxxxxx`

_You can see an example of this call in the `viper.js` file in the_ [_testing folder_](https://github.com/harmony-one/crosschain-api/tree/dev/testing) _of this repo_

### **`POST /local/swap/bridge-out`**

This enpoint will bridges `bscBUSD` into Binance's `BUSD`, it is the third step of the step-by-step swap, the body for this request should look like this:

{% tabs %}
{% tab title="Request" %}
```text
{
    "amount" : amount,
    "wallet" : wallet,
    "oneAddress" : oneAddress,
    "ethAddress" : ethAddress
}
```
{% endtab %}

{% tab title="Response" %}
```
{ 
    trx: "bridge", 
    success: bool, 
    error_message: message, 
    error_body: body
}
```
{% endtab %}
{% endtabs %}

* `amount`: this is a string with amount in decimals \(e.g. "10.50"\) that you want to swap
* `wallet`: this is the private key of the wallets with the funds, please use an `.env` or equivalent to store this key, never put it in your code
* `oneAddress`: the address of the wallet owned by the private key in the Harmony wallet format i.e. `oneaxxxxxxxx`
* `ethAddress`: the address of the wallet owned by the private key in the Ethereum wallet format i.e. `Oxaxxxxxxxx`

_You can see an example of this call in the `bridge-burn.js` file in the_ [_testing folder_](https://github.com/harmony-one/crosschain-api/tree/dev/testing) _of this repo_

