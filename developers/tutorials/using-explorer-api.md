---
description: >-
  This page describes endpoints of harmony explorer to programmatically access
  the data.
---

# Using Explorer EndPoints

{% swagger baseUrl="https://explorer-v2-api.hmny.io/v0/erc20/" path="/v0/erc20/" method="get" summary="List all HRC20 tokens" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io" path="/v0/erc721/" method="get" summary="List all HRC721 tokens" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io" path="/v0/erc1155" method="get" summary="List all HRC1155 tokens" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io" path="/v0/erc20/address/:token_addr/balances" method="get" summary="HRC20 Balance of an address" %}
{% swagger-description %}
Get the HRC20 balance of an address. 

\




`https://explorer-v2-api.hmny.io/v0/erc20/address/0x8454bf4fc72687b61eaf1bcd64bb9e78983fbdd7/balances`
{% endswagger-description %}

{% swagger-parameter in="path" name="token_addr" type="string" %}
HRC20 token address
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io" path="v0/erc721/address/:token_addr/balances" method="get" summary="HRC721/1155 Balance of an address" %}
{% swagger-description %}
Get the HRC721/HRC1155 balance of an address

\




`https://explorer-v2-api.hmny.io/v0/erc721/address/0x847826f2d552c87d2ee6f38b65425fc85befe841/balances`
{% endswagger-description %}

{% swagger-parameter in="path" name="" type="string" %}
HRC20 token address
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io" path="/v0/price/actual/ONEUSDT" method="get" summary="ONE-USDT Price" %}
{% swagger-description %}
Get the price of ONE in USDT

\


Example:

\




`https://explorer-v2-api.hmny.io/v0/price/actual/ONEUSDT`
{% endswagger-description %}

{% swagger-parameter in="path" name="" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io" path="/v0/shard/:shard_id/address/:address/transactions/type/transaction?offset=0&limit=10" method="get" summary="All Transactions" %}
{% swagger-description %}
`https://explorer-v2-api.hmny.io/v0/shard/0/address/0x7912111622cb6455156ceb8a4b17c8c2ce6e7dab/transactions/type/transaction?offset=0&limit=10`
{% endswagger-description %}

{% swagger-parameter in="path" name="shard_id" type="string" %}
shard id
{% endswagger-parameter %}

{% swagger-parameter in="path" name="address" type="string" %}
hex address
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io" path="/v0/shard/:shard_id/address/0xdd46509b31b87f05a0da47e6ff9cdaa5563e7a57/transactions/type/erc20?offset=0&limit=10" method="get" summary="HRC20 Transactions" %}
{% swagger-description %}
Get all HRC20 transactions.

\


Example:

\




`https://explorer-v2-api.hmny.io/v0/shard/0/address/0xdd46509b31b87f05a0da47e6ff9cdaa5563e7a57/transactions/type/erc20?offset=0&limit=10`
{% endswagger-description %}

{% swagger-parameter in="path" name="" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io/" path="/v0/shard/:shard_id/address/:token_addr/transactions/type/erc721?offset=0&limit=10" method="get" summary="NFT (HRC721/HRC1155) Transactions" %}
{% swagger-description %}
Get the transactions of an HRC721/HRC1155 token.

\


Example:

\




`https://explorer-v2-api.hmny.io/v0/shard/0/address/0xe59a79c7516d22a488a3f479626e75a2e81aae66/transactions/type/erc721?offset=0&limit=10`
{% endswagger-description %}

{% swagger-parameter in="path" name="shard_id" type="string" %}
shard id
{% endswagger-parameter %}

{% swagger-parameter in="path" name="token_addr" type="string" %}
HRC721/HRC1155 token contract address
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io/" path="/v0/shard/:shard_id/logs/transaction/hash/:txn_hash" method="get" summary="Logs" %}
{% swagger-description %}
Get the event logs of a transaction.

\


Example:

\




`https://explorer-v2-api.hmny.io/v0/shard/0/logs/transaction/hash/0x0d449c8dde6c13e63064f49c531ba028878a4de368473cdff421255000c8047f`
{% endswagger-description %}

{% swagger-parameter in="path" name="shard_id" type="string" %}
shard id
{% endswagger-parameter %}

{% swagger-parameter in="path" name="txn_hash" type="string" %}
transaction hash
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://explorer-v2-api.hmny.io" path="/v0/erc20/token/:token_addr/holders?limit=100&offset=0" method="get" summary="Token Holders" %}
{% swagger-description %}
Get the list of token holders of an HRC20 token. 

\


Example:

\




`https://explorer-v2-api.hmny.io/v0/erc20/token/0xcf664087a5bb0237a0bad6742852ec6c8d69a27a/holders?limit=100&offset=0`
{% endswagger-description %}

{% swagger-parameter in="path" name="Token Address" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
[
{"ownerAddress":"0xeb049f1ed546f8efc3ad57f6c7d22f081ccc7375","tokenAddress":"0xcf664087a5bb0237a0bad6742852ec6c8d69a27a","balance":"84198183077703161163395138","needUpdate":false,"lastUpdateBlockNumber":null}
...
]

```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://ctrver.t.hmny.io/fetchContractCode?contractAddress=" summary="Fetch contract information" %}
{% swagger-description %}
[https://ctrver.t.hmny.io/fetchContractCode?contractAddress=0xcf664087a5bb0237a0bad6742852ec6c8d69a27a](https://ctrver.t.hmny.io/fetchContractCode?contractAddress=0xcf664087a5bb0237a0bad6742852ec6c8d69a27a)


{% endswagger-description %}

{% swagger-parameter in="query" required="true" name="contractAddress" %}
Contract address
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="JSON output" %}
```javascript
{
    "contractAddress": "0xcf664087a5bb0237a0bad6742852ec6c8d69a27a",
    "constructorArguments": "",
    "libraries": [],
    "sourceCode": "...",
    "compiler": "0.6.6",
    "contractName": "WONE",
    "abi": [
        {
            "type": "event",
            "anonymous": false,
            "name": "Approval",
            "inputs": [
                {
                    "name": "src",
                    "type": "address",
                    "indexed": true,
                    "internalType": "address"
                },
                {
                    "name": "guy",
                    "internalType": "address",
                    "indexed": true,
                    "type": "address"
                },
                {
                    "type": "uint256",
                    "indexed": false,
                    "internalType": "uint256",
                    "name": "wad"
                }
            ]
        },
        {
            "type": "event",
            "anonymous": false,
            "name": "Deposit",
            "inputs": [
                {
                    "type": "address",
                    "name": "dst",
                    "internalType": "address",
                    "indexed": true
                },
                {
                    "name": "wad",
                    "type": "uint256",
                    "indexed": false,
                    "internalType": "uint256"
                }
            ]
        },
        {
            "anonymous": false,
            "name": "Transfer",
            "type": "event",
            "inputs": [
                {
                    "name": "src",
                    "indexed": true,
                    "internalType": "address",
                    "type": "address"
                },
                {
                    "indexed": true,
                    "name": "dst",
                    "type": "address",
                    "internalType": "address"
                },
                {
                    "type": "uint256",
                    "name": "wad",
                    "indexed": false,
                    "internalType": "uint256"
                }
            ]
        },
        {
            "anonymous": false,
            "inputs": [
                {
                    "internalType": "address",
                    "type": "address",
                    "indexed": true,
                    "name": "src"
                },
                {
                    "internalType": "uint256",
                    "name": "wad",
                    "indexed": false,
                    "type": "uint256"
                }
            ],
            "name": "Withdrawal",
            "type": "event"
        },
        {
            "stateMutability": "view",
            "inputs": [
                {
                    "internalType": "address",
                    "type": "address",
                    "name": ""
                },
                {
                    "internalType": "address",
                    "name": "",
                    "type": "address"
                }
            ],
            "type": "function",
            "name": "allowance",
            "outputs": [
                {
                    "name": "",
                    "internalType": "uint256",
                    "type": "uint256"
                }
            ]
        },
        {
            "stateMutability": "view",
            "type": "function",
            "name": "balanceOf",
            "inputs": [
                {
                    "internalType": "address",
                    "name": "",
                    "type": "address"
                }
            ],
            "outputs": [
                {
                    "type": "uint256",
                    "internalType": "uint256",
                    "name": ""
                }
            ]
        },
        {
            "name": "decimals",
            "outputs": [
                {
                    "type": "uint8",
                    "name": "",
                    "internalType": "uint8"
                }
            ],
            "stateMutability": "view",
            "type": "function",
            "inputs": []
        },
        {
            "stateMutability": "view",
            "inputs": [],
            "name": "name",
            "outputs": [
                {
                    "internalType": "string",
                    "name": "",
                    "type": "string"
                }
            ],
            "type": "function"
        },
        {
            "type": "function",
            "name": "symbol",
            "stateMutability": "view",
            "inputs": [],
            "outputs": [
                {
                    "name": "",
                    "internalType": "string",
                    "type": "string"
                }
            ]
        },
        {
            "type": "receive",
            "stateMutability": "payable"
        },
        {
            "type": "function",
            "name": "deposit",
            "stateMutability": "payable",
            "inputs": [],
            "outputs": []
        },
        {
            "outputs": [],
            "name": "withdraw",
            "type": "function",
            "inputs": [
                {
                    "internalType": "uint256",
                    "type": "uint256",
                    "name": "wad"
                }
            ],
            "stateMutability": "nonpayable"
        },
        {
            "outputs": [
                {
                    "type": "uint256",
                    "internalType": "uint256",
                    "name": ""
                }
            ],
            "type": "function",
            "stateMutability": "view",
            "inputs": [],
            "name": "totalSupply"
        },
        {
            "name": "approve",
            "stateMutability": "nonpayable",
            "type": "function",
            "outputs": [
                {
                    "type": "bool",
                    "internalType": "bool",
                    "name": ""
                }
            ],
            "inputs": [
                {
                    "internalType": "address",
                    "name": "guy",
                    "type": "address"
                },
                {
                    "name": "wad",
                    "internalType": "uint256",
                    "type": "uint256"
                }
            ]
        },
        {
            "type": "function",
            "inputs": [
                {
                    "name": "dst",
                    "type": "address",
                    "internalType": "address"
                },
                {
                    "name": "wad",
                    "type": "uint256",
                    "internalType": "uint256"
                }
            ],
            "name": "transfer",
            "stateMutability": "nonpayable",
            "outputs": [
                {
                    "internalType": "bool",
                    "name": "",
                    "type": "bool"
                }
            ]
        },
        {
            "inputs": [
                {
                    "name": "src",
                    "internalType": "address",
                    "type": "address"
                },
                {
                    "type": "address",
                    "name": "dst",
                    "internalType": "address"
                },
                {
                    "type": "uint256",
                    "internalType": "uint256",
                    "name": "wad"
                }
            ],
            "outputs": [
                {
                    "name": "",
                    "internalType": "bool",
                    "type": "bool"
                }
            ],
            "name": "transferFrom",
            "type": "function",
            "stateMutability": "nonpayable"
        }
    ],
    "cached": {
        "ttl": 1654010977245,
        "cached": true
    },
    "proxyDetails": null
}
```
{% endswagger-response %}
{% endswagger %}
