### max_request

the number of max request the worker process could receive.

작업자 프로세스가 수신 할 수있는 최대 요청 수.

The dafault value of `max_request` is 0 which means there is no limit of the max request. If the `max_request` is setted to some number, the worker process will exit and release all the memory amd resouce occupied by this process after receiving the `max_request` request. And then, the manager will respawn a new worker process.

`max_request`의 dafault 값은 0이며 이는 최대 요청의 제한이 없음을 의미합니다. `max_request`가 어떤 숫자로 설정되면, worker 프로세스는`max_request` 요청을받은 후에이 프로세스가 점유하고있는 모든 메모리와 자원을 종료하고 해제합니다. 그런 다음 관리자가 새 작업자 프로세스를 다시 생성합니다.

This parameter is to resolve the problem of nonlocalizable and slow memory leak.

이 매개 변수는 지역화 할 수없고 느린 메모리 누수 문제를 해결합니다.

> `max_request` only works for synchronous, blocking and stateless reponse program
> The totally asynchronous server should not set `max_request`
> `max_request` only works for `SWOOLE_PROCESS` mode.

>`max_request`는 동기식, 블로킹 및 stateless 응답 프로그램에서만 작동합니다
> 완전히 비동기적인 서버는`max_request`를 설정해서는 안됩니다.
>`max_request`는`SWOOLE_PROCESS` 모드에서만 작동합니다.

```php
<?php
$serv = new swoole_server("127.0.0.1", 9501);
$serv->set(array(
            'worker_num' => 2,    
            'max_request' => 3,  
            'dispatch_mode'=>3,
));

$serv->on('receive', function ($serv, $fd, $from_id, $data) {
        $serv->send($fd, "Server: ".$data);
});

$serv->start();
```
Check the pid of worker process before request and after many times request.

요청 전에 여러 번 요청한 후 작업자 프로세스의 PID를 확인하십시오.
