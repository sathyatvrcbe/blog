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
To implement a solution to the above problem, many of us are tempted to write the process as given below.
```
process()
{
  while(true)
  {
    pick a t belonging to the set T where taskState(t) = NotExecuted
    lock(targetResource(T))
    {
      if(taskState(t) == NotExecuted)
      {
        StartProcessing(this,t);
        FinistProcessing(this,t);
      }
    }
  }
}
```
On first look, this solution looks good. If all the processes are within a machine, the *lock()* function can be implemented using a hardware lock. But, in a distributed environment, where the processes are distributed across machines, the *lock()* function is costly. Under the hood, this *lock()* function solves the **consensus** problem. Each *lock()* in the above code block solves one instance of the consensus problem. To understand why consensus problems are costly, please refer the [Part-Time Parliament](http://lamport.azurewebsites.net/pubs/lamport-paxos.pdf)  paper, [RAFT protocol](https://raft.github.io/), [Zookeeper](https://zookeeper.apache.org/) and [Chubby](https://static.googleusercontent.com/media/research.google.com/en//archive/chubby-osdi06.pdf).

Apart from the problem of costly distributed locks, there are other problems which are inherent to locking is also present in this solution. Let's assume that the set S is very large and 90 percent of the unprocessed tasks have the same target resource *r*. If all the processes picks an unexecuted task randomly, approximately 90 percent of the processes will pick a task such that the its target resource is *r*. According to the above implementation, only one of the 90 percent processes will be able to execute any task and the rest of the processes will be waiting on the lock. This creates a live lock situation for those processes waiting on the thread. And the other 10 percent of the tasks will be starved because of unavailability of processes to process them.

Let us take the best case scenario where there are no conflicts between the processes while obtaining the locks. Even in this best case, this solution has to solve **Size(T)** consensus problems. If we compute the compleity of the system in terms of the number of consensus problem it solves, the computational complexity in the best case becomes order of **Size(T)**.
