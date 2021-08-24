---
description: >-
  This tutorial will demonstrate how to build a subgraph and deploy it on
  harmony public graph node
---

# Building & Deploying Subgraph \(public graph node\)

## Install the graph-cli

[https://github.com/graphprotocol/graph-cli\#installation](https://github.com/graphprotocol/graph-cli#installation)

## Our first subgraph 

lets use blocklytics/ethereum-blocks subgraph as example

```text
git clone https://github.com/blocklytics/ethereum-blocks
cd ethereum-blocks
```

we will use Harmony sandbox Graph node \(you can run your local one or set up a server for significant projects, see next section\)

Graph: [https://graph.t.hmny.io/](https://graph.t.hmny.io/)

Management: [https://graph.t.hmny.io:8020/](https://graph.t.hmny.io:8020/)

Metrics: [https://graph.t.hmny.io:8030/](https://graph.t.hmny.io:8030/)

### Edit package.json file and add these lines

```text
"create-harmony": "graph create --node https://graph.t.hmny.io:8020 harmony/blocks",
"deploy-harmony": "graph deploy --node https://graph.t.hmny.io:8020 --ipfs http://graph.t.hmny.io:5001 harmony/blocks",
```

###  Update the manifest

Update the manifest `subgraph.yaml` file `datasources[0]['network']` from `rinkeby` to `mainnet`   
If there is no need to index the entire blockchain, you can add an attribute `startBlock` to speed up the sync : `datasources[0]['source']['startBlock']`

{% hint style="info" %}
It is highly recommended to minimize the number of blocks to be indexed to avoid putting load on the RPCs and to speed up the usage of your subgraph/application
{% endhint %}

### Create and deploy the subgraph

```text
yarn codegen
yarn build
yarn create-harmony 
yarn deploy-harmony
```

Sync begins and you are good to query your subgraph [https://graph.t.hmny.io/subgraphs/name/harmony/blocks/graphql](https://graph.t.hmny.io/subgraphs/name/harmony/blocks/graphql)

{% hint style="danger" %}
If multiple developer are deploying a graph and deploy with the same name \(ie harmony/blocks\) you will have queries and conflict issues, it's recommended to build your own indexer node for your your own testing, see next section
{% endhint %}

