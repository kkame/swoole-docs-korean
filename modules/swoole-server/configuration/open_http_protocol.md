### open_http_protocol

Enable the process of http protocal.

http protocal의 프로세스를 사용 가능하게하십시오.

Once this configuration has enabled, the callback function `onReceive` will receive a whole http package.

이 구성이 활성화되면, 콜백 함수`onReceive`는 전체 http 패키지를받습니다.

The swoole_http_server will enable this configuration automatically.

swoole_http_server는이 구성을 자동으로 활성화합니다.

#### Usage

```php
$serv->set(array('open_http_protocol' => true));
```
