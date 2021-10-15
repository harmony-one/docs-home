---
description: This page provides a set of APIs to interact with backend.
---

# API

This API enable users to do all bridge operations.

For flow freely between Harmony and Ethereum blockchains you need to call these methods in special order and with appropriate parameters.

## Operations Example

### **ETH -> ONE (BUSD)**

1\) call **Create operation API** with params (_see more params in API section_): 

* `type`= `eth_to_one` 
* `id` = operation uniq ID (you need to generate ID on client side)
* `token` = `busd`
* `amount` = transfered amount
* `ethAddress` = your ethereum address
* `oneAddress` = harmony receiver address

2\) call `approveEthManager` smart contract method (_see smart contract methods section in the end_) for BUSD ethereum contract. You need to save generated transaction hash.

3\) call `lockToken` smart contract method (_see smart contract methods section in the end_) for BUSD manager ethereum contract. You need to save generated transaction hash.

4\) call **Confirm action API **with params (_see more params in API section_): 

* operationId - operation ID (generated on step 1)
* transactionHash - `approveEthManager` transaction Hash (generated on step 2)
* actionType = `approveEthManager`

5\) call **Confirm action API **with params (_see more params in API section_): 

* operationId - operation ID (generated on step 1)
* transactionHash - `lockToken` transaction Hash (generated on step 2)
* actionType = `lockToken`

6\) call **Get Operation Info API **with operation ID (generated on step 1) to get actual operation status (see status property).

Also you can monitoring each action status: see `operation -> actions`

7\) Next steps**`Wait for finality`** and** `Mint tokens`** (on harmony side) - will be done automatically. You need only monitoring operation status (step 6).

{% hint style="info" %}
For **Create operation API** and **Confirm action API** you need to call API for each validator from list.
{% endhint %}

```
[
  "https://be1.bridge.hmny.io",
  "https://be2.bridge.hmny.io",
  "https://be3.bridge.hmny.io"
]
```

### ONE** -> ETH (BUSD)**

1\) call **Create operation API** with params (_see more params in API section_): 

* `type`= `one_to_eth` 
* `id` = operation uniq ID (you need to generate ID on client side)
* `token` = `link`
* `amount` = transfered amount
* `oneAddress` = your one address
* `ethAddress` = ethereum receiver address

2\) call `approveHmyManager` smart contract method (_see smart contract methods section in the end_) for BUSD harmony contract. You need to save generated transaction hash.

3\) call `burnToken` smart contract method (_see smart contract methods section in the end_) for BUSD manager harmony contract. You need to save generated transaction hash.

4\) call **Confirm action API **with params (_see more params in API section_): 

* operationId - operation ID (generated on step 1)
* transactionHash - `approveHmyManager` transaction Hash (generated on step 2)
* actionType = `approveHmyManager`

5\) call **Confirm action API **with params (_see more params in API section_): 

* operationId - operation ID (generated on step 1)
* transactionHash - `burnToken` transaction Hash (generated on step 2)
* actionType = `burnToken`

6\) call **Get Operation Info API **with operation ID (generated on step 1) to get actual operation status (see status property).

Also you can monitoring each action status: see `operation -> actions`

7\) Next step** `Unlock tokens`** (on ethereum side) - will be done automatically. You need only monitoring operation status (step 6).

{% hint style="info" %}
For **Create operation API** and **Confirm action API** you need to call API for each validator from list.
{% endhint %}

## API description

{% swagger baseUrl="https://be1.bridge.hmny.io" path="/operations" method="post" summary="Create operation" %}
{% swagger-description %}
this method will create new operation - it must be call for each validator (be1, be2, be3)
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
id must be generated on client side.

\


id format example: 

`b063040e-31c41b19-a7d21a09-9bb0339f`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="amount" type="string" %}
displayed amount (use only for explorer display)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="token" type="string" %}
`link`

 \| 

`busd`

 \| 

`erc20`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
`eth_to_one`

 \| 

`one_to_eth`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="ethAddress" type="string" %}
this field using depends on operation 

`type`

:

\




`eth_to_one`

: ethereum sender (

_who will sign tx_

)

\




`one_to_eth`

: ethereum receiver (

_who will get tokens_

)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="oneAddress" type="string" %}
this field using depends on operation 

`type`

:

\




`eth_to_one`

: harmony receiver (who will get tokens)

\




`one_to_eth`

: harmony sender (who will sign tx)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="erc20Address" type="string" %}
ERC20 address 

\


needed only for operations with type 

`erc20`
{% endswagger-parameter %}

