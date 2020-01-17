# Harmony CLI

## Introduction

`hmy` is the official Command Line Interface \(CLI\) provided by Harmony. You can use it as a local wallet and as a way to interact with your Ledger Nano device. The `hmy` CLI is completely open-source. You can track its development and post any issues encountered and your feature suggestions [here](https://github.com/harmony-one/go-sdk).

{% hint style="info" %}
Be sure to include the output of `$ hmy version` in your bug reports and preferably include the additional output printed when the environment variable HMY\_ALL\_DEBUG is set to true, like so:

`$ HMY_ALL_DEBUG=true hmy transfer ...`
{% endhint %}

## Features <a id="features"></a>

With the `hmy` CLI you can create a wallet, check your balance, send signed transactions to the Harmony blockchain, query previous transactions, recover keys from previous mnemonics, create new keystores, and create new BLS keys.

## Supported Platforms <a id="platforms"></a>

* OSX: main development platform
* Linux: tested
* Windows: tested / working under Windows Subsystem for Linux \(WSL\) 

