# Swoole Lock

Swoole locks enable PHP developers use locks for data synchronization between multiple theads or processes.

Swoole locks은 PHP 개발자가 여러 스레드 또는 프로세스 간의 데이터 동기화를 위해 잠금을 사용할 수있게합니다.

Lock types:

잠금 유형 :

* SWOOLE_FILELOCK: file lock
* SWOOLE_RWLOCK: read write lock
* SWOOLE_SEM: Linux semaphore
* SWOOLE_MUTEX: Mutex
* SWOOLE_SPINLOCK: spin lock

### Methods

#### swoole_lock->__construct($type, $file_lock_location = '/tmp/file.lock');

Construct a lock.

락을 구축합니다.

#### swoole_lock->__destruct();

Destory a lock.

자물쇠를 파괴하십시오.

#### swoole_lock->lock();

Try to acquire the lock. It will block if the lock is not available.

자물쇠를 잡으려고하십시오. 잠금을 사용할 수없는 경우 차단하려고합니다.

#### swoole_lock->lockwait($timeout = 1);

Try to acquire the lock and waiting the lock for a duration before giving up.

포기하기 전에 자물쇠를 획득하고 자물쇠를 기다려보십시오.

#### swoole_lock->trylock();

Try to acquire the lock and return straight away even the lock is not available.

잠금 장치를 사용할 수 없습니다.

#### swoole_lock->lock_read();

Lock a read-write lock for reading.

읽기 위해 읽기 / 쓰기 잠금을 잠급니다.

#### swoole_lock->trylock_read();

Try to lock a read-write lock for reading and return straight away even the lock is not available.

읽고 쓸 수있는 잠금 장치를 잠그고 곧바로 잠금 장치를 사용할 수없는 경우에도 반환하십시오.

#### swoole_lock->unlock();

Release the lock.

자물쇠를 놓습니다.


### Example:

```php
<?php

$lock = new swoole_lock(SWOOLE_MUTEX);
echo "[Master] Create lock\n";
$lock->lock();
if (pcntl_fork() > 0)
{
    sleep(1);
    $lock->unlock();
} 
else
{
    echo "[Child] Wait Lock\n";
    $lock->lock();
    echo "[Child] Get Lock\n";
    $lock->unlock();
    exit("[Child] exit\n");
}
echo "[Master]release lock\n";
unset($lock);
sleep(1);
echo "[Master]exit\n";
```