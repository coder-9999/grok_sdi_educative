### Consensus ## 
Consensus is a problem in distributed systems which becomes impossible to solve under certain scenarios

The common challenges that distributes applications deal with are-
  - ** Reliable Multicast ** :Make sure all the nodes in the network receives the same updates in the same order as each other.
  - ** Membership/ Failure Detection ** : To keep local list at servers where they know about each other and when anyone joins, leaves or fails, everyone is updated simultaneously.
  - ** Leader Election ** : When nodes need to elect a leader among them and let evryone in the group know about it.
  - ** Mutual Exclusion/Locking ** : To ensure exclusive access to critical resources like a file.
  
## What is common across above problem statements? ##
Lets call each server a process. Then our distibuted app is a set of processes talking to each other over the network, these could be processes on the same machines or dfferent remote machies.
All these processes are attempting to ** coordinate ** with each other and reach agreement on something-
  - The ordering of messages
  - The status of alive/new/failed nodes
  - Who the leader is
  - Who currently holds access to the critical resource
All of these are realted to consensus which lets processes coordinate with each other and agree on the value of something.

## What is Consensus? ##
