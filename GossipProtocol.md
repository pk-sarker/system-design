# Gossip Protocol
In a large distributed environment where we do not have any central node that keeps track of all nodes to know if a node is down or not, 
how does a node know every other node’s current state? The simplest way to do this is to have every node maintain a heartbeat 
with every other node. Then, when a node goes down, it will stop sending out heartbeats, and everyone else will find out immediately. 
But, this means <i>O<sup>2</sup></i> messages get sent every tick (**_N_** being the total number of nodes), which is a 
ridiculously high amount and will consume a lot of network bandwidth, and thus, not feasible in any sizable cluster. So, is there any other option for monitoring the state of the cluster?