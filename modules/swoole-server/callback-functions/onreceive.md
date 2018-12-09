### onReceive

The event `receive` happens when the worker process receives the data.

'수신'이벤트는 작업자 프로세스가 데이터를 수신 할 때 발생합니다.

The callback function registered for the event `receive` will be called in the worker process which has received the data.

'receive'이벤트에 등록 된 콜백 함수는 데이터를받은 작업자 프로세스에서 호출됩니다.

#### Example

```php
function onReceive(swoole_server $server, int $fd, int $reactor_id, string $data)
```

- `$server` the swoole server object

- `$fd` If the swoole server is in TCP mode, it's the id number of client. If the swoole server is in UDP mode, it's the value of client ip which has been calculated by some algorithm. 

- `$reactor_id` If the swoole server is in TCP mode, it's the id number of reactor thread. If the swoole server is in UDP mode, it's the value of client port which has been calculated by some algorithm.

- `$data` the data received from the client. If the configurations about automatic protocal hasn't been setted, the max length of data that worker process could receive is 64KB.

For the TCP mode, the data translated between client and server flows and has no boundary. It needs to set the configurations(eof_check/length_check/http_protocol) about spliting the data into package or process the data into package manually. 


-`$ server`는 swoole 서버 객체입니다.

-`$ fd` swoole 서버가 TCP 모드 인 경우 클라이언트의 ID 번호입니다. 스풀 서버가 UDP 모드 인 경우 일부 알고리즘에 의해 계산 된 클라이언트 IP의 값입니다.

-`$ reactor_id` 스풀 서버가 TCP 모드이면 reactor thread의 id 번호입니다. swoole 서버가 UDP 모드 인 경우 일부 알고리즘에 의해 계산 된 클라이언트 포트의 값입니다.

-`$ data`는 클라이언트로부터받은 데이터입니다. 자동 프로토콜에 대한 구성이 설정되지 않은 경우 작업자 프로세스가 수신 할 수있는 최대 데이터 길이는 64KB입니다.

TCP 모드의 경우 클라이언트와 서버간에 변환 된 데이터가 흐르고 경계가 없습니다. 데이터를 패키지로 분할하거나 수동으로 데이터를 패키지로 처리하는 방법에 대한 설정 (eof_check / length_check / http_protocol)을 설정해야합니다.
