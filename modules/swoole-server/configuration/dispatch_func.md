### dispatch_func

Set the `dispatch_func` to dispatch the connection to the worker process.

작업자 프로세스에 연결을 디스패치하기 위해`dispatch_func`를 설정하십시오.

The swoole server provides [five types of `dispatch_mode`](/modules/swoole-server/configuration/dispatch_mode.md). If the `dispatch_mode` can't meet your need, you can write C++ function or PHP function to realize customized dispatch strategy. 

스풀 서버는 다섯 종류의`dispatch_mode` (/ modules / swoole-server / configuration / dispatch_mode.md)를 제공합니다. `dispatch_mode`가 당신의 필요를 충족시킬 수 없다면 C ++ 함수 나 PHP 함수를 작성하여 사용자 정의 된 디스패치 전략을 실현할 수 있습니다.

#### Usage 

```php
$serv->set(array(
    'dispatch_func' => 'my_dispatch_function',
));
```
> Once the `dispatch_func` has been setted, the configuration `dispatch_mode` would not work.

> 일단`dispatch_func`가 설정되면,`dispatch_mode` 설정은 작동하지 않을 것입니다.

> If the function setted by `dispatch_func`, the swoole will result in a fatal error.

> 함수가`dispatch_func`에 의해 설정되면, swoole은 치명적인 에러를 발생시킵니다.

> If the data dispatched is more than 8K, `dispatch_func` can get 0-8180 bytes data. 

> 발송 된 데이터가 8K 이상이면`dispatch_func`는 0-8180 바이트의 데이터를 얻을 수 있습니다.

#### PHP function

> It is forbidden to add any blocking operation in the `dispatch_func` otherwise the `Reactor` group would stop.

>`dispatch_func`에 블로킹 연산을 추가하는 것은 금지되어 있습니다. 그렇지 않으면`Reactor` 그룹이 멈출 것입니다.

```php
$serv->set(array(
    'dispatch_func' => function ($serv, $fd, $type, $data) {
        var_dump($fd, $type, $data);
        return intval($data[0]);
    },
));
```
Parameters:

 - `$fd`, the id number of client

 - `$type`, the type of data, `0`: receive data from the client, `4`: the connection with the client closes, `5`: the connection with the client starts

 - `$data`, the data to dispatch

Return:

the return must be a integer between 0 and `worker_num`

매개 변수 :

  -`$ fd`, 클라이언트의 id 번호

  -`$ type`은 데이터 타입,`0`은 클라이언트로부터 데이터 수신,`4`는 클라이언트와의 연결 종료,`5`는 클라이언트와의 연결 시작

  - '$ data`, 디스패치 할 데이터

반환:

반환 값은 0과`worker_num` 사이의 정수 여야합니다.

#### C++ function

In other extension, use `swoole_add_function` to register function to swoole

다른 확장 기능에서는 swoole에 함수를 등록하기 위해`swoole_add_function`을 사용하십시오

```c++
int dispatch_function(swServer *serv, swConnection *conn, swEventData *data);

int dispatch_function(swServer *serv, swConnection *conn, swEventData *data)
{
    printf("cpp, type=%d, size=%d\n", data->info.type, data->info.len);
    return data->info.len % serv->worker_num;
}

int register_dispatch_function(swModule *module)
{
    swoole_add_function("my_dispatch_function", (void *) dispatch_function);
}
```
