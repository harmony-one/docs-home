# IPFS & Filecoin

Filecoin and IPFS are complementary protocols for storing and sharing data in the distributed web. Both systems are free, open-source, and share many building blocks, including data representation formats (IPLD) and network communication protocols (libp2p).

**IPFS** allows users to store and transfer verifiable, content-addressed data in a peer-to-peer network. It is great for getting started using [content addressing](https://docs.ipfs.io/concepts/how-ipfs-works/#content-addressing) for all sorts of distributed web applications.

IPFS alone does not include a built-in mechanism to incentivize the storage of data for other people. Built on top of IPFS, **Filecoin** is the distributed storage network to add longer term data persistence via on-chain storage deals, along with built-in economic incentives to ensure files are stored reliably over time. 

Together, IPFS & Filecoin will  help breaking free from centralized services. There are many solutions combine the two networks to get the best of both worlds: IPFS for content addressing & data discovery, and Filecoin for longer-term persistence.

In this section, you will find tutorials to guide you through the process of using IPFS and/or Filecoin for decentralized storage, including storage helpers that combine both systems such as  [nft.storage](https://nft.storage/).

+ Using IPFS

{% content-ref url="using-ipfs.md" %}
[using-ipfs.md](using-ipfs.md)
{% endcontent-ref %}

+ Using NFT.storage

{% content-ref url="using-nftstorage.md" %}
[using-nftstorage.md](using-nftstorage.md)
{% endcontent-ref %}
