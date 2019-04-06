# Distributed Locks
If we have multiple processes running in a physical or virtual machine, we may hit a scenario where one of the processes needs to have an exclusive access on some resources. When one process wants to write to a file and wants to make sure no other process writes to the file simultaneously, the first process would get a lock on the file, performs the write and releases the lock after finishing the write. 

This scenario might arise in distributed systems as well. When there are multiple processes from multiple machines (physical or virtual) compete to have exclusive access to some resources, we might think that this problem can be solved by getting a distributed lock. But, the implementation of a distributed lock and a local lock are completely different. Using a distributed lock in a manner similar to a local lock can cause performance problems in some scenarios. We will discusss about one such scenario in the following sections.

## The problem
Let's consider a set ***T*** which contains a finite set of tasks to be executed and ***R*** be the set of resources associated with the tasks. Let ***R*** represent the state of the tasks and ***R*** = {*Executed*, *NotExecuted*}. Let's define the following function on any task t belonging to ***T***:
  - **targetResource** : ***T*** -> ***R***
  - **taskState** : ***T*** -> ***R***
  
Let ***P*** be the set of concurrent processes which will be executing the set of tasks ***T***. Let S be the set of possible states of any process and ***S***={*Idle*, *Executing*}. Let's define functions on any process belonging to ***P*** as follows
  - **processState** : ***P*** -> ***S***
  - **executes** : ***P*** -> ***T*** U ∅

### Operations
Let's define the operation *StartProcessing* and *EndProcessing* on process ***p*** belonging to ***P*** and task ***t*** belonging to ***T***.
```
/// Pre Conditions
/// processState(p) = Idle
/// taskState(t) = NotExecuted
/// there exists no process 'q' such that processState(p) = Executing and targetResource(executes(q)) = targetResource(p) equals 
StartProcessing(p,t)
{
  processState(p) = Executing
  executes(p) = t
}
```
```
/// Pre Conditions
/// executes(p) = t
EndProcessing(p,t)
{
  processState(p) = Idle
  executes(p) = ∅
  taskState(t) = Executed
}
```

The problem is to find a sequence of operations such that the pre-conditions are not violated. This means the target resource of all the tasks are same.

## The Anti-Pattern
### Simple Case
Let's consider the case where **targetResource(t) = r** for every ***t*** belonging to ***T*** and ***r*** belongs to ***R***. This means the target resource of all the processes is same.
