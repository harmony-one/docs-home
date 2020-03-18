---
description: Use the below steps to reset your node after OSTN refresh
---

# Resetting Your Node

1. Open your terminal 

2. `CD` into the folder with your .pem file

3. Connect to your instance by the SSH command you get from AWS: `ssh -i "pangaea-key.pem" ec2-user@ec2-13-250-30-215.ap-southeast-1.compute.amazonaws.com`

4. Start a tmux session`tmux attach`

5. Press `control+c` to stop what’s happening in your tmux session

6. Then run your node again by:

```text
./node.sh -S -c -I -N staking -z -k [BLS KEY FILE].key
```

Or if you are running with Multiple BLSkeys, run your node with the following command

```text
./node.sh -S -c -I -N staking -z -M
```

7. Press `control+b then d` to detach from tmux session

8. Fund your ONE address using: 

```text
curl -X GET https://faucet.os.hmny.io/fund?address=[ONE ADDRESS]
```

9. Create your validator again

{% tabs %}
{% tab title="Open Staking Testnet" %}
```text
./hmy --node=https://api.s0.os.hmny.io staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 10 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name "[NAME]" --identity "[IDENTITY]" --details "DETAILS" \
    --security-contact "CONTACT" --website "YOUR-WEBSITE.COM" \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100 --min-self-delegation 10 --passphrase

```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Your validator should be up and you should get elected after one epoch — check on staking dashboard
{% endhint %}

