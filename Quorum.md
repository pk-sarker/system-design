# Quorum
A quorum is the minimum number of votes that a distributed transaction has to obtain in order to be allowed to perform an operation in a distributed system. 
A quorum-based technique is implemented to enforce consistent operation in a distributed system.

In a distributed database system, a transaction could execute its operations at multiple sites. 
Since atomicity requires every distributed transaction to be atomic, the transaction must have the same fate (commit or abort) at every site. 
In case of network partitioning, sites are partitioned and the partitions may not be able to communicate with each other. 
This is where a quorum-based technique comes in. The fundamental idea is that a transaction is executed if the majority of sites vote to execute it.
