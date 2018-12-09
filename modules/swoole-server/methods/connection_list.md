### swoole_server->connection_list

#### Prototype

```php
mixed swoole_server->connection_list(int $start_fd = 0, int $pagesize = 10)
```

#### Illustration

Get the list of all the TCP connections for all the workers.

모든 작업자에 대한 모든 TCP 연결 목록을 가져옵니다.

> this method is besed on the shared memory and is fast.

>이 방법은 공유 메모리에 저장되며 빠릅니다.

#### Parameter

* `$start_fd`	the start id number of client list
* `$pagesize`   the pagesize of list

*`$ start_fd` 클라이언트리스트의 시작 ID 번호
*`$ pagesize`는 목록의 페이지 크기입니다.

#### Return

the array list of the `$fd` client 

if fail, the result is false 

`$ fd` 클라이언트의 배열리스트

실패 할 경우 결과는 false입니다.

#### Example

```php
<?php
$start_fd = 0;
while(true)
{
    $conn_list = $serv->connection_list($start_fd, 10);
    if($conn_list===false or count($conn_list) === 0)
    {
        echo "finish\n";
        break;
    }
    $start_fd = end($conn_list);
    var_dump($conn_list);
    foreach($conn_list as $fd)
    {
        $serv->send($fd, "broadcast");
    }
}
```
