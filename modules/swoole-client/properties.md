# Swoole TCP/UDP client

## Properties List

### Table of Contents

- swoole_client->errCode

- swoole_client->sock

- swoole_client->reuse

### swoole_client->errCode

When the call of method `connect/send/recv/close` failed, the value of `swoole_client->errCode` is setted automatically.

`connect / send / recv / close '메소드의 호출이 실패하면`swoole_client-> errCode`의 값이 자동으로 설정됩니다.

The value of `swoole_client->errCode` equals to the value of `errno` of Linux. You can use `socket_strerror` to check the concrete information of errCode.

`swoole_client-> errCode`의 값은 리눅스의`errno`의 값과 같습니다. `socket_strerror`를 사용하여 errCode의 구체적인 정보를 확인할 수 있습니다.

```php
echo socket_strerror($client->errCode);
```

### swoole_client->sock

It is an integer which stands for the file descriptor of socket.

socket의 파일 디스크립터를 나타내는 정수이다.

You can use this value to convert a stream socket used for `fread/fwrite/fclose` functions.

이 값을 사용하여`fread / fwrite / fclose` 함수에 사용되는 스트림 소켓을 변환 할 수 있습니다.

```php
$sock = fopen("php://fd/".$swoole_client->sock); 
```

### swoole_client->reuse

It is an Boolean value which stands for reuse status of socket.

소켓의 재사용 상태를 나타내는 부울 값입니다.

```php
if ($client->reuse)
{
    // reused socket
    $client->send($data);
}
else
{
    // new socket
    $client->doHandShake();
    $client->send($data);
}
```
