### open_websocket_protocol

Enable the process of websocket protocal.

websocket protocal의 프로세스를 활성화하십시오.

The swoole  will enable this configuration `open_http_protocol` automatically if the configuration `open_websocket_protocol` has been enabled.

swoole은 'open_websocket_protocol` 설정이 활성화되어 있다면이 설정을`open_http_protocol` 자동으로 가능하게 할 것입니다.

The swoole_websocket_server will enable this configuration automatically.

swoole_websocket_server는이 구성을 자동으로 활성화합니다.

#### Usage

```php
$serv->set(array('open_websocket_protocol' => true));
```
