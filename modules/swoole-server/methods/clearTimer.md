### swoole_server->clearTimer

#### Prototype

```php
void swoole_server->clearTimer(int $timer_id)
```

#### Illustration

Cancel the timer tick or one time tick. Alias of function *swoole_timer_clear*.

타이머 틱 또는 한 번 틱을 취소하십시오. 함수의 별칭 * swoole_timer_clear *.

#### Parameter

* `$timer_id`	the number of timer id which uniquely identifies a timer

*`$ timer_id` 타이머를 고유하게 식별하는 타이머 id의 번호

#### Return

 void

#### Example
```php
$timer_id = $server->tick(1000, function ($id) use ($server) {
    $server->clearTimer($id);
});
```
