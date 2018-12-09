### swoole_server->defer

#### Prototype

```php
void swoole_server->defer(callable $callback)
```

#### Illustration

Delay execution of the callback function at the end of current *EventLoop*. Alias of function *swoole_event_defer()*.

현재 * EventLoop *의 끝에서 콜백 함수의 실행을 지연시킵니다. 함수의 별칭 * swoole_event_defer () *.

#### Parameter

* `$callback` the function that defers to execute

*`$ callback`은 실행을 연기하는 함수입니다.

#### Return

void

#### Example

```php
function query($server, $db) {
	$server->defer(function() use ($db) {
		$db->close();
	});
}
```
