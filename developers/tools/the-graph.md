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

