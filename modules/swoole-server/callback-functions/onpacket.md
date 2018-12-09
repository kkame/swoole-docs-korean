### onPacket

The event `packet` happens when the worker process recevice the UDP package.

'패킷'이벤트는 작업자 프로세스가 UDP 패키지를 수신 할 때 발생합니다.

The callback function registered for event `packet` is called in the process where the event happens.

이벤트`packet`에 대해 등록 된 콜백 함수는 이벤트가 발생하는 프로세스에서 호출됩니다.

#### Example

```php
function onPacket(swoole_server $server, string $data, array $client_info)
```

- `$data` the UDP package received

- UDP 패키지가받은`$ data`

- `$client_info`, this data is an array.

-`$ client_info`,이 데이터는 배열입니다.
    ```php
    Array                                                                                         
    (                                                                                             
     [server_socket] => 4                                                                      
     [server_port] => 9501                                                                 
     [address] => 127.0.0.1                                                            
     [port] => 47306                                                               
    )    
    ```

If the swoole server listens on TCP and UDP port, the callback function `onReceive` will be called when TCP data is received and the callback function `onPacket` will be called when UDP data is received.

서버가 TCP와 UDP 포트를 청취하면 TCP 데이터를 수신 할 때 콜백 함수`onReceive`가 호출되고 UDP 데이터가 수신되면 콜백 함수`onPacket`이 호출됩니다.


#### Data transformation

Transform the data to the `$fd` and `reactor_id` of callback function `onReceive`

데이터를 콜백 함수`onReceive`의`$ fd`와`reactor_id '로 변환하십시오.

```php
$fd = unpack('L', pack('N', ip2long($addr['address'])))[1];
$reactor_id = ($addr['server_socket'] << 16) + $addr['port'];
```
