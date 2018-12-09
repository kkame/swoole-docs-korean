### onShutdown

The event `shutdown` happens when the swoole server shutdowns.

swoole 서버가 종료되면 'shutdown'이벤트가 발생합니다.

Before the event `shutdown`, these operations below happened:

이벤트가 종료되기 전에 아래의 작업이 발생했습니다.

- All threads are closed.
- All the worker processed are closed.
- The listening on the TCP/UDP ports is closed.
- The Reactor is closed.

- 모든 스레드가 닫힙니다.
- 처리 된 모든 작업자가 닫힙니다.
- TCP / UDP 포트에서 청취가 닫힙니다.
- 원자로가 닫혔습니다.

> Kill the process forcibly, like `kill -9`, will not trigger the call of function registered for `shutdown`. It needs to send `SIGTREM` by `kill -15`

> 프로세스를 강제 종료 시키면`kill -9`처럼`shutdown`을 위해 등록 된 함수를 호출하지 않습니다. `kill -15`에 의해`SIGTREM`을 보내야합니다.

#### Example

```php
function onShutdown(swoole_server $server)
```
