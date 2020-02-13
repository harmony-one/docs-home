---
description: hmy_pendingTransactions
---

# hmy\_pendingTransactions

## API v1

Returns list of pending transactions object. See [hmy\_getTransactionByHash](hmy_gettransactionbyhash.md) for result format.

#### Sample Curl Request

```text
curl --location --request POST 'https://api.s0.b.hmny.io/' \
--header 'Content-Type: application/json' \
--data-raw '{
    "jsonrpc": "2.0",
    "method": "hmy_pendingTransactions",
    "params": [],
    "id": 1
}'
```

## API v2

Returns list of pending transactions object. See [hmy\_getTransactionByHash](hmy_gettransactionbyhash.md) for result format.

#### Sample Curl Request

```text
curl --location --request POST 'https://api.s0.b.hmny.io/' \
--header 'Content-Type: application/json' \
--data-raw '{
    "jsonrpc": "2.0",
    "method": "hmyv2_pendingTransactions",
    "params": [],
    "id": 1
}'
```

