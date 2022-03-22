# PACELC Theorem
The **_PACELC_** theorem is an extension to the CAP theorem.

It states that in case of network partitioning (**_P_**) in a distributed computer system, 
one has to choose between availability (**_A_**) and consistency (**_C_**) (as per the CAP theorem), but else (**_E_**), 
even when the system is running normally in the absence of partitions, one has to choose between **_latency (L)_** and **_consistency (C)_**.

Examples:

Database PACELC ratings are from
- The default versions of **_DynamoDB_**, **_Cassandra_**, **_Riak_** and **_Cosmos DB_** are PA/EL systems: if a partition occurs, 
they give up consistency for availability, and under normal operation they give up consistency for lower latency.
- Fully ACID systems such as **_VoltDB/H-Store_**, **_Megastore_** and **_MySQL_** Cluster are PC/EC: they refuse to give up consistency, and will 
pay the availability and latency costs to achieve it. BigTable and related systems such as HBase are also PC/EC.
- **_Couchbase_** provides a range of consistency and availability options during a partition, and equally a range of latency and consistency options with no partition. Unlike most other databases, Couchbase doesn't have a single API set nor does it scale/replicate all data services homogeneously. For writes, Couchbase favors Consistency over Availability making it formally CP, but on read there is more user-controlled variability depending on index replication, desired consistency level and type of access (single document lookup vs range scan vs full-text search, etc.). On top of that, there is then further variability depending on cross-datacenter-replication (XDCR) which takes multiple CP clusters and connects them with asynchronous replication and Couchbase Lite which is an embedded database and creates a fully multi-master (with revision tracking) distributed topology.
- **_Cosmos_** DB supports five tunable consistency levels that allow for tradeoffs between C/A during P, and L/C during E. Cosmos DB never violates the specified consistency level, so it's formally CP.
- **_MongoDB_** can be classified as a PA/EC system. In the baseline case, the system guarantees reads and writes to be consistent.
- **_PNUTS_** is a PC/EL system.
- **_Hazelcast_** IMDG and indeed most in-memory data grids are an implementation of a PA/EC system; Hazelcast can be configured to be EL rather than EC.[5] Concurrency primitives (Lock, AtomicReference, CountDownLatch, etc.) can be either PC/EC or PA/EC.[6]
- **_FaunaDB_** implements Calvin, a transaction protocol created by Dr. Daniel Abadi and author[1] of PACELC theorem, and offers users adjustable controls for LC tradeoff. It is PC/EC for strictly serializable transactions, and EL for serializable reads.
