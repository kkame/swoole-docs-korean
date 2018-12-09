### dispatch_mode

The mode of dispatching connections to worker process.

작업자 프로세스에 연결을 디스패치하는 모드입니다.

This parameter only works for the `SWOOLE_PROCESS` mode swoole_server.

이 매개 변수는`SWOOLE_PROCESS` 모드 swoole_server에서만 작동합니다.

- `1`, polling mode. Dispatch the connection to the workers in sequence.

- `2`, fixed mode(default value of `dispatch_mode`). Dispatch the connection to the worker according to the id number of connection. In this mode, the data from the same connection will be handled by the same worker process. 

- `3`, preemptive mode. The swoole will dispatch the connection to the unoccupied worker process.

- `4`, ip mode. Dispatch the connection to the worker according to the ip of client. The dispatch algorithm is `ip2long(ClientIP) % worker_num`

- `5`, uid mode. If the connection has been bound with a uid by [swoole_server->bind](/modules/swoole-server/methods/bind.md), the swoole will dispatch the connection to the worker according to the uid. The dispatch algorithm is `UID % worker_num`. If you want to use a string as a uid, it should convert this string by `crc32($uid)`

- `1`, 폴링 모드. 작업자와의 연결을 순차적으로 전달합니다.

- `2`, 고정 모드 (`dispatch_mode`의 기본값). 연결 ID 번호에 따라 작업자에게 연결을 전송합니다. 이 모드에서 동일한 연결의 데이터는 동일한 작업자 프로세스에 의해 처리됩니다.

- `3`, 선점 모드. 스톨은 비어있는 작업자 프로세스에 연결을 전달합니다.

- `4`, ip 모드. 클라이언트의 ip에 따라 작업자에게 연결을 전달합니다. 디스패치 알고리즘은`ip2long (ClientIP) % worker_num`입니다.

- `5`, 사용자 모드. 연결이 [swoole_server-> bind] (/ modules / swoole-server / methods / bind.md)에 의해 uid로 바인드 된 경우 swoole은 uid에 따라 작업자에게 연결을 전달합니다. 파견 알고리즘은`UID % worker_num`입니다. 문자열을 uid로 사용하려면이 문자열을`crc32 ($ uid)`로 변환해야합니다.

#### Usage advice

- stateless server: `3` is advised for synchronous and blocking server, `1` is advised for asynchronous and non-blocking server

- 무 상태 서버 : 동기 및 차단 서버는`3 ', 비동기 및 비 차단 서버는`1'을 권고한다.

- stateful server: `2`, `4`, `5`

- 상태 저장 서버 : '2', '4', '5'

> If the `dispatch_mode` is `1` or `3`, the event of `connect` and `close` will be shielded.

> 만약`dispatch_mode`가`1` 또는`3`이라면`connect`와`close` 이벤트가 차폐됩니다.