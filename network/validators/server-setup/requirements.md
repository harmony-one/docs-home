# Requirements

{% hint style="success" %}
We recommend that you run two nodes on two different regions around the globe for **better signing rate** and **high availability**. Differently from other blockchains, Harmony allows you to run multiple nodes with the same BLS keys. This is not considered double signing.  
  
One configuration could be positioning one node in North America and another one with the same BLS keys in Asia or Europe, for example.
{% endhint %}

Here is a list of some cheap and reliable Cloud Providers \(August, 2020\):

* [Digital Ocean](https://www.digitalocean.com/)
* [Vultr](https://www.vultr.com/)
* [Hetzner](http://hetzner.com/)
* [Scaleway](https://www.scaleway.com/)
* [Contabo](https://contabo.com/)
* [AWS](https://aws.amazon.com/)
* [Ankr](https://www.ankr.com/)

## VPS Recommendation

**CPU**: for shard 0 nodes, 4 dedicated cores is recommended such like [c5d.xlarge](https://aws.amazon.com/blogs/aws/ec2-instance-update-c5-instances-with-local-nvme-storage-c5d/) instance type on AWS. If you use VPS with shared CPU, at least 8 cores with 50%+ CPU credit; for shard 1,2,3, the requirement can be halved right now since there is not much transactions.  
**RAM Memory**: 8GB  
**Storage**: 50GB for Shard 0. Extra 15GB for Shard 1, 2 and 3 \(May, 2021\), fast local disk is recommend, network storage may hit I/O bottleneck.  
**OS**: Latest Ubuntu Linux \(LTS Version\)  
**Network**: 100M+ bandwidth, 5~6 TB data usage per month

Check our [Cloud Guide](https://docs.harmony.one/home/validators/cloud-setup/cloud-guides) for instructions.

