---
description: The Harmony CLI tool is used to interact with the Harmony blockchain
---

# Download and setup

## Download Harmony CLI tool

#### 1. For Linux \(pure statically linked binary\)

```text
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

#### 2. For MacOS \(dynamically linked binary\)

`hmy` depends on some dynamic libraries, hence we recommend using the following shell wrapper:

```text
curl -O https://raw.githubusercontent.com/harmony-one/go-sdk/master/scripts/hmy.sh
chmod u+x hmy.sh
./hmy.sh -d
```

Now you can use `hmy.sh` as a wrapper over `hmy` and you should assume that all references to `hmy` in these documents refer to `hmy.sh`.

{% hint style="warning" %}
Note that since `hmy` is not statically linked, you cannot arbitrarily move `hmy.sh` to anywhere on your filesystem like you could with a single binary.
{% endhint %}

#### 3. Compiling from source

If you are interested in compiling from source, then the process is slightly more involved.

**Steps:**

1. Clone the [repo](https://github.com/harmony-one/go-sdk) at the same level as the main Harmony repo:

```text
$  pwd
/Users/edgar/Repos/harmony-work/src/github.com/harmony-one
$ ls
bls     go-sdk  harmony mcl
```

1. Have [`mcl`](https://github.com/harmony-one/mcl), [`bls`](https://github.com/harmony-one/bls) all built and prepared. This may require you to see instructions in the [`harmony`](https://github.com/harmony-one/harmony) repo's `README.md`.
2. Invoke `source harmony/scripts/setup_bls_build_flags.sh`
3. Call `make` in the `go-sdk` repo. This builds a binary named `hmy`

These steps are admittedly involved; eventually everything will be statically linked.

