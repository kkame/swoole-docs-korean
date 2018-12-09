### swoole_server->sendfile

#### Prototype

```php
bool swoole_server->sendfile(int $fd, string $filename, int $offset = 0, int $length = 0)
```

#### Illustration

Send large size data or files to the remote TCP socket. A wrapper of the *sendfile* system call.

큰 크기의 데이터 또는 파일을 원격 TCP 소켓으로 보냅니다. * sendfile * 시스템 호출의 랩퍼.

#### Parameter

* `$fd`	the id number of client
* `$filename` the path of file to send
* `$offset` the start offset of file to send. The default of this parameter is 0
* `$length` the length of file to send. The default of this parameter is the whole length of file

*`$ fd`는 클라이언트의 ID 번호입니다.
*`$ filename`은 보낼 파일의 경로입니다.
*`$ offset`은 보낼 파일의 시작 오프셋입니다. 이 매개 변수의 기본값은 0입니다.
*`$ length`는 보낼 파일의 길이입니다. 이 매개 변수의 기본값은 파일의 전체 길이입니다.

#### Return

the timer id which uniquely identifies the timer

타이머를 일의에 식별하는 타이머 ID

#### Example

```php
<?php
$server->sendfile($fd, __DIR__.'/test.jpg');
```
