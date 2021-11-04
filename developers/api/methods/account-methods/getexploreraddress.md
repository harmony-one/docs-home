---
description: GetExplorerAddress returns the transaction history of an address
---

# address

Returns information about the transaction history of a given address with a configurable format.

## Parameters

1. `id` - `String` -  The address to get the balance of.
2. `offset` - `Integer` - _(Optional)_ Number of address transactions per page.
3. `page` - `Integer` - _(Optional)_ Page number in transactions list (default is 0.)
4. `tx_view` - `String` - _(Optional)_ 4 values:
   1. "NONE" - (default) Show no address transactions
   2. "ALL" - Show all address transactions
   3. "RECEIVED" - Show only transactions this address received
   4. "SENT" - Show only transaction this address sent

## Result

* `id` - `String` - Account address.
* `balance` - `Integer` - Account balance.
* `txs` - `Array` - Collection of the account's transactions; number of transactions listed and type of transaction are specified by `offset`, `page`, and `tx_view`.
  * `id` - `String` - Transaction's hash.
  * `timestamp` - `String` - Transaction's timestamp.
  * `from` - `String` - Address of the sender.
  * `to` - `String` - Address of the receiver.
  * `value` - `Integer` - Amount transferred in ATTO.
  * `bytes` - `String` - **TODO: Suneel**
  * `data` - `String` - Extra data.
  * `type` - `String` - Either "SENT" or "RECEIVED".

## Sample Curl Request

| Param     | Value                                        |
| --------- | -------------------------------------------- |
| `id`      | `one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7` |
| `offset`  | `5`                                          |
| `tx_view` | `ALL`                                        |
| `page`    | `2`                                          |

```bash
curl -H "Content-Type:application/json" -X GET "e0.b.hmny.io:5000/address?id=one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7&tx_view=ALL&offset=5&page=2"
```

## Sample Curl Response

```javascript
{
  "id": "one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7",
  "balance": 1438299000000000600000,
  "txs": [
    {
      "id": "0xb02930434b5f9aa2d8dd502c81c1434cc988f09c9bcaa9e7ef3c4fcf4d8db82d",
      "timestamp": "1568672871000",
      "from": "one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7",
      "to": "one16ll5rj3fxpsjyxz6qlgy9y7akd0jfneds0x9pu",
      "value": 65535,
      "bytes": "101",
      "data": "",
      "type": "SENT"
    },
    {
      "id": "0x163f59fe6fa827409146fe3fadbd38ba57e4beb72f0e8094225e33ee3e55a0cf",
      "timestamp": "1568672725000",
      "from": "one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7",
      "to": "one16ll5rj3fxpsjyxz6qlgy9y7akd0jfneds0x9pu",
      "value": 65535,
      "bytes": "101",
      "data": "",
      "type": "SENT"
    },
    {
      "id": "0x38000e2d8bc1d30d66a214c583b3f2724a925f97aaf572eb5c5551e0a8e231e2",
      "timestamp": "1568672619000",
      "from": "one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7",
      "to": "one16ll5rj3fxpsjyxz6qlgy9y7akd0jfneds0x9pu",
      "value": 65535,
      "bytes": "101",
      "data": "",
      "type": "SENT"
    },
    {
      "id": "0x545ed7c1e14d28323dff5a159e6f788205b528ad8400c1e90fc7bd64433e2526",
      "timestamp": "1568672424000",
      "from": "one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7",
      "to": "one16ll5rj3fxpsjyxz6qlgy9y7akd0jfneds0x9pu",
      "value": 65535,
      "bytes": "101",
      "data": "",
      "type": "SENT"
    },
    {
      "id": "0xcfc8787d0209edb51994d265d5b0cef14d90a029d9fc6bf564853f9d5e766511",
      "timestamp": "1568672293000",
      "from": "one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7",
      "to": "one16ll5rj3fxpsjyxz6qlgy9y7akd0jfneds0x9pu",
      "value": 4095,
      "bytes": "101",
      "data": "",
      "type": "SENT"
    }
  ]
}
```
