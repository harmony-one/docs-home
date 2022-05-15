# Requirements

{% hint style="warning" %}
It is NOT recommended now to run multiple nodes using the same set of BLS keys. As we are moving towards full decentralization, external validators will become the shard leader and start to propose blocks. If one validator runs multiple nodes using the same set of valid keys, they may all become valid leaders when the key is rotated to this validator, in this case, the blockchain is experiencing a high risk of hard-fork as different valid leaders may propose different blocks. So, do not run redundant validator nodes anymore on the Harmony blockchain. This is also strictly forbidden on all PoS blockchains such as Ethereum 2, Cosmos.
{% endhint %}

## Validator Node: Recommendation

### For Cloud

**CPU**: for `shard 0` nodes, 8 dedicated cores are recommended such as [c5d.2xlarge](https://aws.amazon.com/blogs/aws/ec2-instance-update-c5-instances-with-local-nvme-storage-c5d/) instance type on AWS.\
If you use a VPS with shared CPU, at least 8 cores with 50%+ CPU credit.\
For `shard 1,2,3` the requirement can be halved\
**RAM Memory**: 8GB is minimal\
**Storage**: 3072GB for Shard 0 (as of 14/04/2022). Extra 25GB for Shard 1, 2 and 3 (because when you setup a node on Shard 1, 2 or 3, you also need to download the shard 0 database. Fast local disk is recommend, network storage may hit I/O bottleneck. SSD is the minimal requirement. NVMe drive is better.\
**OS**: Latest Ubuntu Linux (LTS Version)\
**Network**: 100M+ bandwidth, 5\~6 TB data usage per month (preferably more if possible)

Here is a list of some cheap and reliable Cloud Providers (August, 2020):

* [OVH](https://www.ovhcloud.com/)
* [Digital Ocean](https://www.digitalocean.com/)
* [Vultr](https://www.vultr.com/)
* [Hetzner](http://hetzner.com/)
* [Scaleway](https://www.scaleway.com/)
* [Contabo](https://contabo.com/)
* [AWS](https://aws.amazon.com/)

Check [Cloud Guides](cloud-guides/) for instructions.

### For Raspberry Pi

**CPU**: Raspberry Pi 4 with a good Fan and Heat sinker elements\
**RAM Memory**: 8GB\
**Storage**: Fast external SSD with minimum 250GB. Suggestion is Samsung T7 500GB\
**OS**: Latest Ubuntu Linux (LTS Version)\
**Network**: A Modem where you have access to settings like set IP address, Port forwarding and priority settings, 100Mbit/s bandwidth, low latency and flat rate usage. Minimum category 6 Cables

Check [Raspberry Pi Guide](raspberry-pi-guide.md) for instructions.

## Explorer Node: Recommendation

**Setup**: AWS i3en.12xlarge or equivalent, with local disk storage\
**Storage**: \~24TB (4x NVMe SSD) is recommended for Archival Explorer Nodes on Shard 0\
**OS**: Latest Ubuntu Linux (LTS Version)\
**Network**: 100M+ bandwidth
