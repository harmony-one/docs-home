---
description: To launch your Digital Ocean instance, follow the steps below.
---

# Digital Ocean

{% hint style="success" %}
For new users, you can get $100 dollars free credits to run Digital Ocean services for 2 months using the link bellow
{% endhint %}

## Step 1: Launching your Digital Ocean Node <a href="#step-1-launching-your-aws-node" id="step-1-launching-your-aws-node"></a>

### Logging into **Digital Ocean** <a href="#logging-into-vultr" id="logging-into-vultr"></a>

[​](https://www.digitalocean.com/)Click [here](https://try.digitalocean.com/performance/) to register a new Digital Ocean account or login if you have an existing one.

### Create a new P**roject** <a href="#create-a-new-instance" id="create-a-new-instance"></a>

Once you have set up and logged into your Digital Ocean account, click on the top left bar “Projects -> New Project". Enter the desired project name and click on "Create Project" as shown by the image below:

![](<../../../../.gitbook/assets/DO1 (2).png>)

### Create a new Droplet <a href="#create-a-new-instance" id="create-a-new-instance"></a>

On the top right corner click on "Create"->"Droplets".

![](<../../../../.gitbook/assets/DO2 (1).png>)

Choose now your desired Linux image. We recommend the latest **LTS version of Ubuntu** (18.04 as of date of now). Use the left and right arrows to navigate between the different plans available. Choose the "Standard" plan and then select a virtual machine with at least 4 CPUs, 4GB of RAM and 80GB SSD accordingly to the [minimum requirements](https://docs.harmony.one/home/validators/cloud-setup/minimum-requirements).

![](<../../../../.gitbook/assets/DO3.1 (1).png>)

You can select the datacenter region of your choice here. We chose "Frankurt" in our example. We recommend using the "SSH Keys" as your authentication method (more secure) instead of the "One-time password" method. A button with the name "New SSH key" will appear on screen, just click on it.

![](<../../../../.gitbook/assets/DO3.2 (1).png>)

To create your SSH key click [here](https://www.digitalocean.com/docs/droplets/how-to/add-ssh-keys/) for instructions.

When you generated your public SSH key, give it a name and click on button "Add SSH key" as shown by the image below. In case you don't have a public SSH key yet, just follow the instructions to create it.

![](<../../../../.gitbook/assets/DO3.3 (1).png>)

Choose a custom hostname if you want and then click on "Create Droplet".

### Firewall Setup <a href="#firewall-setup" id="firewall-setup"></a>

Wait a few seconds till your droplet is created and then click on "Networking" on the left bar.

![](<../../../../.gitbook/assets/DO4 (1).png>)

Click on "Firewall" and then on "Create Firewall".

![](<../../../../.gitbook/assets/DO5 (1).png>)

In the Inbound Rules section, click on "New rule" and select "Custom". Leave the protocol as **TCP** and fill the port range field with **6000**. Repeat the same procedure for port **9000**. You will be left with 2 inbound rules as shown by the image below.

![](<../../../../.gitbook/assets/DO5.1 (1).png>)

In the Outbound Rules section leave it as it is. Type the name of the droplet you want to apply your firewall rules (the droplet name is the same as your hostname you chose previously).Click now on "Create Firewall".

![](<../../../../.gitbook/assets/DO5.2 (1).png>)

## **Step 2: Connecting via SSH to your Instance** <a href="#step-2-connecting-to-your-vultr-node" id="step-2-connecting-to-your-vultr-node"></a>

To connect via SSH to your Digital Ocean instance, please follow the instructions [here](https://www.digitalocean.com/docs/droplets/how-to/connect-with-ssh/).

## Step 3: Update / upgrade your VPS

Before anything, it is recommended to update your system:

```bash
sudo apt update && apt upgrade
```

You will be asked to confirm if you would like to download and install these packages. Just press Y to confirm.
