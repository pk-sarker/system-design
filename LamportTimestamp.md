# Lamport Timestamp

In distributed system synchronizing clocks between systems or finding order of the events is a very hard problem.  
The Lamport timestamp algorithm is a simple logical clock algorithm used to determine the order of events in a distributed computer system.


### Why do we need it

Distributed algorithms such as resource synchronization often depend on some method of ordering events to function. 
For example, consider a system with two processes and a disk. The processes send messages to each other, and also send messages to the 
disk requesting access. The disk grants access in the order the messages were received. For example process _**A**_ sends 
a message to the disk requesting write access, and then sends a read instruction message to process **_B_**. Process **_B_** 
receives the message, and as a result sends its own read request message to the disk. If there is a timing delay causing the disk to 
receive both messages at the same time, it can determine which message happened-before the other: **_A_** happens-before 
**_B_** if one can get from **_A_** to **_B_** by a sequence of moves of two types: moving forward while remaining in the same process, 
and following a message from its sending to its reception. A logical clock algorithm provides a mechanism to determine 
facts about the order of such events. Note that if two events happen in different processes that do not exchange 
messages directly or indirectly via third-party processes, then we say that the two processes are concurrent, that is, nothing 
can be said about the ordering of the two events.



### Algorithm
Lamport invented a simple mechanism by which the happened-before ordering can be captured numerically. A Lamport logical clock is a 
numerical software counter value maintained in each process.

Conceptually, this logical clock can be thought of as a clock that only has meaning in relation to messages moving between processes. 
When a process receives a message, it re-synchronizes its logical clock with that sender. The above-mentioned vector clock is a 
generalization of the idea into the context of an arbitrary number of parallel, independent processes.

The algorithm follows some simple rules:
```
1. A process increments its counter before each local event (e.g., message sending event);
2. When a process sends a message, it includes its counter value with the message after executing step 1;
3. On receiving a message, the counter of the recipient is updated, if necessary, to the greater of its 
current counter and the timestamp in the received message. The counter is then incremented by 1 
before the message is considered received.

```
Pseudocode of the algorithm
```shell
Process A/System A/Message Sending system
# An event occurred
time = time + 1
send(message, time)

Process B/System B/Receiving System
(message, time_stamp) = receive();
time = max(time_stamp, time) + 1;
```
