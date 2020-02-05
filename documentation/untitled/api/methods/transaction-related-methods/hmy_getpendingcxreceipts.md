---
description: hmy_getPendingCXReceipts
---

# hmy\_getPendingCXReceipts

## API v1

### Returns

Array of pending cx receipts in tx pool. See hmy\_getCXReceiptByHash for format

### Sample Curl Request

```text
curl --location --request POST 'https://api.s0.b.hmny.io/' \
--header 'Content-Type: application/json' \
--data-raw '{
    "jsonrpc": "2.0",
    "method": "hmy_getPendingCXReceipts",
    "params": [],
    "id": 1
}'
```

### Sample Curl Response

See hmy\_getCXReceiptByHash response

## API v2

### Returns

Array of pending cx receipts in tx pool. See hmy\_getCXReceiptByHash for format

### Sample Curl Request

```text
curl --location --request POST 'https://api.s0.b.hmny.io/' \
--header 'Content-Type: application/json' \
--data-raw '{
    "jsonrpc": "2.0",
    "method": "hmyv2_getPendingCXReceipts",
    "params": [],
    "id": 1
}'
```

### Sample Curl Response

See hmy\_getCXReceiptByHash response

