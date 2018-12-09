### swoole_server->finish

#### Prototype

```php
swoole_server->finish(string $data)
```

#### Illustration

Used in task process for sending result to the worker process when the task is finished.

작업이 완료되면 작업 프로세스에 결과를 보내기위한 작업 프로세스에 사용됩니다.

#### Parameter

* `$data`	the data to send to the worker process

*`$ data`는 작업자 프로세스에 보낼 데이터입니다.

#### Return


#### Example
