---
description: 'To launch your Google Cloud instance, follow the steps below.'
---

# Google Cloud

{% hint style="success" %}
Google Cloud has a free tier for new users. You get $300 to spend on Google Cloud Platform products during your first 12 months
{% endhint %}

## Step 1: Launching your Google Cloud Instance <a id="step-1-launching-your-google-cloud-instance"></a>

Go to [https://cloud.google.com/free](https://cloud.google.com/free) and click on “Get Started for Free”. Login using an existing account or create a new one.

After you login and validate your credit card, you will be shown a page pretty much like this one. Click on “Compute Engine” and then in “VM Instances”.

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmBR5kBgg9922w3-lIM%2F-LmBT2iqRO2RGMmA24sS%2FFirstPick.PNG?alt=media&token=d9ada2c6-c774-4242-90d2-2248c442df53)

Click on the Create button to make a new instance

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmBR5kBgg9922w3-lIM%2F-LmBTANylI3L_EIZWgOd%2FVMcomputeCreate.PNG?alt=media&token=f101dbf5-f667-4b5d-8082-bf964fe9bbf4)

We recommend to name it something like "pangaea” \(the instance name cannot be changed\). Select the Machine type as “Custom” and set up 2 vCPU’s and 4GB of Memory.

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmBR5kBgg9922w3-lIM%2F-LmBgeT41L-Y04ge1Nq6%2Fvminstancesetup.PNG?alt=media&token=7c89277f-eb66-429b-b8e9-06749e983f73)

Keep everything default after you have configured the cores and memory. For storage, 80GB is perfectly fine for now.

For the Boot Disk, we recommend either the latest **LTS version of Ubuntu** \(18.04 as of date of now\) or the latest version of **Debian**.

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmBR5kBgg9922w3-lIM%2F-LmBhv4-FTM_WdWJGxhY%2Fcreateinstance.PNG?alt=media&token=54639c2e-217d-41d1-8885-469919855bf4)

Click Create. Please wait a few minutes for your instance

Once the instance is created. We will open 4 ingoing ports. To do this click on "nic0" as shown below. In the next page click on “Firewall rules” and after that on “CREATE FIREWALL RULE”.

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmBR5kBgg9922w3-lIM%2F-LmBrlMhlGYf8n0LGdnx%2Ffirewallrules.PNG?alt=media&token=fd23e135-940f-4a6c-a248-3c566af62823)

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmBR5kBgg9922w3-lIM%2F-LmBqtVY0Ssje29ti6uJ%2Fnic0.PNG?alt=media&token=ff2d6589-8f48-4b00-b312-98facb324887)

* TCP 6000
* TCP 9000

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LvzuQOmNvRXBWd1suxY%2F-LvzvhQqA76BwNmSY3AT%2Fports.jpg?alt=media&token=160965b3-2b20-4a80-98f5-fc76f7da070d)

## **Step 2: Connecting via SSH to your Instance** <a id="step-2-connecting-to-your-google-cloud-instance-and-copying-keys"></a>

Go back to the VM instances page and click on SSH. This will open a new window and connect via SSH to your instance:

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmBR5kBgg9922w3-lIM%2F-LmBv5tDs9HYgcS64Ppa%2Fssh.PNG?alt=media&token=d6162ff5-f5be-403b-8cde-78fe4585354b)

## Step 3: Installing Required Packages

Before anything, it is recommended to update your system:

```bash
sudo apt update && apt upgrade
```

Now install the following packages that will be needed to run Harmony by typing:

```bash
sudo apt install dnsutils && sudo apt install tmux
```

You will be asked to confirm if you would like to download and install these packages. Just press Y to confirm.

