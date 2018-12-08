# Swoole Channel

Memory data structure likes Chan in Golang, implemented based on shared memory and Mutex locks. It can be used as high performance message queue in memory. 

Chan in Golang, 공유 메모리 및 뮤텍스 잠금을 기반으로합니다. 메모리의 고성능 메시지 대기열로 사용될 수 있습니다.

* Don't have to warry about data synchronization issues when use swoole channel in multiple processes
* Swoole Channel has to be created in the parent process, and to be used in the child processes

* 여러 프로세스에서 스풀 채널을 사용할 때 데이터 동기화 문제를 걱정할 필요가 없습니다.
* 스몰 채널은 부모 프로세스에서 생성되어야하며 자식 프로세스에서 사용되어야합니다.

### Example

``` php
<?php
$chan = new Swoole\Channel(1024 * 256);
$n = 100000;
$bytes = 0;
if (pcntl_fork() > 0)
{
    echo "Parent process\n";
    for ($i = 0; $i < $n; $i++)
    {
        $data = str_repeat('A', rand(100, 200));
        if ($chan->push($data) === false)
        {
            echo "The channel is full\n";
            usleep(1000);
            $i--;
            continue;
        }
        $bytes += strlen($data);
    }
    echo "Total pushed data size: $bytes bytes\n";
    var_dump($chan->stats());
}
else
{
    echo "Child process\n";
    for ($i = 0; $i < $n; $i++)
    {
        $data = $chan->pop();
        if ($data === false)
        {
            echo "The channel is empty\n";
            usleep(1000);
            $i--;
            continue;
        }
        $bytes += strlen($data);
    }
    echo "Total popped data size: $bytes bytes\n";
    var_dump($chan->stats());
}
```

### Methods

#### swoole_channel->__construct(int $size);

Construct a swoole channel with fixed size.

* The minimum size of a swoole channel is 64KB.
* Exceptions will be thrown if there is not enough memory.

#### swoole_channel->push(mixed $data);

Write and push data into swoole channel.

* Data can be any non-empty PHP variable, the variable will be serialized if it is not string type.
* If size of the data is more than 8KB, swoole channel will use temp files storage.
* The function will return true if the write operation is succeeded, or return false if there is not enough space.

#### swoole_channel->pop();

Read and pop data from swoole channel.

* If the channel is empty, the function will return false, or return the unserialized data.

#### swoole_channel->stats();

Get stats of swoole channel: the numbers of queued elements and total size of the memory used by the queue:

```php
<?php
array(
  "queue_num" => 10,
  "queue_bytes" => 161,
);
```
