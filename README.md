# Introduction

## **What is Harmony?‌**

**‌**Harmony is a decentralized blockchain ecosystem where digital assets can be securely managed and trustless computation can be efficiently executed, supporting the decentralized economy for billions of people.

For the last few years, the blockchain trilemma — decentralization vs scalability vs security — has hindered mainstream adoption of decentralized applications. Harmony breaks the limitation with carefully designed protocol combining the technology of sharding and Proof-of-Stake.

### **Secure Sharding Scheme**

Sharding is a broadly recognized solution to solve the scalability problem without compromising security and decentralization. The general idea of sharding is to divide the workload of transaction processing into separate parts and handle them in parallel. Harmony’s sharding scheme goes beyond that because it also separates the storage of ledger data in each shard, which greatly increases storage capacity of Harmony.

Sharding significantly uplifts a blockchain’s performance, however, if not done right, the security of the system can be compromised. In a sharded blockchain, the security of the whole system is as weak as a single shard. Through the fully random shuffle and periodic reshuffle of validators, Harmony makes the security of a single shard as strong as the whole network. With the help of a cryptographics-based \(VRF and VDF\) unbiasable random function, Harmony ensures its security with strong statistical guarantee.

### **Fast Consensus with Instant Finality**

The core of any blockchain is the consensus mechanism where transactions are acknowledged among all participants and can not be reverted thereafter. Harmony built on the decades of research on byzantine fault tolerance \(BFT\) algorithm and came up with FBFT consensus which scales to hundreds of nodes, provides instant finality in every block, and, of course, is super fast. In Harmony mainnet, FBFT is run among 250 nodes in each shard to produce blocks every 8 seconds, and 10+ millions of blocks have been successfully confirmed since mainnet launch.

Integrated with the FBFT consensus is the view change protocol where the majority of honest validators can jointly vote out the adversarial block proposer to prevent single point of failures. Compared to the original view change protocol in PBFT, the FBFT view change protocol is more efficient, reliable and battle-tested in our mainnet ever since June 2019.

### **Effective Proof-of-Stake and Tokenomics**

Proof-of-Stake has been the standard approach for next-generation blockchains to secure the network. As one of the first PoS blockchain with sharding, Harmony designed a new staking mechanism called Effective Proof-of-Stake \(EPoS\) which fit seamlessly with the sharding scheme to ensure network security. EPoS features an incentive design that fairly rewards all validators, big or small, and a slashing mechanism that punishes misbehaviors according to their severity.

Harmony’s token economic model is a combination of simplicity and practicality. The annual inflation is capped at 441 million ONE tokens to give validators a predictable and profitable return, while making the inflation rate as small as 3%. All transaction fees are burnt which will further offset the inflation to keep Harmony ONE tokens a good “Store of Value”.

