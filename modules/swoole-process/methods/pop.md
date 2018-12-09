### swoole_process->pop

#### Prototype

```php
string swoole_process->pop(int $maxsize = 8192);
```

#### Illustration

Read and pop data from the message queue.

메시지 대기열에서 데이터를 읽고 팝합니다.

#### Parameter

- `$maxsize` the max size of data to read from the message queue

-`$ maxsize`는 메시지 대기열에서 읽을 데이터의 최대 크기입니다.

#### Return

if failed, it returns `false`. Or it returns the data.

In the blocking mode, if the queue is empty, the call of this method will block.

In the non-blocking mode, if the queue is empty, the call of this method will return `false` immediately and set the error code to `ENOMSG`.

실패하면`false`를 반환합니다. 또는 데이터를 반환합니다.

블로킹 모드에서 큐가 비어 있으면이 메서드의 호출이 차단됩니다.

비 블로킹 모드에서 큐가 비어 있으면이 메소드를 호출하면 즉시 false가 반환되고 오류 코드는 ENOMSG로 설정됩니다.
