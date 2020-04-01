# Optimizations

## State Pruning

State pruning is a feature we implemented in harmony nodes to prune redundant state nodes from the state DB before it was written to the DB. State pruning will reduce the blockchain size from current 80+G \(as of Feb/25/2020\) to &lt;2G. Validators can reduce the disk size significantly to save the cloud cost. You can refer to ethereum’s [State Tree Pruning](https://blog.ethereum.org/2015/06/26/state-tree-pruning/).  


