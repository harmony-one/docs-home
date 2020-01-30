---
description: SendRawStakingTransaction
---

# hmy\_sendRawStakingTransaction

## Overview

A staking transaction is like a plain sharded transaction, [hmy\_sendRawTransaction](hmy_sendrawtransaction.md), but with a single field that is not known ahead of time. This field is the staking message itself, which in the harmony go code base, we refer to as `StakeMsg`

## Input

The input is a single RLP encoded version of a StakingTransaction 

