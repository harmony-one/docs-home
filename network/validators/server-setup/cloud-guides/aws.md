---
description: 'To launch your AWS instance, follow the steps below.'
---

# AWS

## Step 1: Launching your AWS Node <a id="step-1-launching-your-aws-node"></a>

**1.** If you don’t already have an AWS account, register one at [https://aws.amazon.com](https://aws.amazon.com/).

**2.** Once you have set up and logged into your AWS account, click on the top left bar “Services -&gt; Compute -&gt; EC2".

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M-SpPev7Rx3tI5_8vit%2F-M-SvY1PztdgOcjd96xZ%2Fassets_-LlDqlxK8e45wuh1WH4h_-LlEvL4ccZjjcXwS1WWY_-LlEoh9qALwq7NrZTaQH_assets%252F-LiQYKCcGux_Ib7Gddno%252F-Lj2HFbsGU29d_abCLle%252F-Lj2HGc3Atm_1mokTWXl%252FAWS-step3%20%281%29.png?alt=media&token=2ab52e1b-9c94-4ae3-bf28-738cbeb9a917)

**3.** Click on the blue button “Launch Instance".

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M-SpPev7Rx3tI5_8vit%2F-M-Sv_xB0oo1-kzPVcC6%2Fassets_-LlDqlxK8e45wuh1WH4h_-LlEvL4ccZjjcXwS1WWY_-LlEoorXG-dkasj2ahJd_assets%252F-LiQYKCcGux_Ib7Gddno%252F-Lj2HFbsGU29d_abCLle%252F-Lj2HGc5NkR0XElzEk6I%252FAWS-step4.png?alt=media&token=29eea808-5ec5-4a38-b483-8d22c1941c76)

**4.** Select “Amazon Linux 2 AMI \(HVM\), SSD Volume Type”.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M18EnlHhxfs4IlN_Xhi%2F-M18Eym_BjlKXaPChBdj%2Fassets_-LlDqlxK8e45wuh1WH4h_-LlEvL4ccZjjcXwS1WWY_-LlEoyu2o6s4Sjkvm34W_assets%252F-LiQYKCcGux_Ib7Gddno%252F-Lj2HFbsGU29d_abCLle%252F-Lj2HGc7aUnyzpkZdHd7%252FAWS-step5.png?alt=media&token=d89a9daf-e89c-4472-97ff-c2890379be82)

**5.** Choose instance type “m5a.xlarge” or “m5.xlarge“.

**6.** Click “Next: Configure Instance Details” at the bottom right corner of the page.

**7.** Don't change anything. Click “Next: Add Storage” at the bottom right corner of the page.

**8.** Change the “Size \(GiB\)” accordingly to the [minimum storage requirements](https://docs.harmony.one/home/validators/cloud-setup/minimum-requirements).

**9.** Click “Next: Add Tags".

**10.** Click "Add Tag." Then, in the “Key” input box put “Name” in “Value” put “Pangaea-key”.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M-SpPev7Rx3tI5_8vit%2F-M-SvyBAYVDNioAq1d8n%2Fassets_-LlDqlxK8e45wuh1WH4h_-LlEvL4ccZjjcXwS1WWY_-LlEqF6sFapEJt6e_ruU_Capture.png?alt=media&token=c2319a18-312e-447a-814f-9d204183a32e)

**11.** Click “Next: Configure Security Group”.

**12.** On the default SSH with port 22, change the “Source” option to “Anywhere”.

**13.** Click "Add Rule". Under "Type" select "Custom TCP Rule", under "Port Range" put "6000" and under "Source" select "Anywhere".

**14.** Click "Add Rule" again. This time, under "Type" select "Custom TCP Rule", under "Port Range" put "9000" and under "Source" select "Anywhere".

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M-SpPev7Rx3tI5_8vit%2F-M-Sw01Yoy6KQN9QE9PX%2Fassets_-LlDqlxK8e45wuh1WH4h_-Lw56FxOeYv0YR4puCg__-Lw56P4Wvhdd5sBaWFho_security_groups_aws.jpg?alt=media&token=f3004e29-8898-4d6f-8654-37de5d847936)

**15.** Click “Review and Launch” and then click "Launch". \(Note: Ignore warnings such as “your security group is open to the world” or “your instance configuration is not eligible for free tier”\)

**16.** In the pop-up window you will need to create a new key pair. Select “Create a new key pair” and then enter a name that you like, for example “Pangaea-key”.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M-SpPev7Rx3tI5_8vit%2F-M-Sw3fLntQmXXvy3JHd%2Fassets_-LlDqlxK8e45wuh1WH4h_-LlEvL4ccZjjcXwS1WWY_-LlEqxD-n79Fd0kkMCF3_Capture.png?alt=media&token=673b6e2c-f70a-4a36-8485-751f3becad99)

