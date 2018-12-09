### swoole_server->bind

#### Prototype

```php
bool swoole_server->bind(int $fd, int $uid)
```

#### Illustration

Bind the fd with system user UID.

fd를 시스템 사용자 UID로 바인드하십시오.

The dispatch of different socket connection to the swoole server is influenced by [the configuration of dispatch_mode](/modules/swoole-server/configuration/dispatch_mode.md)

스풀 서버에 대한 다른 소켓 연결의 발송은 [dispatch_mode의 구성] (/ modules / swoole-server / configuration / dispatch_mode.md)의 영향을받습니다.

In the default dispatch_mode which is 2, the socket connection may be dispatched to different worker process after reconnetion. You can set the configuration of dispatch_mode to 5 and call `swoole_server->bind` to bind a uid number to socket connection. And then the same uid socket connection will be dispatched to the same worker process.

기본 dispatch_mode가 2 인 경우 소켓 연결은 재설정 후 다른 작업자 프로세스로 전달 될 수 있습니다. dispatch_mode의 설정을 5로 설정하고`swoole_server-> bind`를 호출하여 uid 번호를 소켓 연결에 바인드 할 수 있습니다. 그런 다음 동일한 uid 소켓 연결이 동일한 작업자 프로세스에 전달됩니다.

#### Parameter

* `$fd`	the id number of client
* `$uid` the uid number binded for the client

*`$ fd`는 클라이언트의 ID 번호입니다.
*`$ uid`는 클라이언트에 바인드 된 uid 번호입니다.

#### Return

the result of binding

바인딩 결과

#### Example
