### swoole_server->after

#### Prototype

```php
int swoole_server->after(int $after_time_ms, mixed $callback_function)
```

#### Illustration

Trigger a one time tick in the future. Alias of function *swoole_timer_after()*. You can remove the timer later by calling `swoole_timer_clear`

앞으로 한 번 진드기를 발동하십시오. 함수의 별칭 * swoole_timer_after () *. `swoole_timer_clear`를 호출하여 나중에 타이머를 제거 할 수 있습니다.

#### Parameter

* `$time`	the number of millisecond
* `$callable` the function that triggered after with a fixed time delay

*`$ time` 밀리 세컨드 수
*`$ callable`은 고정 시간 지연으로 시작된 함수입니다.

#### Return

the timer id which uniquely identifies the timer

타이머를 일의에 식별하는 타이머 ID

#### Example
