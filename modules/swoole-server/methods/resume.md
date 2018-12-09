### swoole_server->resume

#### Prototype

```php
bool swoole_server->resume(int $fd)
```

#### Illustration

Resume the data receiving for the `$fd` client..

`$ fd` 클라이언트에 대한 데이터 수신을 재개하십시오.

> Only available in SWOOLE_BASE mode.

> SWOOLE_BASE 모드에서만 사용할 수 있습니다.

#### Parameter

* `$fd`	the id number of client

*`$ fd`는 클라이언트의 ID 번호입니다.

#### Return

the result of resuming 

다시 시작한 결과

#### Example
