### swoole_server->send

#### Prototype

```php
bool swoole_server->send(int $fd, string $data, int $extraData = 0)
```

#### Illustration

Send data to the remote TCP socket.

데이터를 원격 TCP 소켓으로 보냅니다.

* The max TCP data size is 2MB. This limit can be changed by configuring [the configuration of buffer_output_size](/modules/swoole-server/configuration/buffer_output_size.md)

* 최대 TCP 데이터 크기는 2MB입니다. 이 제한은 [buffer_output_size의 구성] (/ modules / swoole-server / configuration / buffer_output_size.md)을 구성하여 변경할 수 있습니다.

#### Parameter

* `$fd`	the id number of client
* `$data` the function that triggered after with a fixed time delay
* `$extraData` the extra data of sending data 

*`$ fd`는 클라이언트의 ID 번호입니다.
*`$ data`는 고정 된 시간 지연으로 시작된 함수입니다.
*`$ extraData`는 데이터를 보내는 여분의 데이터입니다.

#### Return

the result of send data to the client

If the result is false, you can call the method `$server->getLastError()` to get the error code.

클라이언트에 데이터를 보낸 결과

결과가 false 인 경우,`$ server-> getLastError ()`메소드를 호출하여 오류 코드를 얻을 수 있습니다.

#### Example
