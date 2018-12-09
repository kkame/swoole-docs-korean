### open_eof_check

This configuration is to check the package eof. The package eof is setted by [the configuration package_eof](/modules/swoole-server/configuration/package_eof.md) 

이 구성은 패키지 eof를 확인하는 것입니다. 패키지 eof는 [configuration package_eof] (/ modules / swoole-server / configuration / package_eof.md)에 의해 설정됩니다.

#### Usage

If this configuration has been enabled, the swoole will check the end of data from the client. If the end of data from client is the string setted by `package_eof`, the swoole will send the data to the worker process otherwise the swoole will continue receive and joint the data from client.

이 구성을 사용하면 swoole이 클라이언트의 데이터 끝을 확인합니다. 클라이언트로부터의 데이터의 끝이`package_eof`에 의해 설정된 문자열이면, swoole은 작업자 프로세스로 데이터를 보내고, 그렇지 않으면 swoole은 클라이언트로부터 데이터를 수신하고 연결합니다.

```php
array(
	'open_eof_check' => true,
	'package_eof' => "\r\n", 
)
```
The above configuration example can be used for Memcache or POP protocal which ends by `\r\n`. Once setted, the worker process will receive one or serveral whole packages. In the worker process, you should use `explode("\r\n", $data)` split the data or set [the configuration package_eof](/modules/swoole-server/configuration/open_eof_split.md) to split the data automatically. 

위의 설정 예는 '\ r \ n'으로 끝나는 Memcache 또는 POP 프로토콜에 사용할 수 있습니다. 일단 설정되면, 작업자 프로세스는 하나 또는 전체 패키지를 수신하게됩니다. 작업자 프로세스에서는`explode ( "\ r \ n", $ data)`데이터를 분리하거나 [configuration package_eof] (/ modules / swoole-server / configuration / open_eof_split.md)를 설정하여 데이터를 분할해야합니다 자동으로
