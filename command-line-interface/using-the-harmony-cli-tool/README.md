---
description: Interacting with the Harmony one blockchain
---

# Using the Harmony CLI tool

## Overview

The harmony binary, known as `hmy_cli` is your one stop shop to interact with the Harmony blockchain from the CLI. With `hmy_cli` you can:

* manage your locally stored keys
* query the Harmony network 
* create transactions

### Installation

Download `hmy_cli` from TODO S3 LINK and add it to anywhere on your `$PATH`.

### Initial Usage and getting acquainted

`hmy_cli` follows a _fluent API_, that is, the commands flow like an English sentence. Get a feel for the program by invoking it without any subcommand. The examples assume that `hmy_cli` is on your `PATH` already but you can invoke it directly from where you downloaded it with `./hmy_cli`

```text
$ hmy_cli

CLI interface to the Harmony blockchain

Usage:
  hmy_cli [flags]
  hmy_cli [command]

Available Commands:
  account     Query account balance
  blockchain  Interact with the Harmony.one Blockchain
  docs        Generate docs to a local hmy_cli-docs directory
  help        Help about any command
  keys        Add or view local private keys
  version     Show version

Flags:
  -h, --help     help for hmy_cli
  -p, --pretty   pretty print JSON outputs

Use "hmy_cli [command] --help" for more information about a command.
```

As a quick example, let's invoke the simplest subcommand, `version`

```text
$ hmy_cli version
v19 df07dfa-dirty 2019-08-23T14:19:07-0700 edgar@harmony.one
```

This dumps out useful build metadata information about the binary itself, be sure to include this information in any issue you might encounter with `hmy_cli` when letting the Harmony team know about bugs/issues.

As shown, we have subcommands for the key features you will need to interact with the blockchain. Refer to the other subpages in this wiki for usage and examples subcommands.

### Building local docs

Notice that `hmy_cli` has a subcommand called `docs`, invoking this command generates a directory called `hmy_cli-docs` in the same directory that `hmy_cli docs` was invoked in. In `hmy_cli-docs` will be markdown files with documentation of all the commands.

