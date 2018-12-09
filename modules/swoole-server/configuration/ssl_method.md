## Configuration 

#### ssl_method

Set the algorithm of ssl. The algorithm of client and server must be same otherwise the handshake of websocket will fail.
The default algorithm is `SWOOLE_SSLv23_METHOD`

ssl의 알고리즘을 설정하십시오. 클라이언트와 서버의 알고리즘은 동일해야합니다. 그렇지 않으면 websocket의 핸드 셰이크가 실패합니다.
디폴트의 알고리즘은`SWOOLE_SSLv23_METHOD`입니다.

```php
$server->set(array(
    'ssl_method' => SWOOLE_SSLv3_CLIENT_METHOD, // this configuration is available for the swoole whose version is higher than 1.7.20
));
```
