# Choosing A Cloud Provider

Which cloud provider to choose for your Harmony node?

We've put together a list of possible cloud providers and some examples of their instances that can be used. Note that I used recommended settings such as 4 GB RAM and at least 2vCPU. Although you can probably run away with a 2 GB RAM instance, it is not recommended, as the performance might be lesser and so will the rewards. All prices displayed are based on a monthly basis. Important note: currently the blockchain size for non shard 0 nodes is around 100GB \(because they have to sync their own shard and also shard 0, which is called beacon chain\). Shard 0 nodes blockchain size is around 50GB at the moment. This is at the time of writing. We can expect this to grow larger until the Harmony team introduces state pruning which should significantly lower the size.

Since we are about to see EPoS go live on Harmony network, I decided to put together a list of possible cloud providers and some examples of their instances that can be used. 

TLDR:

CPU we recommend 2 core, 2G ram for running single BLS key; 2 core, 4G ram for running up to 4 BLS keys. Bandwidth better be 100M or better for downlink, uplink 10M or better. Although you can probably run away with a lower instance, it is not recommended, as the performance might be impacted and so are the rewards\(slashing risk due to unavailability\). In case of computer crash or power outage, you need backup or UPS. Currently the blockchain size is around 30GB. 

Based on the different cloud service you choose, machine cost can vary from a few dollars \(digital ocean\) to 29 dollar fixed price per month \(Ankr\). All prices displayed are based on a monthly basis.

