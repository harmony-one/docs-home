---
description: >-
  GetExplorerCommittee returns a list of network of a particular shard and
  epoch.
---

# committee

Returns a list of network of a particular shard and epoch. To get current list of validators you should pass epoch from current block.

## Parameters

* `shard_id` - `Integer` - Shard to query.
* `epoch` - `Integer` - Defaults to current epoch.

## Returns

* `validators` - `Array` - Array of all of the validators.

## Sample Curl Request

| Parameter | Value |
| :--- | :--- |
| `shard_id` | `0` |
| `epoch` | `0` |

```bash
curl -H "Content-Type:application/json" -X GET "e0.b.hmny.io:5000/committee?shard_id=0&epoch=0"
```

## Sample Curl Response

```javascript
{
  "validators": [
    {
      "address": "one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw",
      "balance": 6103521642043592000000
    },
    {
      "address": "one1shzkj8tty2wu230wsjc7lp9xqkwhch2ea7sjhc",
      "balance": 8327211831740720000000
    },
    {
      "address": "one1puj38zamhlu89enzcdjw6rlhlqtyp2c675hjg5",
      "balance": 8410554014194876000000
    },
    {
      "address": "one1z0udzslh8pn082pnfhg9jx6ekwsem88v24k2v5",
      "balance": 10950921904207266000000
    },
    {
      "address": "one1dpm37ppsgvepjfyvsamas25md280ctgmcfjlfx",
      "balance": 10801160103441872000000
    },
    {
      "address": "one13uqaxe8wr2j3azj7sytv59ua0ff322auh270mc",
      "balance": 10973142420484450000000
    },
    {
      "address": "one1gzf2cmv607r64nths76ur3z5rkdl9n2ucnaw66",
      "balance": 7667735618008520000000
    },
    {
      "address": "one1l4dp4ksy85fzchlr5pgdp5we0lpc8dsyzga6y5",
      "balance": 11139791882723510000000
    },
    {
      "address": "one12zlfzd2tyfngcghslrmv57xmn7ec4cqct32sks",
      "balance": 7373671505125239000000
    },
    {
      "address": "one1mwr4d2awwcx7f2n3c90lykt6r6sjv4agfn8k7m",
      "balance": 11104470510644150000000
    },
    {
      "address": "one1yd8hywc5rhas63l2mn9a49hg8znfnha2zntunc",
      "balance": 10983256876056509000000
    },
    .
    .
    .
    {
      "address": "one17nhau9quvr6492dkl54qenp5tsx8v2d7zd7hj7",
      "balance": 1.5e+19
    }
  ]
}
```

