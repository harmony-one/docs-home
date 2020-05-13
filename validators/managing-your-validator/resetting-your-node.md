---
description: Use the below steps to reset your validator
---

# Resetting Your Validator

1. Login via SSH.

2. Attach your current tmux session in case you are not logged in on it already:

```bash
tmux attach-session -t node
```

3. Press **Ctrl** + **c** to stop what’s happening in your tmux session.

4. Manually clean the databases:

```bash
sudo rm -rf harmony_db_*
```

5. Clean the .dht files:

```bash
sudo rm -rf .dht*
```

6. Clean md5sum.txt file:

```bash
sudo rm -rf md5sum.txt
```

7. Update the `hmy` :

```bash
sudo curl -LO https://harmony.one/hmycli && sudo mv hmycli hmy && sudo chmod +x hmy
```

8. Update the binary:

```bash
curl -LO https://raw.githubusercontent.com/harmony-one/harmony/master/scripts/node.sh \
&& chmod a+x node.sh
```

9. Then run your node again by:

```bash
./node.sh -S -c -I -N staking -z -k [BLS KEY FILE].key
```

Or if you are running with Multiple BLSkeys, run your node with the following command:

```bash
./node.sh -S -c -I -N staking -z -M
```

10. Press **Ctrl** + **b** then **d** to dettach from the tmux session.

11. Have your ONE address funded.

12. Create your validator again:

```bash
./hmy --node="https://api.s0.t.hmny.io" staking create-validator \
    --validator-addr [ONE ADDRESS] --amount 10000 \
    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \
    --name "[NAME]" --identity "[IDENTITY]" --details "DETAILS" \
    --security-contact "CONTACT" --website "YOUR-WEBSITE.COM" \
    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \
    --max-total-delegation 100000000 --min-self-delegation 10000 --passphrase
```

{% hint style="info" %}
Your validator should be up and you should get elected after one epoch — check on staking dashboard.
{% endhint %}

