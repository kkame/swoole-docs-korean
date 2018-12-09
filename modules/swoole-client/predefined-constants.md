# Swoole TCP/UDP client

## Constants List

### swoole_client::MSG_WAITALL

This constant is used in the second parameter of method `swoole_client->recv`. It means that the swoole client will not return untill received the data of specified length.

이 상수는`swoole_client-> recv` 메소드의 두 번째 매개 변수에서 사용됩니다. 이는 swoole 클라이언트가 지정된 길이의 데이터를 수신 할 때까지 리턴하지 않는다는 것을 의미합니다.

```php
$client->recv(8192, swoole_client::MSG_PEEK | swoole_client::MSG_WAITALL);
```

### swoole_client::MSG_DONTWAIT

Receive the data in non-blocking mode.

비 차단 모드에서 데이터를 수신하십시오.

### swoole_client::MSG_PEEK

If this constant has been added to the parameter, the recv of client will not change the pointer of recv data and read data from the same offset in next time.

이 상수가 매개 변수에 추가 된 경우 클라이언트의 recv는 다음 번에 recv 데이터의 포인터를 변경하지 않고 동일한 오프셋에서 데이터를 읽지 않습니다.

### swoole_client::MSG_OOB

Receive the out-of-band data.

대역 외 데이터를 수신합니다.