# Quorum
A quorum is the minimum number of votes that a distributed transaction has to obtain in order to be allowed to perform an operation in a distributed system. 
A quorum-based technique is implemented to enforce consistent operation in a distributed system.

In a distributed system, a transaction could execute its operations at multiple sites. 
Since atomicity requires every distributed transaction to be atomic, the transaction must have the same fate (**_commit_** or **_abort_**) at every site. 
In case of network partitioning, sites are partitioned and the partitions may not be able to communicate with each other. 
This is where a **_quorum_**-based technique comes in. 
The fundamental idea is that a transaction is executed if the majority of sites vote to execute it.

Every site in the system is assigned a vote <i>V<sub>i</sub></i>. 
Let us assume that the total number of votes in the system is _V_ and 
the **_abort_** and **_commit_** quorums are <i>V<sub>a</sub></i> and <i>V<sub>c</sub></i>, respectively. 
Then the following rules must be obeyed in the implementation of the commit protocol:

- <i>V<sub>a</sub></i> + <i>V<sub>c</sub></i> > _V_, where _0_ < <i>V<sub>c</sub></i>.
  - We don't want <i>V<sub>a</sub></i> = <i>V<sub>c</sub></i>
  - This ensures that a transaction cannot be committed and aborted at the same time.
- Before a transaction **_commits_**, it must obtain a commit quorum <i>V<sub>c</sub></i>. The total of at least one site that is prepared to commit and zero or more sites waiting >= <i>V<sub>c</sub></i>
- Before a transaction **_aborts_**, it must obtain an abort quorum <i>V<sub>a</sub></i>, The total of zero or more sites that are prepared to abort or any sites waiting >= <i>V<sub>a</sub></i>

Second and third rules indicate the votes that a transaction has to obtain before it can terminate one way or the other.

Quorum is achieved when nodes follow the below protocol:_R+W>N_, where: \
_N_ = nodes in the quorum group\
_W_ = minimum write nodes \
_R_ = minimum read nodes.

If a distributed system follows _R+W>N_ rule,

For example, a common configuration could be (_N=3, W=2, R=2_) to ensure strong consistency. Here are a couple of other examples:
- _(N=3,W=1,R=3)_: fast write, slow read, not very durable
- _(N=3,W=3,R=1)_: slow write, fast read, durable
The following two things should be kept in mind before deciding read/write quorum:
- _R=1_ and _W=N_ ⇒ full replication (write-all, read-one):undesirable when servers can be unavailable because writes are not guaranteed to complete.
- Best performance (throughput/availability) when _1 < r < w < n_

Quorum is also used to ensure that at least one node receives the update in case of failure
in Cassandra, to ensure data consistency, each write request can be configured to be 
successful only if the data has been written to at least a quorum (or majority) of replica nodes.


# Sloppy Quorum 
Dynamo replicates writes to a sloppy quorum of other nodes in the system, instead of a strict majority quorum like Paxos. 
All read/write operations are performed on the first N healthy nodes from the preference list, which may not always be the first N nodes encountered while walking the consistent hashing ring.
Sloppy quorums are particularly useful for increasing write availability.

