### open_mqtt_protocol

Enable the process of mqtt protocal.

mqtt protocal 프로세스를 활성화하십시오.

Once this configuration has enabled, the swoole will analyze the mqtt package head and the callback function `onReceive` will receive a whole mqtt package.

이 구성이 활성화되면 swoole이 mqtt 패키지 헤드를 분석하고 콜백 함수`onReceive`가 전체 mqtt 패키지를 수신합니다.

#### Usage

```php
$serv->set(array('open_mqtt_protocol' => true));
```
