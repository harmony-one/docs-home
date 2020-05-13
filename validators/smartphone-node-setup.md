---
description: >-
  Running a Harmony validator node today got so easy and convenient wherever we
  go. Follow these steps to run a validator node thru smartphone devices.
  (Contributed by Community)
---

# Smartphone Node Setup

1. Download and Install the Termux app in the [Playstore](https://play.google.com/store/apps/details?id=com.termux&hl=en). 

![](../.gitbook/assets/screen-shot-2020-05-12-at-11.01.48-am.png)

2. Run the app and install the SSH for the program by typing:

```text
pkg install openssh
```

3. Setup your instance in the different [cloud providers](cloud-guides/).

4. Connect your instance by using the Termux app and use the following command:

```text
ssh root@<INSTANCEIPADDRESS>
```

5. Click "yes" for authentication and retype again the command to access your instance. After that, type the unique password associated with your instance that comes from your cloud provider and change it after successful logging in to protect your instance.

6. Before doing anything, update your system by using the command:

```text
sudo apt update && apt upgrade
```

7. Install the following packages that will be needed to run the Harmony:

```text
sudo apt update && apt upgrade
```

8. Download Harmony CLI to interact with your node:

{% tabs %}
{% tab title="Linux Download" %}
```text
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```
{% endtab %}
{% endtabs %}

9. Run ./hmy cookbook to see some commonly commands that will help you:

```text
./hmy --node=https://api.s0.t.hmny.io cookbook
```

10. Create a new BLS key in order to run your validating node. When generating a BLS key, the CLI will ask you to provide a passphrase to encrypt the BLS key file.‌ To generate the BLS key file type the following command:

```text
./hmy keys generate-bls-key --passphrase
```

{% hint style="info" %}
**Remember your passphrase. You will need it to decrypt the BLS key file in order to create a validator & start a node with that key. Create a backup of your BLS key file or save the BLS private key \(optional\).**
{% endhint %}

11. Check which shard your key will validate by using the command:

```text
./hmy --node="https://api.s0.t.hmny.io" utility shard-for-bls [BLS PUBLIC KEY]
```

{% hint style="info" %}
**The BLS public key is the same as the name of the file, without the ".key".**
{% endhint %}

12. Download the node.sh by running the command:

```text
curl -LO https://raw.githubusercontent.com/harmony-one/harmony/master/scripts/node.sh && chmod a+x node.sh
```

13. Install tmux

```text
sudo yum install tmux
```

14. Create a new tmux session called "node" by using the command:

```text
tmux new-session -s node
```

15. Run the node.sh script with the following command. Once you do, it will ask for a passphrase for your BLS key file. Type your passphrase on the screen that follows and your node should be up and running.

```text
./node.sh -S -c -z -I -N staking -k [BLS KEY FILE].key
```

16. Detach your "node" tmux session by press \[Ctrl\]+b, releasing and and then press d.

17. Create a new wallet and provide your local account name by using the command:

```text
./hmy keys add mylocalaccountname --passphrase 
```

{% hint style="info" %}
Remember your passphrase. You will need it to decrypt the account keystore in order to send transactions & perform other actions. Also save your seed phrase \(mnemonic\) somewhere as well, in case you lose your keystore.
{% endhint %}

18. You can check the account balance:

```text
./hmy balances [ONE ADDRESS]
```

19. Fund your ONE address.

20. Creating a validator by replacing everything in \[ \] with your own data. 

```text
./hmy --node=https://api.s0.t.hmny.io staking create-validator \
--validator-addr [ONE ADDRESS] --amount 10000 \
--bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
--name "[NAME]" --identity "[IDENTITY]" --details "DETAILS" \
--security-contact "CONTACT" --website "YOUR-WEBSITE.COM" \
--max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
--max-total-delegation 100000000 --min-self-delegation 100000 --passphrase
```

21. Check your validator information by using the command below:

```text
./hmy --node="https://api.s0.t.hmny.io" blockchain validator information [ONE ADDRESS]
```

  
  
  
  
  
  


