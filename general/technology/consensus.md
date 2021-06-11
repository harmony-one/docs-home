# Consensus

### Fast Byzantine Fault Tolerance \(FBFT\)

The consensus algorithm is a key component of any blockchain. It determines the security and performance of a blockchain and is often referred to as the "engine" of a blockchain. Harmony’s consensus algorithm is called **Fast Byzantine Fault Tolerance \(FBFT\)**, which is an innovative upgrade on the famous PBFT algorithm. FBFT is one order of magnitude faster and more scalable than PBFT because BLS \(Boneh–Lynn–Shacham\) aggregate signature is used to significantly reduce the communication cost. Specifically, FBFT allows at least 250 validators to reach consensus within 2 seconds.

For every round of consensus in FBFT, one validator serves as the “leader” and there are three phases: the announce phase, the prepare phase and the commit phase. In the announce phase, the leader proposes a new block and broadcasts the block hash to all of the validators. In the prepare phase, validators verify the message and sign on the block hash, as well as sending the signature back to the leader. The prepare phase finishes when signatures with more than 2/3 of the voting power are collected. After that, the leader aggregated the collected signatures into a O\(1\)-sized BLS aggregate signature and then broadcast it with the whole block to start the commit phase. The commit phase involves validators verifying the block and doing a similar signing process as the prepare phase \(i.e. 2/3 voting power collection\). The consensus is reached after the commit phase is done. This whole process can be done within 2 seconds in mainnet.

![Network communication during a single round of consensus.](https://lh5.googleusercontent.com/_XUr5ImkES1QtMPQeVHJv1wTxO9xo6iMarIj_9gOj0p6aAaetRlmt67G8kfqEZAHPPUrWvF52FWHo-BPWNlIoTl8hlAjyE5DEbCMrcGZLuJ4gc1fyb-p4nAjjTmdgIZXzTy8MwCj)

Specifically, Harmony’s FBFT consensus involves the following steps:

1. The leader constructs the new block and broadcasts the block hash to all validators. This is called the “announce” phase.
2. The validators check the validity of the message, sign the block hash with a BLS signature, and send the signature back to the leader.
3. The leader waits for valid signatures with more than 2/3 voting power from validators \(including the leader itself\) and aggregates them into a BLS aggregate signature. Then the leader broadcasts the new block and the aggregated signature along with a bitmap indicating which validators have signed. Together with Step 2, this concludes the “prepare” phase.
4. The validators check that the aggregate signature has at least 2/3 of total voting power, verify the new block, sign the received block from Step 3, and send it back to the leader.
5. The leader waits for valid signatures with more than 2/3 voting power \(can be different signers from Step 3\), aggregates them together into a BLS aggregate signature, and creates a bitmap for all the signers. Finally, the leader commits the new block with the aggregate signatures and bitmaps into local DB, and broadcasts the aggregate signature and bitmap for all validators to confidently commit the block too. Together with Step 4, this concludes the “commit” phase.

### **Synchronous View Change**

One of the drawbacks of BFT-based consensus is the potential stallment of the consensus if the leader is malicious. The solution to this in PBFT algorithm is the additional view change protocol on top of the consensus which is able to switch leaders when the consensus is stalled. The view change in PBFT works well in the traditional distributed system setting but it fails in the more complicated blockchain space. Particularly, the view change in PBFT is relying on the timeout mechanism where the timer is triggered based on the live progress of the consensus. This works fine if the nodes are always online and are in sync with the consensus progress. However, this won’t be true in the real world situation where nodes can be down for extended time or restarted due to machine crash, which will make the nodes having inconsistent view IDs and not able to make progress in the view change.

We solve this problem by using an improved version of the view change protocol that’s fully synchronous based on the local clock rather than assuming the liveness of the nodes. Specifically, instead of setting the validator’s view ID based on the live progress of the consensus, the view ID is calculated based on the elapsed time of the last successfully committed block’s timestamp. Of course, there is no global clock to rely on in the calculation of elapsed time. Each validator will use their own local clock for that. However, this is totally fine as long as more than 2/3 of the validators maintain a relatively accurate local clock that’s not drifting by a few seconds. This is achievable in the protocol to make validators to periodically synchronize its local clock with NTP time.

This improvement makes our view change protocol fully robust and functional as long as more than 2/3 of the honest validators are online, guaranteeing the liveness of the FBFT consensus. Besides, BLS aggregate signatures are also used in the view change protocol to reduce network communication cost, making it a very efficient process which takes a few seconds to finish.  
****

