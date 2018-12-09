### swoole_server->shutdown

#### Prototype

```php
void swoole_server->shutdown()
```

#### Illustration

Shutdown the master server process, this function can be called in worker processes.

Shutdown server by system signal *SIGTERM*

마스터 서버 프로세스를 종료하면이 기능을 작업자 프로세스에서 호출 할 수 있습니다.

시스템 신호 별 서버 종료 * SIGTERM *

```bash
kill -15 MASTER_PID
```

#### Parameter

void

#### Return

void

#### Example
