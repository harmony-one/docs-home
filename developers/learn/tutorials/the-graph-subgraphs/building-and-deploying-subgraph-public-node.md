---
description: >-
  This tutorial will demonstrate how to build a subgraph and deploy it on
  harmony public graph node
---

# Building & Deploying Subgraph \(public graph node\)

## Quick start

### Install the graph-cli

[https://github.com/graphprotocol/graph-cli\#installation](https://github.com/graphprotocol/graph-cli#installation)

### Our first subgraph 

lets use blocklytics/ethereum-blocks subgraph as example

```text
git clone https://github.com/blocklytics/ethereum-blocks
cd ethereum-blocks
yarn
```

we will use Harmony sandbox Graph node \(you can run your local one or set up a server for significant projects, see next section\)

Graph: [https://graph.t.hmny.io/](https://graph.t.hmny.io/)

Management: [https://graph.t.hmny.io:8020/](https://graph.t.hmny.io:8020/)

Metrics: [https://graph.t.hmny.io:8030/](https://graph.t.hmny.io:8030/)

edit package.json file and add these lines

```text
"create-harmony": "graph create --node https://graph.t.hmny.io:8020 harmony/blocks",
"deploy-harmony": "graph deploy --node https://graph.t.hmny.io:8020 --ipfs https://ipfs.infura.io:5001 harmony/blocks",
```

```text
yarn run create-harmony
yarn run deploy-harmony
```

Syncing begins and you are good to query your subgraph [https://graph.t.hmny.io/subgraphs/name/harmony/blocks/graphql](https://graph.t.hmny.io/subgraphs/name/harmony/blocks/graphql)

{% hint style="danger" %}
If multiple developer are deploying a graph and deploy with the same name \(ie harmony/blocks\) you will have queries and conflict issues, it's recommended to build your own indexer node for your your own testing, see next section
{% endhint %}

