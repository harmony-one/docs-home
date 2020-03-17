# Querying balances

Get JSON output of balances on all shards of a given ONE address with the `balances` subcommand:

## Using the Binary:

```text
$ ./hmy balances --node="<endpoint-address>" <ONE-address>
```

## Using the Shell Wrapper:

```text
$ ./hmy.sh -- balances --node="<endpoint-address>" <ONE-address>
```

## Example:

```text
$ ./hmy --node=https://api.s0.os.hmny.io/ balances one1km7xg8e3xjys7azp9f4xp8hkw79vm2h3f2lade
```

