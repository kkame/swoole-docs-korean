### swoole_server->tick

#### Prototype

```php
int swoole_server->tick(int $time, mixed $callable)
```

#### Illustration

Trigger a timer tick by interval. Alias of function *swoole_timer_tick()*. You can remove the timer later by calling `swoole_timer_clear`

타이머 틱을 간격으로 트리거합니다. 함수의 별칭 * swoole_timer_tick () *. `swoole_timer_clear`를 호출하여 나중에 타이머를 제거 할 수 있습니다.

#### Parameter

* `$time`	the number of millisecond
* `$callable` the function that triggered repeatedly with a fixed time delay between each call

*`$ time` 밀리 세컨드 수
*`$ callable` 각 호출 사이에 고정 된 시간 지연으로 반복적으로 트리거 된 함수

#### Return

the timer id  which uniquely identifies the timer

타이머를 일의에 식별하는 타이머 ID

#### Example

Use the `swoole_server->tick` in onReceive

onReceive에서`swoole_server-> tick`을 사용하십시오.

```php
function onReceive($server, $fd, $from_id, $data) {
	$server->tick(1000, function() use ($server, $fd) {
		$server->send($fd, "hello world");
	});
}
```

Use the `swoole_server->tick` in onWorkerStart

onWorkerStart에서`swoole_server-> tick`을 사용하십시오.

```php
function onWorkerStart(swoole_server $serv, $worker_id)
{
	if (!$serv->taskworker) {
		$serv->tick(1000, function ($id) {
			var_dump($id);
		});
	} else {
		$serv->addtimer(1000);
	}
}
```