**17.** Click “Download Key Pair” and save the key file somewhere you'll remember.

**18.** Click “Launch Instances”.

**19.** Click “View Instances” at the bottom right. Your new instance should be initializing. Wait a few moments for it to get started.

**21.** Congratulations your instance is up and running! Now it's time to connect to your instance.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M18Fj8DCAY2KtBma_zp%2F-M18G50wfliuTSWxfFPs%2Fassets_-LlDqlxK8e45wuh1WH4h_-LlEvL4ccZjjcXwS1WWY_-LlErACMN7pbdPNpbeia_assets%252F-LiQYKCcGux_Ib7Gddno%252F-Lj2HFbsGU29d_abCLle%252F-Lj2HGcJYpniB9O_xpMo%252FAWS-step21.png?alt=media&token=cbd9a6fb-c7dd-43db-83cd-bfc8026058a8)

## Step 2: Connecting to your AWS Instance <a id="step-2-connecting-to-your-aws-instance"></a>

**1.** Open a Terminal window on your computer.

 **For Mac:** If you can’t find Terminal, use spotlight to search for it. Or go to your "Applications' folder, and it should be inside of “Utilities”.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M-SpPev7Rx3tI5_8vit%2F-M-SwDSVomei_wm8RgU8%2Fassets_-LlDqlxK8e45wuh1WH4h_-LlEvL4ccZjjcXwS1WWY_-LlErPyudVu-nb4ZLB4D_assets%252F-LiQYKCcGux_Ib7Gddno%252F-Lj2HFbsGU29d_abCLle%252F-Lj2HGcLt-ekXY8UUO4g%252Fkey-step1.png?alt=media&token=04abdbb4-bec6-4c09-94ae-b9aca707139d)

**For Windows:** Download PuTTY to allow your computer to SSH into the AWS instance. For instructions on connecting to an EC2 instance using Putty follow [these instructions](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/step-2-connect-to-instance.html) from Amazon.

**2.** Once Terminal is open, use the `cd` command to change your directory to where the key pair file \(Pangaea-key.pem\) that you generated is. Hint it may be in your “Downloads” folder.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M-SpPev7Rx3tI5_8vit%2F-M-SwIfjL7K3O36MS2Lc%2Fassets_-LlDqlxK8e45wuh1WH4h_-LlYZ1j_-40H7bnDrwxD_-LlYgjVgJIwE8kk2L6wF_AWSCDDOWNLAODS.png?alt=media&token=3d58106e-1758-46e7-835e-45efc1a8f6de)

**3.** Enter the command `chmod 400 Pangaea-key.pem`. This command makes your key not publicly viewable.

**Note:** On Mac, your pem file may have been changed to a .txt file so the correct command on Mac would be: `chmod 400 Pangaea-key.pem.txt`

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M1ZJQFhdhIexbw67x-l%2F-M1ZUv7XgOzmLxxNLMUq%2Fimage.png?alt=media&token=ffbf732d-b408-47ce-9179-9d5ac19a22d2)

**4.** Go back to your AWS window where you are viewing your instances. Select your new "Pangaea-key" instance and click “Connect” on the top bar.

**5.** In the pop-up window, under the “Example:” header, copy the sample command to connect to your ec2 instance. The command will look something like:

```text
ssh -i "pangaea-key.pem" ec2-user@ec2-13-250-30-215.ap-southeast-1.compute.amazonaws.com
```

Now connect to your instance by running the sample command you copied from the “Connect” page in your terminal window.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M1ZJQFhdhIexbw67x-l%2F-M1ZVNJoWUwvEOWQ5xFq%2Fimage.png?alt=media&token=b998d9af-6344-48bd-ae7f-1523787b30c4)

It may ask you whether or not you want to continue connecting. Type in “yes” and hit enter.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT_3k%2F-M-SpPev7Rx3tI5_8vit%2F-M-SwU2UBsT7Dov4WsF6%2Fassets_-LlDqlxK8e45wuh1WH4h_-LlYZ1j_-40H7bnDrwxD_-LlYiEuvvkCZfCrmaujP_AWSpangaeaConnected.png?alt=media&token=0b089e53-81bf-49b0-acc3-7ea47f5e9f55)

Congratulations! You should be logged into your new AWS instance!

## Step 3: Installing Required Packages

 ****Run the following command to make sure your instance is properly updated:

```bash
sudo yum update
```

When prompted whether or not you want to download packages, enter "y" for yes.

