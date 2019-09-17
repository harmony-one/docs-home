---
description: GetExplorerBlocks returns information about the requested block(s).
---

# blocks

Returns information about the block\(s\) specified by the parameters.

#### Parameters

{% hint style="info" %}
The search range specified by `from` and `to` is inclusive of the ends, meaning `from=0&to=5` will return the blocks at indices 0, 1, 2, 3, 4, and 5.

If `from` and `to` are both some index **n**, then `blocks` will return the **n**th block.
{% endhint %}

* `from` - `Integer` - Beginning of search range.
* `to` - `Integer` - _\(Optional\)_ End of search range.
* `with_signers` - `Boolean` - _\(Optional\)_ If response contains block signers. Defaults to `false`.
* `offset` - `Integer` - _\(Optional\)_ How many blocks are listed per page.
* `page` - `Integer` - _\(Optional\)_ Which page to view.

#### Returns

* An array of blocks.
  * `height` - `String` - Block's height in the blockchain.
  * `id` - `String` - Block's hash.
  * `txCount` - `String` - How many transactions the block contains.
  * `timestamp` - `String` - Block's timestamp.
  * `blockTime` - `Integer` - Time it took to mine the block.
  * `merkleRoot` - `String` - Hash of all of the transaction hashes in the block; The root of the block's Merkle Patricia state trie.
  * `prevBlock` - `Object` 
    * `id` - `String` - Hash of the previous block in the chain.
    * `height` - `Integer` - Height of the previous block in the chain.
  * `bytes` - `String` - **TODO: Suneel - Fill in**
  * `nextBlock` - `Object` 
    * `id` - `String` - Hash of the next block in the chain.
    * `height` - `Integer` - Height of the next block in the chain.
  * `txs` - **TODO: Suneel - Is this implemented? Always returns null even if the block has transactions.**
  * `signers` - `Array` - Signers of this block.
  * `epoch` - `Integer` - Epoch this was mined in.
  * `extra_data` - `String` - Block's extra data.

#### Sample Curl Request

| Parameter | Value |
| :--- | :--- |
| `from` | `0` |
| `to` | `4` |

```bash
curl -H "Content-Type:application/json" -X GET "http://e1.b.hmny.io:5000/blocks?from=0&to=4"
```

#### Sample Curl Response

```javascript
[
  {
    "height": "0",
    "id": "0xb0d3bf0992e9036112b64429875f4000c265bb2ac60be30f23e1f75af7904c66",
    "txCount": "0",
    "timestamp": "1561734000000",
    "blockTime": 0,
    "merkleRoot": "0xae22370df046aa8c4470a032ecc88609efc08438abe79fd9e7f134b077a11fb6",
    "prevBlock": {
      "id": "",
      "height": ""
    },
    "bytes": "11461",
    "nextBlock": {
      "id": "0xe61c2e1a923ff5115029e01eff1be0cf88ec9dee158b60db9742c1c730e5bc08",
      "height": "1"
    },
    "txs": null,
    "signers": [],
    "epoch": 0,
    "extra_data": "Harmony for One and All. Open Consensus for 10B."
  },
  {
    "height": "1",
    "id": "0xe61c2e1a923ff5115029e01eff1be0cf88ec9dee158b60db9742c1c730e5bc08",
    "txCount": "0",
    "timestamp": "1568163268000",
    "blockTime": 6429268,
    "merkleRoot": "0xae22370df046aa8c4470a032ecc88609efc08438abe79fd9e7f134b077a11fb6",
    "prevBlock": {
      "id": "0xb0d3bf0992e9036112b64429875f4000c265bb2ac60be30f23e1f75af7904c66",
      "height": "0"
    },
    "bytes": "601",
    "nextBlock": {
      "id": "0x560986a1ea2142b2a3ae0a0175fe39bf0d3b85773c5bf5906be2aecb0f76410f",
      "height": "2"
    },
    "txs": null,
    "signers": [],
    "epoch": 0,
    "extra_data": ""
  },
  {
    "height": "2",
    "id": "0x560986a1ea2142b2a3ae0a0175fe39bf0d3b85773c5bf5906be2aecb0f76410f",
    "txCount": "0",
    "timestamp": "1568163276000",
    "blockTime": 8,
    "merkleRoot": "0x463c7ad17674b2a07884139cb50c4c7b8782f0097d1fad88f6a6063f0eb1329e",
    "prevBlock": {
      "id": "0xe61c2e1a923ff5115029e01eff1be0cf88ec9dee158b60db9742c1c730e5bc08",
      "height": "1"
    },
    "bytes": "620",
    "nextBlock": {
      "id": "0xc34d8d33c0bc709bea660bb6665514247ff73f2a58db17e415acbcb1b0c56613",
      "height": "3"
    },
    "txs": null,
    "signers": [],
    "epoch": 0,
    "extra_data": ""
  },
  {
    "height": "3",
    "id": "0xc34d8d33c0bc709bea660bb6665514247ff73f2a58db17e415acbcb1b0c56613",
    "txCount": "0",
    "timestamp": "1568163284000",
    "blockTime": 8,
    "merkleRoot": "0xc8262fd52c8912d8bad90a8ece6fadffc258611ab045b09403a67f870b9d568c",
    "prevBlock": {
      "id": "0x560986a1ea2142b2a3ae0a0175fe39bf0d3b85773c5bf5906be2aecb0f76410f",
      "height": "2"
    },
    "bytes": "620",
    "nextBlock": {
      "id": "0x1a07f5bfcd36b121092f88469c96ae235be958c720486187d3501ca96bf42067",
      "height": "4"
    },
    "txs": null,
    "signers": [],
    "epoch": 0,
    "extra_data": ""
  },
  {
    "height": "4",
    "id": "0x1a07f5bfcd36b121092f88469c96ae235be958c720486187d3501ca96bf42067",
    "txCount": "0",
    "timestamp": "1568163292000",
    "blockTime": 8,
    "merkleRoot": "0x0b1122790b3d6c5523d067dbcc7a809f1b0e7263e9d216644ba9a3dfc9f58d1c",
    "prevBlock": {
      "id": "0xc34d8d33c0bc709bea660bb6665514247ff73f2a58db17e415acbcb1b0c56613",
      "height": "3"
    },
    "bytes": "620",
    "nextBlock": {
      "id": "0x9c17813c409e63ed8f4ea437b4fede1d16cdc9e0f02c3e00d068def23688ecc9",
      "height": "5"
    },
    "txs": null,
    "signers": [],
    "epoch": 0,
    "extra_data": ""
  }
]
```



