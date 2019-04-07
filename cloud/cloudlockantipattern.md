# An Anti-Pattern Distributed Locks
If we have multiple processes running in a physical or virtual machine, we may hit a scenario where one of the processes needs to have an exclusive access on some resources. When one process wants to write to a file and wants to make sure no other process writes to the file simultaneously, the first process would get a lock on the file, performs the write and releases the lock after finishing the write. 

This scenario might arise in distributed systems as well. When there are multiple processes from multiple machines (physical or virtual) compete to have exclusive access to some resources, we might think that this problem can be solved by getting a distributed lock. But, the implementation of a distributed lock and a local lock are completely different. Using a distributed lock in a manner similar to a local lock can cause performance problems in some scenarios. We will discusss about one such scenario in the following sections.

## The problem
Let's consider a set ***T*** which contains a finite set of tasks to be executed and a set ***R*** which contains a finite set of resources. Let ***Q*** represent the state of the tasks and ***R*** = {*Executed*, *NotExecuted*}. Let's define the following function on any task t belonging to ***T***:
  - **targetResource** : ***T*** -> ***R***
  - **taskState** : ***T*** -> ***Q***
  
Let ***P*** be the set of concurrent processes which will be executing the tasks in ***T***. Let S be the set of possible states of any process and ***S***={*Idle*, *Executing*}. Let's define the following functions on any process belonging to ***P***:
  - **processState** : ***P*** -> ***S***
  - **executes** : ***P*** -> ***T*** U ∅

### Operations
Let's define the operations *StartProcessing* and *EndProcessing* on process ***p*** belonging to ***P*** and task ***t*** belonging to ***T***. Each of the operations defined below have some pre-conditions and these pre-conditions should be satisfied when these operations are performed.
```
/// Pre Conditions
/// processState(p) = Idle
/// taskState(t) = NotExecuted
/// there exists no process 'q' such that processState(q) = Executing and targetResource(executes(q)) = targetResource(p)
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

The problem is to find an ordered execution of the above operations such that the pre-conditions are not violated and all the tasks in ***T*** reaches *Executed* state.

## The Anti-Pattern
One simple solution to solve the problem is to obtain a lock on these target resource of the task that is being executed. The code snippet which illustrates this solution is give below.
```
process()
{
  while(true)
  {
    pick a task t belonging to the set T where taskState(t) = NotExecuted
    lock(targetResource(T))
    {
      if(taskState(t) == NotExecuted)
      {
        StartProcessing(this,t);
        FinishProcessing(this,t);
      }
    }
  }
}
```
On first look, this solution looks good. If all the processes are within a machine, the *lock()* function can be implemented using a hardware lock. But, in a distributed environment, where the processes are distributed across machines, the *lock()* function is costly. Under the hood, this *lock()* function solves the **consensus** problem. Each *lock()* in the above code block solves one instance of the consensus problem. To understand why consensus problems are costly, please refer the [Part-Time Parliament](http://lamport.azurewebsites.net/pubs/lamport-paxos.pdf)  paper, [RAFT protocol](https://raft.github.io/), [Zookeeper](https://zookeeper.apache.org/) and [Chubby](https://static.googleusercontent.com/media/research.google.com/en//archive/chubby-osdi06.pdf).

Apart from the problem of costly distributed locks, there are other problems which are inherent to locking is also present in this solution. Let's assume that the set S is very large and 90 percent of the unprocessed tasks have the same target resource *r*. If all the processes picks and unexecutes task randomly, approximately 90 percent of the processes will pick a task such that the its target resource is *r*. According to the above implementation, only one of these 90 percent processes will be able to execute any task and the rest of the processes will be waiting on the lock. This creates a live lock situation for those processes waiting on the lock. And the other 10 percent of the tasks will be starved because of unavailability of processes to process them.

Let us take the best case scenario where there are no conflicts between the processes while obtaining the locks. Even in this best case scenario, this solution has to solve **Size(T)** consensus problems. If we compute the complexity of the system in terms of the number of consensus problem it solves, the best case computational complexity will be of order **Size(T)**.

## One Consensus Problem Per Target Resource
For this problem, we connot skip solving consensus problem. But, we can reduce the number consensus problem that we solve. In the solution given above, we were trapped by the *lock()* semantics.

Let's introduce another consensus operation called *getOwnership()*. The operation *getOwnership()* solves the consensus problem to give ownership to one of the competing processes. The idea of the solution below is to get consensus on the ownership on distinct resources before we start processing any task. Once a process ***p*** gets ownership for a resource, it can sequentially execute the tasks corresponding to the resources owned by the task.
```
onStart()
{
  foreach unique targetResource r
  {
    success = getOwnership(r);
    if(success)
    {
      ownedSet(this) = ownedSet(this) U {r};
    }
  }
}

