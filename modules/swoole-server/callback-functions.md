### Events List

The swoole is an an high-performance network framework uses an event-driven, asynchronous, non-blocking I/O model makes it scalable and efficient. All the business logic is written in the callback functions of events. When a certain event is triggered, the swoole will call the callback function registered for the event. 

강력한 네트워크 프레임 워크는 이벤트 중심의 비동기식 비 차단 I / O 모델을 사용하여 확장 가능하고 효율적입니다. 모든 비즈니스 로직은 이벤트의 콜백 함수로 작성됩니다. 특정 이벤트가 트리거되면 swoole은 이벤트에 대해 등록 된 콜백 함수를 호출합니다.

There are thirteen types of event listed in the below table of contents.

아래 목차에는 13 가지 유형의 이벤트가 나열되어 있습니다.

#### Table of Contents

 - [onStart](/modules/swoole-server/callback-functions/onstart.md)
 - [onShutdown](/modules/swoole-server/callback-functions/onshutdown.md)
 - [onWorkerStart](/modules/swoole-server/callback-functions/onworkerstart.md)
 - [onWorkerStop](/modules/swoole-server/callback-functions/onworkerstop.md)
 - [onTimer](/modules/swoole-server/callback-functions/ontimer.md)
 - [onConnect](/modules/swoole-server/callback-functions/onconnect.md)
 - [onReceive](/modules/swoole-server/callback-functions/onreceive.md)
 - [onPacket](/modules/swoole-server/callback-functions/onpacket.md)
 - [onClose](/modules/swoole-server/callback-functions/onclose.md)
 - [onBufferFull](/modules/swoole-server/callback-functions/onbufferfull.md)
 - [onBufferEmpty](/modules/swoole-server/callback-functions/onbufferempty.md)
 - [onTask](/modules/swoole-server/callback-functions/ontask.md)
 - [onFinish](/modules/swoole-server/callback-functions/onfinish.md)
 - [onPipeMessage](/modules/swoole-server/callback-functions/onpipemessage.md)
 - [onWorkerError](/modules/swoole-server/callback-functions/onworkererror.md)
 - [onManagerStart](/modules/swoole-server/callback-functions/onmanagerstart.md)
 - [onManagerStop](/modules/swoole-server/callback-functions/onmanagerstop.md)

#### Order of events

- All the callback functions of events are triggered after the start of swoole server.

- The last event of swoole server is `onShutdown` when the swoole server shutdowns.

- After starting the swoole server, the callback functions of `onStart/onManagerStart/onWorkerStart` are triggered in different process.

- 이벤트의 모든 콜백 기능은 스풀 서버가 시작된 후에 트리거됩니다.

- swoole 서버의 마지막 이벤트는 swoole 서버가 종료 될 때`onShutdown`입니다.

- swoole 서버를 시작한 후`onStart / onManagerStart / onWorkerStart` 콜백 함수가 다른 프로세스에서 실행됩니다.


#### Catch Exception

The swoole doesn't support the `set_exception_handler` function.

스톨은`set_exception_handler` 함수를 지원하지 않습니다.

If there is the logic of throwing exception in your code, it must add the `try/catch` in the very beginning of callback function.

코드에 예외를 throw하는 로직이 있다면, 콜백 함수의 시작 부분에`try / catch`를 추가해야합니다.

```php
$serv->on('Timer', function() {
    try
    {
        //some code
    }
    catch(Exception $e)
    {
        //exception code
    }
}
```

#### Example

Example of registering event callback functions:

이벤트 콜백 함수 등록의 예 :

```php
<?php
$server = new swoole_server("127.0.0.1", 9501, SWOOLE_BASE, SWOOLE_SOCK_TCP);
$server->on('WorkerStart', function($serv, $workerId) {
    var_dump(get_included_files());
});
```