{% swagger-response status="200" description="Cake successfully retrieved." %}
```
{
   "id":"7076042e-f23b3018-cfe6195f-b94b75f5",
   "type":"eth_to_one",
   "erc20Address":"0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
   "token":"link",
   "status":"in_progress",
   "amount":"0.1",
   "ethAddress":"0x85c016897702a33a1ef58a0755d149ee943e2cd5",
   "oneAddress":"one1shqpdzthq23n58h43gr4t52fa62rutx4s247sk",
   "timestamp":1603303897,
   "actions":[
      {
         "id":"f70af6bb-2f24915a-7ab56d36-b03bbc5f",
         "type":"approveEthManger",
         "status":"waiting",
         "payload":null
      },
      {
         "id":"88d9cc67-b004e8cc-71020a1b-5e2ba517",
         "type":"lockToken",
         "status":"waiting",
         "payload":null
      },
      {
         "id":"0c2b22b9-94891de9-85088db4-1b9dc3e0",
         "type":"waitingBlockNumber",
         "status":"waiting",
         "payload":null
      },
      {
         "id":"393dabb6-b43a583e-7852a254-61be358a",
         "type":"mintToken",
         "status":"waiting",
         "payload":null
      }
   ]
}
```
{% endswagger-response %}

{% swagger-response status="404" description="Could not find a cake matching this query." %}
```
{    "error": "error message here"
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://be1.bridge.hmny.io" path="/operations/:operationId/actions/:actionType/confirm" method="post" summary="Confirm action" %}
{% swagger-description %}
Is used for confirm actions instead of process 

`eth_to_one`

 ore 

`one_to_eth`
{% endswagger-description %}

{% swagger-parameter in="path" name="operationId" type="string" %}
operation Id (was created on frontend side on 1 step)
{% endswagger-parameter %}

{% swagger-parameter in="path" name="actionType" type="string" %}
`approveEthManager`

 \| 

`lockToken`

 |

`approveHmyManager`

 \| 

`burnToken`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="transactionHash" type="string" %}
hash of transaction which must be success, for move to next step. you can send transaction in pending status - validator will observe it automatically.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
   "id":"7076042e-f23b3018-cfe6195f-b94b75f5",
   "type":"eth_to_one",
   "erc20Address":"0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
   "token":"link",
   "status":"in_progress",
   "amount":"0.1",
   "ethAddress":"0x85c016897702a33a1ef58a0755d149ee943e2cd5",
   "oneAddress":"one1shqpdzthq23n58h43gr4t52fa62rutx4s247sk",
   "timestamp":1603303897,
   "actions":[
      {
         "id":"f70af6bb-2f24915a-7ab56d36-b03bbc5f",
         "type":"approveEthManger",
         "status":"waiting",
         "payload":null
      },
      {
         "id":"88d9cc67-b004e8cc-71020a1b-5e2ba517",
         "type":"lockToken",
         "status":"waiting",
         "payload":null
      },
      {
         "id":"0c2b22b9-94891de9-85088db4-1b9dc3e0",
         "type":"waitingBlockNumber",
         "status":"waiting",
         "payload":null
      },
      {
         "id":"393dabb6-b43a583e-7852a254-61be358a",
         "type":"mintToken",
         "status":"waiting",
         "payload":null
      }
   ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://be1.bridge.hmny.io" path="/operations/:id" method="get" summary="Get operation info" %}
{% swagger-description %}
Is used for get operation status and actions status (look at actions array in response)
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" %}
operation id
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
   "id":"7076042e-f23b3018-cfe6195f-b94b75f5",
   "type":"eth_to_one",
   "erc20Address":"0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
   "token":"link",
   "status":"in_progress",
   "amount":"0.1",
   "ethAddress":"0x85c016897702a33a1ef58a0755d149ee943e2cd5",
   "oneAddress":"one1shqpdzthq23n58h43gr4t52fa62rutx4s247sk",
   "timestamp":1603303897,
   "actions":[
      {
         "id":"f70af6bb-2f24915a-7ab56d36-b03bbc5f",
         "type":"approveEthManger",
         "status":"waiting",
         "payload":null
      },
      {
         "id":"88d9cc67-b004e8cc-71020a1b-5e2ba517",
         "type":"lockToken",
         "status":"waiting",
         "payload":null
      },
      {
         "id":"0c2b22b9-94891de9-85088db4-1b9dc3e0",
         "type":"waitingBlockNumber",
         "status":"waiting",
         "payload":null
      },
      {
         "id":"393dabb6-b43a583e-7852a254-61be358a",
         "type":"mintToken",
         "status":"waiting",
         "payload":null
      }
   ]
}

```
{% endswagger-response %}
{% endswagger %}

## LINKS

Smart contracts ABI and method call examples - here ([https://github.com/harmony-one/ethhmy-bridge/tree/master/scripts](https://github.com/harmony-one/ethhmy-bridge/tree/master/scripts))

You can see more examples of API using without UI here: [https://github.com/harmony-one/ethhmy-bridge.tests](https://github.com/harmony-one/ethhmy-bridge.tests)
