# Distributed Locks
If we have multiple processes running in a physical or virtual machine, we may hit a scenario where one of the processes needs to have an exclusive access on some resources. When one process wants to write to a file and wants to make sure no other process writes to the file simultaneously, the first process would get a lock on the file, performs the write and releases the lock after finishing the write. 

This scenario might arise in distributed systems as well. When there are multiple processes from multiple machines (physical or virtual) compete to have exclusive access to some resources, we might think that this problem can be solved by getting a distributed lock. But, the implementation of a distributed lock and a local lock are completely different. Using a distributed lock in a manner similar to a local lock can cause performance problems in some scenarios. We will discusss about one such scenario in the following sections.

## The problem
Let's consider a set ***S*** which contains a finite set of tasks to be executed. Let's define the following function on any task t belonging to ***S***:
  - targetResource - A mapping from task t (belonging to S) to a resource r (belonging to R)
