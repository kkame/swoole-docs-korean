### open_http2_protocol

Enable the process of http2 protocal.

http2 protocal의 프로세스를 사용 가능하게하십시오.

This configuration needs to compile swoole with `--enable-http2`

이 설정은`--enable-http2`로 swoole을 컴파일해야합니다.

#### Usage

```php
$serv->set(array('open_http2_protocol' => true));
```