[AWS \(Amazon Web Services\)](https://aws.amazon.com/ec2/?nc2=h_ql_prod_fs_ec2):

Amazon offers powerful networking options and a large array of hardware specs. They offer speeds from 1 Gigabit and up to 100 Gigabit. Their T instances are burst instances, which means they are capable of high performance for a while only. After that, if the instance is still stretched you might get charged extra. They offer 3 kinds of instance purchases:

* On-demand instance: this one is self-explanatory, you pick an instance you wish to run, set it up and launch it. This is the default option.
* Spot instance: A Spot Instance is an unused EC2 instance that is available for less than the On-Demand price. Because Spot Instances enable you to request unused EC2 instances at steep discounts, you can lower your Amazon EC2 costs significantly. The hourly price for a Spot Instance is called a Spot price. Note that although you save some money compared to on-demand instances, there is a high chance the EC2 service will take them back when they need the extra capacity, or you might even have to pay more.
* Reserved instance \(RI\): this type allows you to reserve an instance type for a period in advance, for which you receive a significant discount. However, no matter if you still need it or not, you have to pay for it as long as the reserved period lasts \(usually 1 year\).

Here is the link for an explanation of the burst instances:[  ](https://www.cloudhealthtech.com/blog/amazon-burstable-instances-explained)

[https://www.cloudhealthtech.com/blog/amazon-burstable-instances-explained](https://www.cloudhealthtech.com/blog/amazon-burstable-instances-explained)

IMPORTANT NOTE: Bandwidth is charged on a pay-as-you-go basis, and it is calculated on the actual bandwidth usage \(GB\) in your last month multiplied by AWS bandwidth charges \($0.12/GB\). For example, if your server consumed 100GB bandwidth in a month, you will be charged for $12 \(100GB x $0.12\). Only the first 1GB is free, everything else is payable on top of the instance cost. Currently, the data charges for a Harmony mainnet node are around 20 USD extra per month. For cost estimation also refer to  [AWS Pricing Calculator](https://calculator.aws/#/createCalculator).

Relevant offers:

* t3a.small: EBS storage, 2 vCPU, 2GB RAM –  recommended for 1-2 bls keys
* t3a.medium: EBS storage, 2 vCPU, 4GB RAM –  recommended for 4 bls keys

There are also AMD CPU versions of all of the above instances which are also good and a little bit cheaper. They are named like this: T3a.medium, M5a.large.

NOTE: if you purchase a RI version of the above instances, then you get a discount of up to 50% on your instance. It also heavily depends on the region you want to launch it. For reference, you can check this website which has a table of the information and a lot of filters:[  ](https://www.ec2instances.info/?min_memory=4&min_vcpus=2&region=us-west-2&cost_duration=monthly)

[https://www.ec2instances.info/?min\_memory=4&min\_vcpus=2&region=us-west-2&cost\_duration=monthly](https://www.ec2instances.info/?min_memory=4&min_vcpus=2&region=us-west-2&cost_duration=monthly)

Payment options: Credit card – they prefer business accounts, you will have a lot less problems and less questions about what you are using them for.

Setup: instantly

[Digital Ocean](https://www.digitalocean.com/products/droplets/?_campaign=DO_Dev_Awareness_BA_Search_B_GENERIC&_adgroup=&_keyword=digitalocean&_device=c&_copytype=nonbiz_ad&_adposition=&_medium=brand_sem&_source=bing&msclkid=7557b0b28d151775d0e6ee3916eadc75&utm_source=bing&utm_medium=cpc&utm_campaign=DO_Dev_Awareness_BA_Search_B_GENERIC&utm_term=digitalocean&utm_content=GENERIC_DO):

Digital Ocean is another seasoned provider with a good reputation and stability. They do not disclose their network speed performance, however, based on user experience from node runners, it is satisfactory. Digital Ocean does not charge any fee on data transfer thus is highly recommended.

Relevant offers:

* 2 GB, 2 vCPUs, 3 TB, 60 GB - $15/month
* 4 GB, 2 vCPUs, 4 TB, 80 GB -  $20/month

Payment options: credit card, Paypal

Setup: instantly  


[Ankr](https://www.ankr.com/):

Ankr has developed a one-click node deployment application for Harmony Open Staking Validator nodes,which takes a lot less manual work to set up and maintain the node. 

* 2 core, 4GB Memory, 60GB Storage, 29.00 USD per month

Ankr is now providing a 2 month free period for 200 external validators on our testnet: [Ankr provides 2 months of free hosting for Harmony Open Staking Validators](https://medium.com/ankr-network/ankr-provides-2-months-of-free-hosting-for-harmony-open-staking-validators-bb8269729966).

Payment options: credit card, PayPal

[Vultr](https://www.vultr.com/):

Vultr is another very popular option amongst Harmony node runners. It has good pricing and setting it up within your Vultr account is quite simple. They also do not charge anything extra per month, except for the instance price. They do not show their network speed performance, but based on user experience it is more than enough, and probably is around 1 Gigabit.

Relevant offers:

* High frequency compute instances:
  * 128 GB SSD, 2 vCPU, 4GB RAM and 3TB monthly bandwidth – PRICE: 24 USD
* Compute instances:
  * 80 GB SSD, 2vCPU, 4GB RAM and 3TB monthly bandwidth – PRICE: 20 USD

By comparison, performance and benchmark testing, the high frequency compute instances are of course better and this recommended. More info here: [https://www.vpsbenchmarks.com/posts/vultr\_high\_frequency\_compute\_instances](https://www.vpsbenchmarks.com/posts/vultr_high_frequency_compute_instances)

Relevant links:

* [https://www.vultr.com/products/cloud-compute/](https://www.vultr.com/products/cloud-compute/) 
* [https://www.vultr.com/news/Get-Paid-by-Referring-Customers/](https://www.vultr.com/news/Get-Paid-by-Referring-Customers/) \(Vultr has a referral program if you bring them new customers\)
* promo code GOVULTR that gives you 10 USD of free credit for the first month

Payment options: credit card, Bitcoin, Paypal, Alipay, Wechat pay

Setup: instantly  


[Hetzner](https://www.hetzner.com/cloud):

Hetzner is one of the latest popular options amongst node runners. Their prices are great and their service is stable. They also do not show the network speed performance, but based on user experience they are fast enough, and most probably up to 1 Gigabit.

Relevant offers:

* CX41: 160 GB SSD, 4 vCPU, 16GB RAM and 20TB monthly bandwidth – PRICE 19,4 EUR
* CX51: 250 GB SSD, 8 vCPU, 32GB RAM and 20TB monthly bandwidth – PRICE 36,48 EUR

Relevant links:[ https://www.hetzner.com/cloud](https://www.hetzner.com/cloud)

Payment options: credit card, Paypal, wire transfer

Setup: instantly  


[Microsoft Azure](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/linux/):

Azure offers a similar service like Amazon, with RI instances which are up to 70% cheaper than on-demand instance. However their pricing tiers are even more expensive than Amazon, so I will not go into details about this provider.

[Google Cloud Platform](https://cloud.google.com/):

Google has also similar offers to Amazon and Azure, but it seems to be even more expensive. They charge a lot for data transfer as far as I heard from the node runners. The only bonus they have is the 300 USD free credits for new signups, which can be used within 1 year. 

Google Cloud Platform Pricing Calculator: [https://cloud.google.com/products/calculator](https://cloud.google.com/products/calculator)  


[Contabo](https://contabo.com/?show=home):

Contabo is one of the newest possibilities amongst node runners, although the service provider itself is quite established already. The pricing is great, albeit not much tested yet within the node runners. Their web interface is a bit more simplified and doesn’t provide all the extra tools that some others do, but for these prices I think its worth it. Their network speed performance varies based on the instance type you choose.

Relevant offers:

* VPS S SSD: 200 GB SSD, 4 vCPU, 8GB RAM and unlimited bandwidth, speed: 200 Mbit – PRICE 4,99 EUR
* VPS M SSD: 400 GB SSD, 6 vCPU, 16GB RAM and unlimited bandwidth, speed: 400 Mbit – PRICE 8,99 EUR
* VPS L SSD: 800 GB SSD, 8 vCPU, 30GB RAM and unlimited bandwidth, speed: 600 Mbit – PRICE 14,99 EUR

Important note: Contabo is charging a low one-time setup fee for each of your instances, you can find more info about exact prices in the link below.

Relevant links:[ https://contabo.com/?show=vps](https://contabo.com/?show=vps)

Payment options: Paypal and wire transfer

Setup: after the first payment is received  


[Linode](https://www.linode.com/pricing/):

Linode is an established provider with competitive pricing and very good stability. They do show network speeds based on the instance type you choose, but they are all satisfactory.

Relevant offers:

* 160 GB SSD, 2 vCPU, 4GB RAM and 4TB monthly bandwidth, network speed: in 40 Gbps, out 4000 Mbps – PRICE 20 USD

Payment options: credit card, Paypal

Setup: instantly  


[Scaleaway](https://www.scaleway.com/en/pricing/):

Scaleaway is a newer provider to me, but it does offer its services for quite some time already. They offer various options within your account and their network speed performances are good.

Relevant offers:

* DEV1-S: 120 GB SSD, 2 vCPU, 20GB RAM and 200 Mbit/s bandwidth – PRICE 2.99 EUR

Payment options: credit card, SEPA direct debit

Setup: instantly  
  


Final Notes:

There are a few clear front runners in these cloud providers, however, I would advise diversity here, as it will make the network stronger and more secure. If you run more than one node, I would also recommend different cloud providers for them. For example, I currently use Vultr and Hetzner. Once EPoS is live I might try some other providers too. 

As a side note, most of these cloud providers also offer additional block storage, with which you can extend the disk space on your instance in order to keep pace with the blockchain size. However, except for the Amazon service, I would not recommend extending disk space as it usually brings your performance down and lowers your overall IOPS \([https://en.wikipedia.org/wiki/IOPS](https://en.wikipedia.org/wiki/IOPS)\).  


