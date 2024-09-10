# Tuning

## Tuning Pinot

This section provides information on various options to tune Pinot cluster for storage and query efficiency. Unlike key-value store, tuning Pinot sometimes can be tricky because the cost of query can vary depending on the workload and data characteristics.

If you want to improve query latency for your use case, you can refer to `Index Techniques` section. If your use case faces the scalability issue after tuning index, you can refer `Optimizing Scatter and Gather` for improving query throughput for Pinot cluster. If you have identified a performance issue on the specific component (broker or server), you can refer to the `Tuning Broker` or `Tuning Server` section.

* [Index Techniques](../../../basics/indexing/)
* [Star-Tree: A Specialized Index for Fast Aggregations](../../../basics/indexing/star-tree-index.md)
* [Optimizing Scatter and Gather](https://docs.pinot.apache.org/operators/operating-pinot/tuning/routing)
* [Tuning Real-time Performance](realtime.md#tuning-realtime-performance)\


