# Swoole TCP/UDP client

## Methods 

### swoole_client->sleep

#### Prototype

```php
swoole_client->sleep();
```

#### Illustration

Remove the TCP client from system event loop.

시스템 이벤트 루프에서 TCP 클라이언트를 제거하십시오.

#### Parameter

void

#### Return

void

#### Example
```php
$client->on("receive", function(swoole_client $cli, $data){
    //sleep mode and stop receive data
    $cli->sleep();
    swoole_timer_after(5000, function() use ($cli) {
        // wakeup the client and start to receive data
        $cli->wakeup();
    });
});
```
