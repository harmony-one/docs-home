# Querying balance

Get JSON output of balances on all shards of a given one address with the `balances` subcommand, for example:

```text
./hmy --node="https://api.s0.t.hmny.io" balances one1yc06ghr2p8xnl2380kpfayweguuhxdtupkhqzw

[
  {
    "shard": 0,
    "amount": 34705.209868152
  },
  {
    "shard": 1,
    "amount": 88.5
  }
]
```

