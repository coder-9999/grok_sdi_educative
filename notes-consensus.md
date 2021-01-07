### Consensus ## 
Consensus is a problem in distributed systems which becomes impossible to solve under certain scenarios

The common challenges that distributes applications deal with are-
  - **Reliable Multicast** :Make sure all the nodes in the network receives the same updates in the same order as each other.
  - **Membership/ Failure Detection** : To keep local list at servers where they know about each other and when anyone joins, leaves or fails, everyone is updated simultaneously.
  - **Leader Election** : When nodes need to elect a leader among them and let evryone in the group know about it.
  - **Mutual Exclusion/Locking** : To ensure exclusive access to critical resources like a file.
  
## What is common across above problem statements? ##
Lets call each server a process. Then our distibuted app is a set of processes talking to each other over the network, these could be processes on the same machines or dfferent remote machies.
All these processes are attempting to **coordinate** with each other and reach **agreement** on something-
  - The ordering of messages
  - The status of alive/new/failed nodes
  - Who the leader is
  - Who currently holds access to the critical resource
All of these are realted to consensus which lets processes coordinate with each other and agree on the value of something.

## What is Consensus? ##
Given n processes, each process P has 2 binary variables:
  - Input variable Xp: Represents P's contribution or proposal to the group, is initialyy 0 or 1
  - output Variable Yp: Initially undecided. Also. process P can change this output var exactly once, once decided cannot be changed afterwards.
**Consensus Problem** is to design a distibuted protocol such that at the end of the protocol, al the processes decide the same output variable , i.e. either all of the processes set their O/p var to 0 or all set it to 1.

### Summary ###
- every process contributes a value
- the goal is to have all the processes deciding the same value, whatever value it is, either 0 or 1,
- once a process makes a decision, it cannot change that decision. (because the decision is communicated up to the application, and the application might take certain actions based on that decision.)

### Why solving consensus is important? ###
The consensus problem is important because several important, uh, distributed computing problems are, uh, related to it. They are either equivalent to consensus, which means that, um, they are in fact the same problem, if you can solve consensus, you can solve the other problem, and if you can solve the other problem you can solve consensus.

For example, Failure Detection and Leader Election are equivalent to consensus.

### What are the challenges with solving consensus? ###
So, there are 2 kinds of system models in distributed systems:
  - Synchronous Distributed Systems: 
      - has bounds on everything. As long as the sender and recipient processes are alive, the message will be delivered within that bounded time.
      - local clocks do not drift away from each other too much
      - each process has a minimum speed and also a maximum speed at which it executes instructions. In other words, each step in a process takes a time that is lower bounded by a well-known value.
  - Asynchronous Distributed Systems: no not meet above three
  
It is impossible to solve consensus in Asynchronous model
  
