# Harmony CLI

## Introduction

`hmy` is the official CLI provided by Harmony. You can use it as a local wallet and as a way to interact with your `Ledger Nano` device. Completely open-source, you can track its development and post any issues encountered and your feature suggestions [here](https://github.com/harmony-one/go-sdk).

{% hint style="info" %}
Be sure to include the output of `$ hmy version` in your bug reports and preferably include the additional output printed when the environment variable HMY\_ALL\_DEBUG is set to true, like so:

`$ HMY_ALL_DEBUG=true hmy transfer ...`
{% endhint %}

## Features <a id="features"></a>

With the `hmy` CLI you can send signed transactions to the Harmony blockchain, check previous transactions, recover keys from previous mnemonics, create new keystores, create new BLS keys etc.

## Platforms <a id="platforms"></a>

* OSX: main development platform
* Linux: tested
* Windows: tested / working under Windows Subsystem for Linux \(WSL\) 

