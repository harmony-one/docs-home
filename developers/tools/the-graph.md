# The Graph

The Graph is available for use on Harmony:

Graph: [https://graph.t.hmny.io/](https://graph.t.hmny.io/)   
Management: [https://graph.t.hmny.io:8020/](https://graph.t.hmny.io:8020/)   
Metrics: [https://graph.t.hmny.io:8030/](https://graph.t.hmny.io:8030/)  
  
To upload a subgraph using IP address:

```text
graph create --node https://graph.t.hmny.io:8020/  namespace/subgraph
```

Note: The Graph is only a sandbox. We do not guarantee uptime or data persistence. Projects should run their own instances and not rely on sandbox Graph. To run Graph locally, use the official repo at [https://github.com/graphprotocol/graph-node](https://github.com/graphprotocol/graph-node) with the RPC `https://a.api.s0.t.hmny.io` 

It is important to enable "env var" for Graph:

```text
GRAPH_ETH_CALL_BY_NUMBER: 1
GRAPH_NO_EIP_1898_SUPPORT: 1
```

#### Graph docker for Harmony

Docker for running graph node for Harmony mainnet. Copy the code below to `docker-compose.yml` and run `docker-compose up` command to launch a local graph node for Harmony mainnet. 

```text
version: "3"
services:
  graph-node:
    container_name: hmy_indexer
    image: graphprotocol/graph-node:0.23.1
    ports:
      - "8000:8000"
      - "8001:8001"
      - "8020:8020"
      - "8030:8030"
      - "8040:8040"
    depends_on:
      - ipfs
      - postgres
    environment:
      postgres_host: postgres
      postgres_user: graph-node
      postgres_pass: let-me-in
      postgres_db: graph-node
      ipfs: "ipfs:5001"
      GRAPH_ETH_CALL_BY_NUMBER: 1
      GRAPH_NO_EIP_1898_SUPPORT: 1
      GRAPH_ALLOW_NON_DETERMINISTIC_IPFS: 1
      ethereum: 'mainnet:no_eip1898,archive,traces:https://a.api.s0.t.hmny.io"
      RUST_LOG: info
  ipfs:
    container_name: ipfs
    image: ipfs/go-ipfs:v0.4.23
    ports:
      - "5001:5001"
    volumes:
      - ./data/ipfs:/data/ipfs
  postgres:
    image: postgres
    ports:
      - "5432:5432"
    command: ["postgres", "-cshared_preload_libraries=pg_stat_statements"]
    environment:
      POSTGRES_USER: graph-node
      POSTGRES_PASSWORD: let-me-in
      POSTGRES_DB: graph-node
    volumes:
      - ./data/postgres:/var/lib/postgresql/data
```

### Example Subgraphs

* [HRC20, HRC721, HRC1155 subgraphs](https://github.com/harmony-one/harmony-tokens-subgraph)
* [horizon-bridge-subgraph](https://github.com/harmony-one/horizon-bridge-subgraph) is built to support querying [http://bridge.harmony.one/](http://bridge.harmony.one/)

