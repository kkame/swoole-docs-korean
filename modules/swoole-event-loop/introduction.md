# Swoole EventLoop

Developers can use swoole EventLoop API to use the system EventLoop.

개발자는 EventLoop 시스템을 사용하기 위해 Swoole EventLoop API를 사용할 수 있습니다.

## Methods

### bool swoole_event_add(int $sock, mixed $read_callback, mixed $write_callback = null, int $flags = null);

Add new callback functions of a socket into the EventLoop.

EventLoop에 소켓에 새로운 콜백 함수를 추가하십시오.

Example:

예제 :

```php
<?php
$fp = stream_socket_client("tcp://www.qq.com:80", $errno, $errstr, 30);
fwrite($fp,"GET / HTTP/1.1\r\nHost: www.qq.com\r\n\r\n");

swoole_event_add($fp, function($fp) {
    $resp = fread($fp, 8192);
    // Remove the socket from eventloop
    swoole_event_del($fp);
    fclose($fp);
});
echo "Finish\n";
```

### bool swoole_event_set($fd, mixed $read_callback, mixed $write_callback, int $flags);

Update the event callback functions of a socket.

소켓의 이벤트 콜백 함수를 업데이트하십시오.

### bool swoole_event_del(int $sock);

Remove all event callback functions of a socket.

소켓의 모든 이벤트 콜백 함수를 제거하십시오.

### void swoole_event_exit()

Exit the eventloop, only available at client side.

이벤트 루프를 종료하십시오. 클라이언트 측에서만 사용할 수 있습니다.

### void swoole_event_wait(void);

### swoole_event_write($fp, $data);

Write data to the socket.

데이터를 소켓에 씁니다.

Example:

예제 :

```php
<?php
$fp = stream_socket_client('tcp://127.0.0.1:9501');
$data = str_repeat('A', 1024 * 1024*2);

swoole_event_add($fp, function($fp) {
     echo fread($fp);
});

swoole_event_write($fp, $data);
```

### swoole_event_defer(mixed $callback_function);

Add callback function to the next event loop.

콜백 함수를 다음 이벤트 루프에 추가하십시오.

Example:

예제 :

```php
<?php
swoole_event_defer(function(){
    echo "After EventLoop\n";
});
```
