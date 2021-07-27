# What is Harmony?‌

**‌**Harmony is a fast and secure blockchain for decentralized applications. Our production mainnet supports 4 shards of 1000 nodes, producing blocks in 2 seconds with finality.

Our Effective Proof-of-Stake \(EPoS\) reduces centralization while supporting stake delegation, reward compounding and double-sign slashing.

Harmony aims to build an open network of nodes operated and governed by a large community. This node community is called Pangaea.

Are we decentralized yet? There’s no consensus without participation. There are now 1,000 Harmony nodes – so far 800 of them run by the community – in line with thousands of Bitcoin and Ethereum nodes. Pangaea consists of volunteers and validators from more than 100 countries and most of them have never run a node before.

## Key Innovations

### Fully Scalable Architecture

Harmony’s sharding works not only on the network communication and transaction validation, but also on the blockchain state. This makes Harmony fully scalable on all three aspects of the blockchain: network, storage and transaction processing.

### Secure Random Sharding

Harmony’s sharding process is provably secure against  shard attacks because the network validators are randomly assigned and shuffled among shards. The randomness used in the sharding is obtained with a distributed randomness generation algorithm \(based on VRF and VDF\) which is unpredictable, un-biased, verifiable and scalable. Harmony reshards the network in a non-interruptive manner using “Cuckoo Rule” to prevent against slowly adaptive byzantine adversaries.

### Efficient and Fast Consensus

Harmony’s consensus algorithm is called Fast Byzantine Fault Tolerance or FBFT. FBFT is a highly efficient and speedy consensus algorithm built upon the famous PBFT \(Practical Byzantine Fault Tolerance\) algorithm which is the cornerstone for distributed systems and consensus research for the past 30 years. Harmony’s FBFT is able to confirm blocks within 2 seconds thanks to the adoption of aggregated BLS \(Boneh–Lynn–Shacham\) signature. FBFT is also highly optimized in network message processing and block proposal pipelining so that the consensus can scale to hundreds of validators at the same time.

### Effective Proof-of-Stake

Unlike traditional blockchains which require PoW \(Proof of Work\) to reach consensus, Harmony is a Proof-of-Stake blockchain which is energy efficient and low-cost for node runners. The process to elect validators is called Effective Proof-of-Stake \(EPoS\) which is the first sharding-focused PoS mechanism that prevents stake centralization. In EPoS, validators with a large amount of staked tokens are obligated to run more nodes to support the network while validators with less stake run fewer nodes. Besides, EPoS is able to randomly and evenly distribute the stakes among all shards so no shard is less secure than other shards.

### Scalable Networking Infrastructure

Harmony’s network layer is based on the industry-leading p2p protocol named libp2p. We use libp2p’s gossip protocol for network message broadcasting and stream protocol for decentralized state synchronization. To achieve high performance, we adopt RaptorQ fountain code and use Adaptive Information Dispersal Algorithm to quickly and efficiently broadcast large blocks. Harmony also features a design where Kademlia routing is used to achieve cross-shard transactions that scale logarithmically with the number of shards.

### Asynchronous Cross-Shard Transactions

Harmony supports cross-shard transactions to achieve composability of assets and smart contracts between shards. We designed a receipt-based asynchronous cross-shard communication mechanism which achieves eventual consistency so no double-spending is possible between shards.

## Fun Facts

### **Why is the project called “Harmony”?**

Harmony is the beautiful music when we sing in different notes but resonate. It’s analogous to our high-performance protocol of multiple shards but reaching consensus.

### **Why is the token called “ONE”?**

Harmony’s vision is “For One and For All,” creating open consensus for 10 billion people.

### **Why is the logo designed as such?**

Harmony’s community is built on “Handshake & Embrace.” All Is Fair in Love and War. \(Euphues \[Euphuism\]: The Anatomy of Wit, 1579\). Read the “[Xoogler](https://harmony.one/xoogler) Interview” on our founding story.

