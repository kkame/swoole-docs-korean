### onWorkerStart

The event `workerstart` happens when the worker process or task worker process starts.

'workerstart'이벤트는 작업자 프로세스 또는 작업 작업자 프로세스가 시작될 때 발생합니다.

According to the value of `$worker_id`, if `$worker_id>= $serv->setting['worker_num'] `, the worker is a task worker process otherwise it is a worker process.

`$ worker_id> = $ serv-> setting [ 'worker_num']`이면 $ worker_id의 값에 따라 작업자 프로세스는 작업자 프로세스입니다. 그렇지 않으면 작업자 프로세스입니다.

> There is no relation between `worker_id` and pid of process.

> 'worker_id'와 프로세스의 PID는 관계가 없습니다.

#### Example

```php
function onWorkerStart(swoole_server $server, int $worker_id)
```

#### Usage 

```php
$serv->on('WorkerStart', function ($serv, $worker_id){
    global $argv;
    if($worker_id >= $serv->setting['worker_num']) {
        swoole_set_process_name("php {$argv[0]} task worker");
    } else {
        swoole_set_process_name("php {$argv[0]} event worker");
    }
});
```