process()
{
  while(true)
  {
    pick a task t such that targetResource(t) belongs to ownedSet(this) and taskState(t) = NotExecuted
    StartProcessing(this,t);
    FinistProcessing(this,t);
  }
}
```
If there are **N** distinct target resources,  only **N** consensus problems will be solved. If any new process enters the system or if any process goes out of the system, to redistribute the tasks within the processes, *getOwnership()* operation can be processed on a subset of tasks. Assuming adding/removing of processes to the system as a rare scenario, we can safely assume that the number of consensus problems solved in this solution to be of order **N**.

## One Consensus Problem Per Target Resource Group
One drawback of the above solution is its worst case performance. The input in which all the tasks have different target resources is the worst case input and with this input the solution solves the consensus problem ***Count(T)*** times which is same as the complexity of the first solution. Let's try to reduce furhter the number of consensus problem that we solve.

Let's define some more terminologies regarding groups and group memberships. Let ***G*** be the set of groups. We define few functions as follows:
  - ***groupForResource*** : ***R*** -> ***G***
  - ***uniqueTargetResources*** : ***PowerSet(T)*** -> ***PowerSet(R)*** where 
    - ***uniqueTargetResources(T)*** = Union of ***targetResourceType(t)*** for every ***t*** in ***T***
    
With the functions defined above, the solution to our original problem can be written as follows:
```
onStart()
{
  foreach g in G  
  {
    success = getOwnership(g);
    if(success)
    {
      ownedSet(this) = ownedSet(this) U {g};
    }
  }
}

process()
{
  while(true)
  {
    pick a task t such that groupForResource(targetResource(t)) belongs to ownedSet(this) and taskState(t) = NotExecuted
    StartProcessing(this,t);
    FinistProcessing(this,t);
  }
}
```
This solution is similar to the one provided in the previous section except that the consensus problem is solved over the group instead of being solved over the resource. The effeciency of this solution depends upon the number of groups ***Count(G)*** and the concrete implementation of the function ***groupForResource***. 

If the number of groups is lesser than the number of processes, then there will be some processes which will not have any groups assigned. This leads to ineffecient use of the computing resources available. So, the number of groups should be at least equal to the number of processes. If we make the number of groups equal ***uniqueTargetResources(T)*** and assign each member of ***uniqueTargetResource(T)*** to one group, this solution reduces to the solution presented in the above section. So, the ideal number of groups should be at least ***Count(P)*** and should be of the order ***Count(P)***. Hence the number of consensus problems that we solve remains of order ***Count(P)***.

The function ***groupForResource*** should be designed in such a way that the number of tasks processed by each process are of equal numbers. When the tasks are more biased towards certain target resources, we cannot do much in improving the throughput of the system. But, what we save is the number of consensus problem that we solve. As we are discussing this problem abstractly, we will not go into the design of the function ***groupForResource()***.

So, let's understand that the distributed lock is not a hardware lock but a costly consensus problem. Let's make the right choice and avoid the misuse of distributed locks. 
