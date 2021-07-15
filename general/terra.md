---
description: Using Terra <-> Harmony Bridge
---

# Bridge Terra UST

## Assumptions

1\) Terra station wallet is installed on your mobile [https://chrome.google.com/webstore/detail/terra-station/aiifbnbfobpmeekipheeijimdpnlpgpp?hl=en](https://chrome.google.com/webstore/detail/terra-station/aiifbnbfobpmeekipheeijimdpnlpgpp?hl=en) , configured and has required UST. Alternatively, you can use the Terrastation Desktop wallet to interact with Terra network. 

2\) Metamask is installed and configured with Harmony network + wallet.

3\) This guide will explain how to bridge UST from Terra to Harmony using Mobile Terrastation wallet. We will also demonstrate bridging of 1UST from Harmony to Terra using Metamask \(Desktop\).

4\) Please ensure you have sufficient UST to pay for Bridge transaction fees. \(e.g. UST tx fees from Terra to Harmony as of 2021-07-12\)

## Bridging UST from Terra to Harmony

Step 1: Navigate to [https://bridge.terra.money/](https://bridge.terra.money/) in your browser. 

![Click Connect](../.gitbook/assets/image%20%28103%29.png)

![Click Terra Station Mobile](../.gitbook/assets/image%20%28111%29.png)

![Click Allow when prompted](../.gitbook/assets/image%20%2898%29.png)

![The app will connect to the Wallet. ](../.gitbook/assets/image%20%28168%29.png)

Go back to the Terra Bridge browser window.

Make sure that the Wallet shows as connected, select Terra as source, Harmony as destination, Asset as UST, enter the amount \(Note: Amount must be greater than 1 UST\) and the Desination Harmony Wallet in 0x format. 

![](../.gitbook/assets/image%20%28174%29.png)

Review the Fees and Click Next

App will display Gas Fees + Shuttle Fee \(Bridge Fee\) and the actual amount you will receive at destination. For example, in this case for the 2 UST we entered, 1 UST is used as shuttle fee and 1 UST will be available in Harmony destination address

![Review Fees and Click Next](../.gitbook/assets/image%20%28153%29.png)

![Review and Confirm](../.gitbook/assets/image%20%28172%29.png)

The App will then open up your Terra station wallet and prompt you to sign the transaction. Note that the MEMO field will display the destination Harmony wallet address 

![](../.gitbook/assets/image%20%28107%29.png)

Depending on your Terra station wallet setup, you will be either prompted to enter the password or use your biometric scan to sign the transaction

Once you sign the transaction, you will see a success screen.

![Click Continue](../.gitbook/assets/image%20%28167%29.png)

You can inspect the Terra Bridge transaction, by clicking on the arrow icon

![To inspect the bridge transaction, click the arrow icon](../.gitbook/assets/image%20%28136%29.png)

You will see the transaction details + the amount that was transferred to the bridge \(including the fees of 1 UST\) displayed in UST 

![](../.gitbook/assets/image%20%28149%29.png)

Open up Metamask and add the Wrapped-UST Token address \(Harmony's wrapped version of Terra UST\)

Click Add Tokens and Type 0x224e64ec1bdce3870a6a6c777edd450454068fec

![](../.gitbook/assets/image%20%28143%29.png)

![](../.gitbook/assets/image%20%28117%29.png)

You should be able to see your 1UST balance

![](../.gitbook/assets/image%20%28157%29.png)

## Bridging UST from Harmony to Terra

Open up the browser and navigate to Harmony Terra bridge URL

Select Source as "Harmony". App will prompt you to connect. Select "Metamask"

![](../.gitbook/assets/image%20%28151%29.png)



Make sure metamask source wallet has ONE tokens to pay for gas fees, required UST to be bridged to Terra, Enter the amount and destination address, click Next

![](../.gitbook/assets/image%20%28101%29.png)

Review details, click confirm

![](../.gitbook/assets/image%20%28160%29.png)

Click confirm in the metamask pop-up window to approve the bridge transaction.

![](../.gitbook/assets/image%20%28118%29.png)

You should see a "Complete" message when the bridge transaction is completed. Additionally, you can click on the Transaction hash to verify.



![](../.gitbook/assets/image%20%28170%29.png)



At this point, you should have received UST back in your Terra wallet.

## FAQs

* **What is the contract address of 1UST token bridged using terra&lt;&gt;harmony bridge?**

  * [https://explorer.harmony.one/address/0x224e64ec1bdce3870a6a6c777edd450454068fec](https://explorer.harmony.one/address/0x224e64ec1bdce3870a6a6c777edd450454068fec)

* **Can I bridge UST from Ethereum or BSC using Horizon bridge \(https://bridge.harmony.one\) to obtain 1UST from** [**https://explorer.harmony.one/address/0x224e64ec1bdce3870a6a6c777edd450454068fec**](https://explorer.harmony.one/address/0x224e64ec1bdce3870a6a6c777edd450454068fec) **contract?**
  * No. The horizon bridge issues different UST tokens when bridged from Ethereum and BSC and it is not same the UST bridged using native terra&lt;&gt;harmony bridge. 
    * The 1UST token address for UST bridged from Ethereum: [https://explorer.harmony.one/address/0x2BfA122427085E0D1993CCcf1F74A4C915908F7B](https://explorer.harmony.one/address/0x2BfA122427085E0D1993CCcf1F74A4C915908F7B)
    * The 1UST token address for UST bridged from BSC:

      * [https://explorer.harmony.one/address/0xb82307fF75F0CD2cFc253BA2621851fd9123a818](https://explorer.harmony.one/address/0xb82307fF75F0CD2cFc253BA2621851fd9123a818)
* **Which 1UST is used in DEXs like Viper and Sushi for farming?**
  * It is the 1UST bridged using native terra&lt;&gt;harmony bridge with address: [https://explorer.harmony.one/address/0x224e64ec1bdce3870a6a6c777edd450454068fec](https://explorer.harmony.one/address/0x224e64ec1bdce3870a6a6c777edd450454068fec)

