---
description: 'Getting the hmy binary, installing it on your system'
---

# Download and installation

There are multiple ways to get the `hmy` CLI binary.

## Shell wrapper

`hmy` depends on some dynamic libraries, hence we recommend using the following shell wrapper

```shell
$ curl -O https://raw.githubusercontent.com/harmony-one/go-sdk/master/scripts/hmy.sh
$ chmod +x hmy.sh
$ ./hmy.sh -d
```

Now you can use `hmy.sh` as a wrapper over `hmy` and you should assume that all references to `hmy`
in these documents refer to `hmy.sh`.

> Note that since `hmy` is not statically linked, you cannot arbitrarily move `hmy.sh` to anywhere
> on your filesystem like you could with a single binary.

## Compiling from source

If you are interested in compiling from source, then the process is slightly more involved.

### Steps

1. Clone the [repo](https://github.com/harmony-one/go-sdk) at a same level as the main Harmony repo:

```shell
$  pwd
/Users/edgar/Repos/harmony-work/src/github.com/harmony-one
$ ls
bls     go-sdk  harmony mcl
```

2. Have `mcl`, `bls` all built and prepared. This may require you to see instructions in the
   `harmony` repo's `README.md`. 

3. Invoke `source harmony/scripts/setup_bls_build_flags.sh`

4. Call `make` in the `go-sdk` repo, this builds a binary named `hmy`

> These steps are admittedly involved, eventually everything will be statically linked.
