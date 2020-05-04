# Introduction

## **What is Harmony?‌**

**‌**Harmony is a decentralized blockchain ecosystem where digital assets can be securely managed and trustless computation can be efficiently executed, supporting the decentralized economy for billions of people.

For the last few years, the blockchain trilemma — decentralization vs scalability vs security — has hindered mainstream adoption of decentralized applications. Harmony breaks the limitation with carefully designed protocol combining the technology of sharding and Proof-of-Stake.

### **Secure Sharding**

Sharding is a broadly recognized solution to solve the scalability problem without compromising security and decentralization. The basic principle of sharding is to divide the workload of transaction processing into separate parts and handle them in parallel across multiple shards. Harmony’s innovative sharding approach goes far deeper by separating the storage of ledger data within each shard, massively increasing the storage capacity of the network.

Sharding can bring about significant improvements in a blockchain’s performance, however, it also creates more challenges at the security level. If not done right, the security of a sharded network is only as strong as its weakest shard. But by employing the fully random shuffle and periodic reshuffle of its validators, Harmony makes the security of a single shard as strong as that of the whole network. With the help of a cryptographics-based \(VRF and VDF\) un-biasable random function, Harmony ensures its security with strong statistical guarantee.

### **Fast Consensus with Instant Finality**

The core of any blockchain is its consensus mechanism where transactions are confirmed among all participants and can not be reverted. Harmony has built on decades of research on byzantine fault tolerance \(BFT\) algorithm to develop what we call Fast Byzantine Fault Tolerance \(FBFT\). FBFT allows Harmony to scale to hundreds of nodes, providing instant finality in every block and allowing low-cost transactions. In Harmony mainnet, FBFT is run by 250 nodes per shard to produce blocks every 8 seconds and 10+ millions of blocks have been successfully confirmed since the mainnet launched in June 2019.

The second key innovation is our variant of the view change protocol where a majority of honest validators can jointly vote out an adversarial block proposer to prevent single point of failures. Compared to the original view change protocol in PBFT, the FBFT view change protocol is more efficient, reliable and successfully battle-tested in our mainnet.

### **Effective Proof-of-Stake and Tokenomics**

Proof-of-Stake has become the most commonly adopted standard for the next-generation of high-speed blockchains. Harmony’s key innovation was to design a radically new staking mechanism called Effective Proof-of-Stake \(EPoS\) which fit seamlessly with our sharding scheme to ensure network security. EPoS features an incentive design that fairly rewards all validators, big or small, and a slashing mechanism that punishes misbehaviors according to their severity.

Harmony’s token economic model is a combination of simplicity and practicality. The annual inflation is capped at 441 million ONE tokens to give validators a predictable and profitable return, while making the inflation rate as small as 3%. All transaction fees are burnt which will further offset the inflation and achieve zero inflation when network usage is high.

