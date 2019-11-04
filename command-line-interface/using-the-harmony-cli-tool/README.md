---
description: Interacting with the Harmony one blockchain
---

# Using the Harmony CLI tool

* [Download, installation](download-and-installation.md)
* [Key management](key-management.md)
* [Creating, sending transactions](creating-sending-transactions.md)
* [Querying the blockchain](querying-the-blockchain.md)
* [Full CLI reference](full-cli-reference.md)

## TL;DR

#### Linux \(pure statically linked binary\)

1. curl -LO https://harmony.one/hmycli
2. chmod +x hmycli
3. Place anywhere on your PATH

#### OS X \(needs to use wrapper script for dynamic libraries\)

1. Go through the steps outlined in [Download and installation](download-and-installation.md#shell-wrapper)

For the impatient, use `hmy cookbook` to see the most common examples & proper arguments.

![](../../.gitbook/assets/hmy-cookbook%20%281%29.gif)

## Introduction

`hmy` is the offical CLI provided by Harmony. You can use it as a local wallet and as a way to interact with your `Ledger Nano` device. Completely open-source, you can track its development and post any issues encountered and your feature suggestions [here](https://github.com/harmony-one/go-sdk).

{% hint style="info" %}
Be sure to include the output of `$ hmy version` in your bug reports and preferably include the additional output printed when the environment variable HMY\_ALL\_DEBUG is set to true, like so:

`$ HMY_ALL_DEBUG=true hmy transfer ...`
{% endhint %}

## Features

With the `hmy` CLI you can send signed transactions to the Harmony blockchain, check previous transactions and recover keys from previous mnemonics.

## Platforms

* OSX: main development platform
* Linux: tested
* Windows: not tested, but in principle should work under Windows Subsystem for Linux \(WSL\)

