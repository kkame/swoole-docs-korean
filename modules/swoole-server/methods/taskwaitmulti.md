### swoole_server->taskWaitMulti

#### Prototype

```php
array swoole_server->taskWaitMulti(array $tasks, double $timeout = 0.5)
```

#### Illustration

Execute multiple tasks concurrently

여러 작업을 동시에 실행

#### Parameter

* `$tasks`	the array of task data which is to send to the task worker, its type could any type except fot resource
* `$timeout`    the time of timeout 

*`$ tasks` 작업 작업자에게 보낼 작업 데이터의 배열입니다. 그 유형은 fot 자원을 제외한 모든 유형이 될 수 있습니다
*`$ timeout`은 타임 아웃 시간입니다.

#### Return

If the call of this method succeeds, the return is the array of the result of tasks
If the execution of some task exceeds the time of timeout, its result will not be in the return array

이 메서드의 호출이 성공하면 반환 값은 태스크 결과의 배열입니다.
어떤 작업의 실행이 시간 초과 시간을 초과하면 결과는 반환 배열에 포함되지 않습니다.

#### Example

```php
<?php
$tasks[] = mt_rand(1000, 9999); 
$tasks[] = mt_rand(1000, 9999); 
$tasks[] = mt_rand(1000, 9999); 
var_dump($tasks);

$results = $serv->taskWaitMulti($tasks, 10.0);

if (!isset($results[0])) {
    echo "Task 1: timeout.\n";
}
if (isset($results[1])) {
    echo "Task 2: {$results[1]}\n";
}
if (isset($results[2])) {
    echo "Task 3: {$results[2]}\n";
}
```
