---
description: >-
  This tutorial will demonstrate how to build a subgraph and deploy it on
  harmony public graph node
---

# Building & Deploying Subgraph

## Quick start
lets use blocklytics/ethereum-blocks subgraph as example
```
git clone https://github.com/blocklytics/ethereum-blocks
cd ethereum-blocks
yarn
```

we will use Harmony sandbox Graph node (you can run your local one or set up a server for significant projects)
Graph: https://graph.t.hmny.io/ 
Management: https://graph.t.hmny.io:8020/ 
Metrics: https://graph.t.hmny.io:8030/

edit package.json file and add these lines
```
"create-harmony": "graph create --node https://graph.t.hmny.io:8020 harmony/blocks",
"deploy-harmony": "graph deploy --node https://graph.t.hmny.io:8020 --ipfs https://ipfs.infura.io:5001 harmony/blocks",
```

```
yarn run create-harmony
yarn run deploy-harmony
```

syncing begins and you are good to query your subgraph
https://graph.t.hmny.io/subgraphs/name/harmony/blocks/graphql

## Run Graph node locally
clone official repo
https://github.com/graphprotocol/graph-node

copy docker-compose.yml from here and replace original docker/docker-compose.yml
https://docs.harmony.one/home/developers/tools/the-graph

then run docker-compose up

## How to write subgraphes

official Graph's doc
https://thegraph.com/docs/developer/create-subgraph-hosted

medium articles
https://medium.com/protofire-blog/subgraph-development-part-1-understanding-and-aggregating-data-ef0c9a61063d
https://medium.com/protofire-blog/subgraph-development-part-2-handling-arrays-and-identifying-entities-30d63d4b1dc6

the Graph’s Discord server https://discord.gg/vtvv7FP
