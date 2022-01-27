# Concurrency

## Thead Safe

### Lock

#### synchronized

> - 지정 대상에 대한 자동 잠금과 반환

```java
// Method lock
public synchronized void method() { ... }

// Code blocks lock
public synchronized void method() { 
    synchronized(`target_to_be_locked`) { ... }
}
```

#### ReentrantLock

> - `Reentrant : 재진입 가능한`
> - `synchronized` 와 비교하여 정교한 thread lock 구현에 사용된다.

```java
import java.util.concurrent.locks.ReentrantLock;

class Clazz {
    private final ReentrantLock locker = new ReentrantLock();

    public void method() {
        
        ...

        try {
            locker.lock();

            ...
            
        } catch (Exception e) {
            //TODO: handle exception
        } finally {
            locker.unlock();
        }
    }
}
```

|Modifier|Type|Method|Actions|
|-|-|-|-|
|public|int|getHoldCount()|Count of owned lock of current thread|
|protected|Thread|getOwner()|Current lock owner|
|protected|Collection\<Thread\>|getQueuedThreads()|Waiting thread collection|
|public|int|getQueueLength()|Waiting thread count|
|protected|Collection\<Thread\>|getWaitingThreads(Condition condition)|getQueuedThreads() with condition|
|public|int|getWaitingQueueLength()|getQueueLength() with condition|
|public|boolean|hasQueuedThread(Thread thread)|Is waiting thread for current lock|
|public|boolean|hasQueuedThread()|Is there waiting thread for current lock|
|public|boolean|isFair()|Is current lock fair|
|public|boolean|isHeldByCurrentThread()|Is held by current thread|
|public|boolean|isLocked()|Is current lock held|
|public|void|lock()|lock from current position, or waiting unlock() to lock|
|public|void|lockInterruptibly()|lock(), unless interrupted|
|public|Condition|newCondition()|Get condition, that control separated signal by condition|
|public|String|toString()|get object as string|
|public|boolean|tryLock()|lock() at once without waiting|
|public|boolean|tryLock(long timeout, TimeUnit unit)|lockInterruptibly() during timeout|
|public|void|unlock()|release current lock, one by one|
