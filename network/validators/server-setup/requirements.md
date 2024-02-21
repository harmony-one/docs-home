# Requirements

{% hint style="warning" %}
It is NOT recommended now to run multiple nodes using the same set of BLS keys. As we are moving towards full decentralization, external validators will become the shard leader and start to propose blocks. If one validator runs multiple nodes using the same set of valid keys, they may all become valid leaders when the key is rotated to this validator, in this case, the blockchain is experiencing a high risk of hard-fork as different valid leaders may propose different blocks. So, do not run redundant validator nodes anymore on the Harmony blockchain. This is also strictly forbidden on all PoS blockchains such as Ethereum 2, Cosmos.
{% endhint %}

## Validator Node: Recommendation

### For Cloud

#### Validator

<table><thead><tr><th width="131">Specs</th><th>Shard 0</th><th>Shard 1</th></tr></thead><tbody><tr><td>CPU</td><td>8 dedicated core</td><td>4 dedicated core</td></tr><tr><td>RAM</td><td>8 GB </td><td>4 GB</td></tr><tr><td>Storage </td><td>1 TB (using snapDB)<br>SSD Minimum, NVMe recommended</td><td>100GB<br>SSD Minimum, NVMe recommended</td></tr><tr><td>Network</td><td>50Mb/s bandwidth, 5~6 TB data usage per month</td><td>50Mb/s bandwidth, 5~6 TB data usage per month</td></tr><tr><td>OS</td><td>Ubuntu 22 LTS</td><td>Ubuntu 22 LTS</td></tr></tbody></table>

{% hint style="info" %}
Cloud provider CPU's are usually shared unless you specifically chose a dedicated CPU or opt for a dedicated bare metal server
{% endhint %}

Here is a list of  Cloud Providers (August, 2020):

* [OVH](https://www.ovhcloud.com/)
* [Digital Ocean](https://www.digitalocean.com/)
* [Vultr](https://www.vultr.com/)
* [Hetzner](http://hetzner.com/)
* [Scaleway](https://www.scaleway.com/)
* [Contabo](https://contabo.com/)
* [AWS](https://aws.amazon.com/)

Check [Cloud Guides](cloud-guides/) for instructions.

#### RPC / Explorer node Full Node

Same requirement as validator unless specified below:&#x20;

| Specs   | Shard 0                            | Shard 1                             |
| ------- | ---------------------------------- | ----------------------------------- |
| Storage | 6 TB SSD Minimum, NVMe recommended | 50 GB SSD Minimum, NVMe recommended |

#### RPC / Explorer node Archival Node

Same requirement as validator unless specified below:&#x20;

|                       | Shard 0                                   | Shard 1                                     |
| --------------------- | ----------------------------------------- | ------------------------------------------- |
| CPU                   | 16 dedicated core                         | 8 dedicated core                            |
| RAM                   | <p>32GB minimum<br>64GB recommended</p>   | <p>16GB minimum<br>32GB recommended</p>     |
| Storage (21 Feb 2024) | <p>32 TB minimum<br>36 TB recommended</p> | <p>250 GB minimum<br>500 GB recommended</p> |

### For Raspberry Pi

**Same as above for the type of node you wish to run**

A Raspberry Pi 4 with a good Fan and Heat sinker elements will be required\
Check [Raspberry Pi Guide](raspberry-pi-guide.md) for instructions.

