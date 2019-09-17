---
description: GetExplorerTx returns information about the requested transaction.
---

# tx

Returns information about a given transaction.

#### Parameters

1. `id` - `String` - Transaction's hash \(ID\).

#### Returns

* `id` - `String` - Transaction's hash.
* `timestamp` - `String` - Transaction's timestamp.
* `from` - `String` - Address of the sender.
* `to` - `String` - Address of the receiver.
* `value` - `Integer` - Amount transferred in ATTO.
* `bytes` - `String` - **TODO: Suneel - Fill in**
* `data` - `String` - Extra data.
* `type` - `String` - Either "SENT" or "RECEIVED". **TODO: Suneel - Why doesn't this get marked?**

#### Sample Curl Request

| Parameter | Value |
| :--- | :--- |
| `id` | `0x7d8329dfd17cf82fcfda4e44f0f59b59c7a1379f173829beb005e94504d99b0f` |

```bash
curl -X GET -H "Content-Type:application/json" e0.b.hmny.io:5000/tx?id=0x7d8329dfd17cf82fcfda4e44f0f59b59c7a1379f173829beb005e94504d99b0f
```

#### Sample Curl Response

```javascript
{
  "id": "0x7d8329dfd17cf82fcfda4e44f0f59b59c7a1379f173829beb005e94504d99b0f",
  "timestamp": "1568241562000",
  "from": "one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw",
  "to": "one1z05g55zamqzfw9qs432n33gycdmyvs38xjemyl",
  "value": 1e+20,
  "bytes": "108",
  "data": "",
  "type": ""
}
```

