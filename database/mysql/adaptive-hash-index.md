Notes taken from [Mysql Adaptive Hash Index ](https://dev.mysql.com/doc/refman/8.0/en/innodb-adaptive-hash.html)
- The adaptive hash index enables InnoDB to perform more like an in-memory database on systems with appropriate combinations of workload and sufficient memory for the buffer pool without sacrificing transactional features or reliability.

- Based on the observed pattern of searches, a hash index is built using prefix of the index key, InnoDB has mechanism that monitor index searches, if a queries could benefit from building hash index, its does so automatically.
    + Its noteworthy that based on certain workloads, the speedups from hash index may outweight the extra works of monitoring index lookups and maintain hash index structure.

- Access AHI sometimes become the source of contention during heavily workloads.
    + Consider running benchmarks with it enabled or disabled.

- Monitoring AHI index use and contention in the **SEMAPHORES** section of __SHOW ENGINE INNODB STATUS__ output.