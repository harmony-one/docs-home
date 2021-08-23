---
description: >-
  This page describes endpoints of harmony explorer to programmatically access
  the data.
---

# Using Explorer EndPoints

{% api-method method="get" host="https://explorer-v2-api.hmny.io/v0/erc20/" path="/v0/erc20/" %}
{% api-method-summary %}
List all HRC20 tokens
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io" path="/v0/erc721/" %}
{% api-method-summary %}
List all HRC721 tokens
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io" path="/v0/erc1155" %}
{% api-method-summary %}
List all HRC1155 tokens
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io" path="/v0/erc20/address/:token\_addr/balances" %}
{% api-method-summary %}
HRC20 Balance of an address
{% endapi-method-summary %}

{% api-method-description %}
Get the HRC20 balance of an address.   
`https://explorer-v2-api.hmny.io/v0/erc20/address/0x8454bf4fc72687b61eaf1bcd64bb9e78983fbdd7/balances`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="token\_addr" type="string" required=false %}
HRC20 token address
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io" path="v0/erc721/address/:token\_addr/balances" %}
{% api-method-summary %}
HRC721/1155 Balance of an address
{% endapi-method-summary %}

{% api-method-description %}
Get the HRC721/HRC1155 balance of an address  
`https://explorer-v2-api.hmny.io/v0/erc721/address/0x847826f2d552c87d2ee6f38b65425fc85befe841/balances`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}
HRC20 token address
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io" path="/v0/price/actual/ONEUSDT" %}
{% api-method-summary %}
ONE-USDT Price
{% endapi-method-summary %}

{% api-method-description %}
Get the price of ONE in USDT  
Example:  
`https://explorer-v2-api.hmny.io/v0/price/actual/ONEUSDT`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io" path="/v0/shard/:shard\_id/address/:address/transactions/type/transaction?offset=0&limit=10" %}
{% api-method-summary %}
All Transactions
{% endapi-method-summary %}

{% api-method-description %}
`https://explorer-v2-api.hmny.io/v0/shard/0/address/0x7912111622cb6455156ceb8a4b17c8c2ce6e7dab/transactions/type/transaction?offset=0&limit=10`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="shard\_id" type="string" required=false %}
shard id
{% endapi-method-parameter %}

{% api-method-parameter name="address" type="string" required=false %}
hex address
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io" path="/v0/shard/:shard\_id/address/0xdd46509b31b87f05a0da47e6ff9cdaa5563e7a57/transactions/type/erc20?offset=0&limit=10" %}
{% api-method-summary %}
HRC20 Transactions
{% endapi-method-summary %}

{% api-method-description %}
Get all HRC20 transactions.  
Example:  
`https://explorer-v2-api.hmny.io/v0/shard/0/address/0xdd46509b31b87f05a0da47e6ff9cdaa5563e7a57/transactions/type/erc20?offset=0&limit=10`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io/" path="/v0/shard/:shard\_id/address/:token\_addr/transactions/type/erc721?offset=0&limit=10" %}
{% api-method-summary %}
NFT \(HRC721/HRC1155\) Transactions
{% endapi-method-summary %}

{% api-method-description %}
Get the transactions of an HRC721/HRC1155 token.  
Example:  
`https://explorer-v2-api.hmny.io/v0/shard/0/address/0xe59a79c7516d22a488a3f479626e75a2e81aae66/transactions/type/erc721?offset=0&limit=10`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="shard\_id" type="string" required=false %}
shard id
{% endapi-method-parameter %}

{% api-method-parameter name="token\_addr" type="string" required=false %}
HRC721/HRC1155 token contract address
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io/" path="/v0/shard/:shard\_id/logs/transaction/hash/:txn\_hash" %}
{% api-method-summary %}
Logs
{% endapi-method-summary %}

{% api-method-description %}
Get the event logs of a transaction.  
Example:  
`https://explorer-v2-api.hmny.io/v0/shard/0/logs/transaction/hash/0x0d449c8dde6c13e63064f49c531ba028878a4de368473cdff421255000c8047f`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="shard\_id" type="string" required=false %}
shard id
{% endapi-method-parameter %}

{% api-method-parameter name="txn\_hash" type="string" required=false %}
transaction hash
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://explorer-v2-api.hmny.io" path="/v0/erc20/token/:token\_addr/holders?limit=100&offset=0" %}
{% api-method-summary %}
Token Holders
{% endapi-method-summary %}

{% api-method-description %}
Get the list of token holders of an HRC20 token.   
Example:  
`https://explorer-v2-api.hmny.io/v0/erc20/token/0xcf664087a5bb0237a0bad6742852ec6c8d69a27a/holders?limit=100&offset=0`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Token Address" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
[
{"ownerAddress":"0xeb049f1ed546f8efc3ad57f6c7d22f081ccc7375","tokenAddress":"0xcf664087a5bb0237a0bad6742852ec6c8d69a27a","balance":"84198183077703161163395138","needUpdate":false,"lastUpdateBlockNumber":null}
...
]

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



