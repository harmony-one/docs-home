# Vultr

To launch your Vultr instance, we will go through 2 steps.

**Step 1: Launching Your Vultr Node**

* Registering Vultr and choosing the correct instance.

**Step 2: Connecting to your Vultr Node**

* Connecting to your Vultr instance.

## **Step 1: Launching Your Vultr Instance** <a id="step-1-launching-your-vultr-instance"></a>

### Logging into Vultr <a id="logging-into-vultr"></a>

​[Vultr Main Page](https://www.vultr.com/) If you don’t already have an Vultr account, register one by clicking on "Sign up". Otherwise, log into your Vultr Account by clicking on "Sign in".

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmN5L0MtjVtbA_GYd6S%2F-LmN5N4DxS6VF1s2zswY%2Fbrave_5ABtBQkPcT.png?alt=media&token=ba1288f4-0c76-48ea-bf39-68109f2d2b64)

### Create a new instance <a id="create-a-new-instance"></a>

Once logged in, you'll want to add a new instance. Depending on whether your account is new or not, you may or may not have a Products page.

* If you already have an instance, click the "+" button to deploy a new server. You can also use this [link](https://my.vultr.com/deploy/) to go to the deploy page.
* Otherwise, your Products page will be already link you to the Deploy page.

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmLNRdAg8YfuFxXiQq0%2F-LmM3X7d52fBZllcOPFd%2Fbrave_ijOE8hiNrv.png?alt=media&token=aca0bd2c-20ac-4169-ac10-63adf2a9bae4)

### Choose Instance Type <a id="choose-instance-type"></a>

For Pangaea requirements, two instance types would fit: Cloud Compute and High Frequency. Cloud Compute is recommended for Pangaea.

* **Cloud Compute instances** also work properly with 2 CPUs, 4 GB RAM with 80 GB SSDs.
* **High Frequency Instances** were recently introduced by Vultr and offer latest generation high performance 3GHz+ CPUs and NVMe SSDs.

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LlJ1k4k3MsK7srbkEEP%2F-LlJ4bAtQ7yHCVwEtO5d%2Fimage.png?alt=media&token=e05f2088-96f4-4e5d-9d8f-bb834f7d7857)

### Select Server Location and Server Type <a id="select-server-location-and-server-type"></a>

Choose now your desired server type. We recommend either the latest **LTS version of Ubuntu** \(18.04 as of date of now\) or the latest version of **Debian**.

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LlxvSktdLiGcUCOJpxp%2F-Lly3uMNT60Id55f1x7K%2Fbrave_qvMA6y4YCr.png?alt=media&token=bc26c01f-1a11-49bd-8fe5-638f46feee6a)

### Choose Server Size <a id="choose-server-size"></a>

Harmony recommends one of the two following:

**Cloud Compute**

* 2 CPU, 4 GB RAM, 80 GB SSD

**High Frequency**

* 2 CPU, 4 GB RAM, 128 GB NVMe SSD

For "Additional Features", none of the selections are necessary.

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LlxvSktdLiGcUCOJpxp%2F-LlxzVtdrbyY8vr6IsO8%2Fbrave_jSr54JprOg.png?alt=media&token=99b042ec-7a94-4508-b130-cda76553a737)

### Setting Server Name <a id="setting-server-name"></a>

You can now set the name of your server, e.g. PangaeaNode Then you should click "Deploy Now".

![](https://blobs.gitbook.com/assets%2F-LlDqlxK8e45wuh1WH4h%2F-LmLNRdAg8YfuFxXiQq0%2F-LmLOsTYFmwEN458cYNp%2FGsdkLBmR24.png?alt=media&token=0b2e774c-5132-4fbc-ba50-d2359830a844)

At this point you should be back on the Products page and your server should be installing. However, the setup isn't completely done, as you need to still create a firewall.

### Firewall Setup <a id="firewall-setup"></a>

As we want to allow other nodes to connect to yours, we have to open the correct ports.

Once you are on the [Firewall page](https://my.vultr.com/firewall/), click Add Firewall Group.

![](../../../.gitbook/assets/firewall_group.png)

Enter a name for the firewall group, e.g. FoundationNode.

#### Open the following 3 ports to the public \("Anywhere" on inbound\). <a id="open-the-following-5-ports-to-the-public-anywhere-on-inbound"></a>

* TCP 22 \(SSH\)
* TCP 6000
* TCP 9000

Make sure to check that 3 Group Rules have been set.

![](../../../.gitbook/assets/rules_vultr_firewall.jpg)

#### Then link the instance to the firewall group. The steps are as follows: <a id="then-link-the-instance-to-the-firewall-group-the-steps-are-as-follows"></a>

1. Click Linked Instances.
2. Make sure your new server is selected.
3. Click the + button.
4. Click Add Linked Instance.

![](../../../.gitbook/assets/manage_firewall_group.jpg)

Your instance should now be added to the firewall group and the number of linked instances should increment by 1.

![](../../../.gitbook/assets/vultr_linked_instances.jpg)

You can now go back to the Products page and your server is now successfully set up!

![](../../../.gitbook/assets/products_page.png)

## **Step 2: Connecting to your Vultr Node** <a id="step-2-connecting-to-your-vultr-node"></a>

{% embed url="https://youtu.be/rtniAY1RUiM" %}

**Connect to your Vultr Instance by using Git Bash.**

If you do not have gitbash installed. Please visit this [link to install](https://gitforwindows.org/). Everything can be default selection when you are installing.

In your Vultr instance console overview. You will see your instance information. To go into your instance from git bash. We will use the command:

```text
ssh root@<INSTANCEIPADDRESS>
```

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M1ZJQFhdhIexbw67x-l%2F-M1ZP-2I7upBywwunoi8%2Fimage.png?alt=media&token=76a43985-cbcb-470e-989b-7d6fe5eb65c3)

It will the prompt you for a password. The password is unique to each instance. To find your password. Look at the Vultr Console website. There is a unique password that is associated with your instance. Copy and paste that in.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M1ZJQFhdhIexbw67x-l%2F-M1ZP5alORLnXftHH2V-%2Fimage.png?alt=media&token=2aaa5b5b-297c-4d93-923e-7298086035be)

Before anything, it is recommended to update your system:

```bash
sudo apt update && apt upgrade
```

Now install the following packages that will be needed to run Harmony by typing:

```bash
sudo apt-get install dnsutils && sudo apt-get install tmux
```

You will be asked to confirm if you would like to download and install these packages. Just press Y to confirm.



