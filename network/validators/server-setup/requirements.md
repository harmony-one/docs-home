# Requirements

{% hint style="success" %}
We recommend that you run two nodes on two different regions around the globe for **better signing rate** and **high availability**. Differently from other blockchains, Harmony allows you to run multiple nodes with the same BLS keys. This is not considered double signing.

One configuration could be positioning one node in North America and another one with the same BLS keys in Asia or Europe, for example.
{% endhint %}

## Validator Node: Recommendation

### For Cloud

**CPU**: for shard 0 nodes, 4 dedicated cores is recommended such like [c5d.xlarge](https://aws.amazon.com/blogs/aws/ec2-instance-update-c5-instances-with-local-nvme-storage-c5d/) instance type on AWS. If you use VPS with shared CPU, at least 8 cores with 50%+ CPU credit; for shard 1,2,3, the requirement can be halved right now since there are not that many transactions. **RAM Memory**: 8GB  
**Storage**: 163GB for Shard 0 \(as of 09/02/2021\). Extra 15GB for Shard 1, 2 and 3 \(July, 2021\) \(because when you setup a node on Shard 1, 2 or 3, you also need to download the databse of Shard 0\) fast local disk is recommend, network storage may hit I/O bottleneck.  
**OS**: Latest Ubuntu Linux \(LTS Version\)  
**Network**: 100M+ bandwidth, 5~6 TB data usage per month \(preferably more if possible\)

Here is a list of some cheap and reliable Cloud Providers \(August, 2020\):

* [OVH](https://www.ovhcloud.com/)
* [Digital Ocean](https://www.digitalocean.com/)
* [Vultr](https://www.vultr.com/)
* [Hetzner](http://hetzner.com/)
* [Scaleway](https://www.scaleway.com/)
* [Contabo](https://contabo.com/)
* [AWS](https://aws.amazon.com/)

Check [Cloud Guides](cloud-guides/) for instructions.

### For Raspberry Pi

**CPU**: Raspberry Pi 4 with a good Fan and Heat sinker elements  
**RAM Memory**: 8GB  
**Storage**: Fast external SSD with minimum 250GB. Suggestion is Samsung T7 500GB  
**OS**: Latest Ubuntu Linux \(LTS Version\)  
**Network**: A Modem where you have access to settings like set IP address, Port forwarding and priority settings, 100Mbit/s bandwidth, low latency and flat rate usage. Minimum category 6 Cables

Check [Raspberry Pi Guide](raspberry-pi-guide.md) for instructions.

## Explorer Node: Recommendation

**Setup**: AWS i3en.6xlarge or equivalent  
**Storage**: 15000 GiB \(2 \* 7500 GiB NVMe SSD\) is recommended for Archival Explorer Nodes on Shard 0  
**OS**: Latest Ubuntu Linux \(LTS Version\)  
**Network**: 100M+ bandwidth

