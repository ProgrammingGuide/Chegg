# N-Batched Concurrent Execution

N-Batched Concurrent Execution: It is desirable for a set of K processes to execute a section of code in groups of N. In other words, a process cannot start executing that section of code until it is one of a batch of N processes that need to execute that section as a group. Using semaphores, devise a protocol that will enforce that behavior. Explain the purpose from any semaphore you use and its initialization. Show that your protocol works by implementing it using Java threading, and trying it on a set of K=12 processes that need to go through a section of code in groups of N=3. Include enough print statements (e.g., "Process i in batch j is going through") and random delays in your code to show different batches, each of size 3 going through.

## Chegg "expert answer"

public class BoundedSemaphore {
private int signals = 0;
private int bound   = 0;

public BoundedSemaphore(int upperBound){
    this.bound = upperBound;
}

public synchronized void take() throws InterruptedException{
    while(this.signals == bound) wait();
    this.signal++;
    this.notify();
}

public synchronized void release() throws InterruptedException{
    while(this.signal == 0) wait();
    this.signal--;
}
}

## Comment

Not very helpful 
