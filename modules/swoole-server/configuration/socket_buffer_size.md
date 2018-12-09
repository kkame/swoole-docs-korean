### socket_buffer_size

Set the buffer size of socket.

소켓의 버퍼 사이즈를 설정합니다.

This configuration is to set the max memory size of connection. 

이 구성은 연결의 최대 메모리 크기를 설정하는 것입니다.

#### Usage

```php
$server->set([
    'socket_buffer_size' => 128 * 1024 *1024, //必须为数字
])
```
