# Choosing A Cloud Provider

**Which cloud provider to choose for your Harmony node?** 

I decided to put together a list of possible cloud providers and some examples of their instances that can be used. Note that I used recommended settings such as 4 GB RAM and at least 2vCPU. Although you can probably run away with a 2 GB RAM instance, it is not recommended, as the performance might be lesser and so will the rewards. All prices displayed are based on a monthly basis. Important note: currently the blockchain size for non shard 0 nodes is around 100GB \(because they have to sync their own shard and also shard 0, which is called beacon chain\). Shard 0 nodes blockchain size is around 50GB at the moment. This is at the time of writing. We can expect this to grow larger until the Harmony team introduces state pruning which should significantly lower the size.

**AWS \(Amazon Web Services\)** 

Amazon offers powerful networking options and a large array of hardware specs. They offer speeds from 1 Gigabit and up to 100 Gigabit. Their T instances are burst instances, which means they are capable of high performance for a while only. After that if the instance is still stretched you might get charged extra. They offer 3 kinds of instance purchases: Spot instance: A Spot Instance is an unused EC2 instance that is available for less than the On-Demand price. Because Spot Instances enable you to request unused EC2 instances at steep discounts, you can lower your Amazon EC2 costs significantly. The hourly price for a Spot Instance is called a Spot price. Note that although you save some money compared to on demand instances, there is a high chance the EC2 service will take them back when they need the extra capacity, or you might even have to pay more. On demand instance: this one is self explanatory, you pick an instance you wish to run, set it up and launch it. This is the default option. Reserved instance \(RI\): this type allows you to reserve an instance type for a period in advance, for which you receive a significant discount. However no matter if you still need it or not, you have to pay for it as long as the reserved period lasts \(usually 1 year\) Here is the link for explanation of the burst instances: [https://www.cloudhealthtech.com/blog/amazon-burstable-instances-explained](https://www.cloudhealthtech.com/blog/amazon-burstable-instances-explained) 

IMPORTANT NOTE: Bandwidth is charged on a pay-as-you-go basis, and it is calculated on the actual bandwidth usage \(GB\) in your last month multiplied by AWS bandwidth charges \($0.12/GB\). For example, if your server consumed 100GB bandwidth in a month, you will be charged for $12 \(100GB x $0.12\). Only the first 1GB is free, everything else is payable on top of the instance cost. Currently the data charges for a Harmony mainnet node are around 35 USD extra per month. Relevant offers: T2.medium: EBS storage, 2 vCPU, 4GB RAM – PRICE is around 30 USD, depending on the region T3.medium: EBS storage, 2 vCPU, 4GB RAM \(but a longer burst time\) – PRICE is around 30 USD, depending on the region M5a.large: EBS storage, 2 vCPU, 8GB RAM and is not a burst instance. Network speed is up to 10 Gigabit – PRICE is around 60 USD, depending on the region There are also AMD CPU versions of all of the above instances which are also good and a little bit cheaper. They are named like this: T3a.medium, M5a.large. NOTE: if you purchase a RI version of the above instances, then you get a discount of up to 50% on your instance. It also heavily depends on the region you want to launch it. For reference, you can check this website which has a table of the information and a lot of filters: [https://www.ec2instances.info/?min\_memory=4&min\_vcpus=2&region=us-west-2&cost\_duration=monthly](https://www.ec2instances.info/?min_memory=4&min_vcpus=2&region=us-west-2&cost_duration=monthly) 

Payment options: Credit card – they prefer business accounts, you will have a lot less problems and less questions about what you are using them for. 

Setup: Instant

**Vultr** 

Vultr is another very popular option amongst Harmony node runners. It has good pricing and setting it up within your Vultr account is quite simple. They also do not charge anything extra per month, except for the instance price. They do not show their network speed performance, but based on user experience it is more than enough, and probably is around 1 Gigabit. Relevant offers: High frequency compute instances: 128 GB SSD, 2 vCPU, 4GB RAM and 3TB monthly bandwidth – PRICE: 24 USD 256 GB SSD, 3 vCPU, 8GB RAM and 4TB monthly bandwidth – PRICE: 48 USD Compute instances: 160 GB SSD, 4 vCPU, 8GB RAM and 4TB monthly bandwidth – PRICE 40 USD 320 GB SSD, 6 vCPU, 16GB RAM and 5TB monthly bandwidth – PRICE 80 USD

By comparison, performance and benchmark testing, the high frequency compute instances are of course better and this recommended. More info here: [https://www.vpsbenchmarks.com/posts/vultr\_high\_frequency\_compute\_instances](https://www.vpsbenchmarks.com/posts/vultr_high_frequency_compute_instances) Relevant links: [https://www.vultr.com/products/cloud-compute/\#pricing](https://www.vultr.com/products/cloud-compute/#pricing) [https://www.vultr.com/products/high-frequency-compute/\#pricing](https://www.vultr.com/products/high-frequency-compute/#pricing) [https://www.vultr.com/news/Get-Paid-by-Referring-Customers/](https://www.vultr.com/news/Get-Paid-by-Referring-Customers/) \(Vultr has a referral program if you bring them new customers\) promo code GOVULTR that gives you 10 USD of free credit for the first month 

Payment options: Credit card, Bitcoin, PayPal, Alipay, WeChat pay 

Setup: Instant

**Hetzner**

Hetzner is one of the latest popular options amongst node runners. Their prices are great and their service is stable. They also do not show the network speed performance, but based on user experience they are fast enough, and most probably up to 1 Gigabit. Relevant offers: CX41: 160 GB SSD, 4 vCPU, 16GB RAM and 20TB monthly bandwidth – PRICE 19,4 EUR CX51: 250 GB SSD, 8 vCPU, 32GB RAM and 20TB monthly bandwidth – PRICE 36,48 EUR 

Website: [https://www.hetzner.com/cloud](https://www.hetzner.com/cloud) 

Payment options: Credit card, PayPal, wire transfer 

Setup: Instant

**Contabo** 

Contabo is one of the newest possibilities amongst node runners, although the service provider itself is quite established already. They pricing is great, albeit not much tested yet within the node runners. Their web interface is a bit more simplified and doesnt provide all the extra tools that some others do, but for these prices I think its worth it. Their network speed performance varies based on the instance type you choose. Relevant offers: VPS S SSD: 200 GB SSD, 4 vCPU, 8GB RAM and unlimited bandwidth, speed: 200 Mbit – PRICE 4,99 EUR VPS M SSD: 400 GB SSD, 6 vCPU, 16GB RAM and unlimited bandwidth, speed: 400 Mbit – PRICE 8,99 EUR VPS L SSD: 800 GB SSD, 8 vCPU, 30GB RAM and unlimited bandwidth, speed: 600 Mbit – PRICE 14,99 EUR VPS XL SSD: 1600 GB SSD, 10 vCPU, 60GB RAM and unlimited bandwidth, speed: 1000 Mbit – PRICE 26,99 EUR Important note: Contabo is charging a low one time setup fee for each of your instances, you can find more info about exact prices in the link below. 

Website: [https://contabo.com/?show=vps](https://contabo.com/?show=vps) 

Payment options: PayPal, wire transfer 

Setup: After first payment is received

**Linode** 

Linode is an established provider with competitive pricing and very good stability. They do show network speeds based on the instance type you choose, but they are all satisfactory. Relevant offers: 160 GB SSD, 4 vCPU, 8GB RAM and 5TB monthly bandwidth, network speed: in 40 Gbps, out 5000 Mbps – PRICE 40 USD 320 GB SSD, 6 vCPU, 16GB RAM and 8TB monthly bandwidth, network speed: in 40 Gbps, out 6000 Mbps – PRICE 80 USD

Website: [https://www.linode.com/pricing/](https://www.linode.com/pricing/) 

Payment options: Credit card, PayPal 

Setup: Instant

**Scaleaway** 

Scaleaway is a newer provider to me, but it does offer their services for quite some time already. They offer various options within your account and their network speed performances are good. Relevant offers: DEV1-XL: 120 GB SSD, 4 vCPU, 12GB RAM and unlimited bandwidth, speed: 500 Mbit – PRICE 23,99 EUR GP1-XS: 150 GB SSD, 4 vCPU, 16GB RAM and unlimited bandwidth, speed: 500 Mbit – PRICE 39,99 EUR GP1-S: 300 GB SSD, 8 vCPU, 32GB RAM and unlimited bandwidth, speed: 800 Mbit – PRICE 79 EUR

 Website: [https://www.scaleway.com/en/pricing/](https://www.scaleway.com/en/pricing/) 

Payment options: Credit card, SEPA direct debit 

Setup: Instant

**Digital Ocean** 

Digital Ocean is another seasoned provider with good reputation and stability. They do not disclose their network speed performance, however based on user experience from node runners, it is satisfactory. Relevant offers: 160 GB SSD, 4 vCPU, 8GB RAM and 5TB monthly bandwidth – PRICE 40 USD 320 GB SSD, 6 vCPU, 16GB RAM and 6TB monthly bandwidth – PRICE 80 USD 

Website: [https://www.digitalocean.com/pricing/\#Compute](https://www.digitalocean.com/pricing/#Compute) 

Payment options: Credit card, PayPal 

Setup: Instant

**Microsoft Azure** 

Azure offers a similar service as Amazon, with RI instances which are up to 70% cheaper than on demand instance. However their pricing tiers are even more expensive than Amazon, so I will not go into details about this provider. Relevant links: [https://azure.microsoft.com/en-us/pricing/details/virtual-machines/linux/](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/linux/)

**Google Cloud Platform \(GCP\)**

Google has also similar offers to Amazon and Azure, but it seems to be even more expensive. They charge a lot for data transfer as far as I heard from the node runners. The only bonus they have is the 300 USD free credits for new signups, which can be used within 1 year. 

Website: [https://cloud.google.com/compute/all-pricing](https://cloud.google.com/compute/all-pricing)

**Final Thoughts** 

There are a few clear front runners in these cloud providers, however I would advise diversity here, as it will make the network stronger and more secure. If you run more than one node, I would also recommend different cloud providers for them. For example I currently use Vultr and Hetzner. Once EPoS is live I might try some other providers too. As a side note, most of these cloud providers also offer additional block storage, with which you can extend the disk space on your instance in order to keep pace with the blockchain size. However, except for the Amazon service, I would not recommend extending disk space as it usually brings your performance down and lowers your overall IOPS \([https://en.wikipedia.org/wiki/IOPS](https://en.wikipedia.org/wiki/IOPS)\).

