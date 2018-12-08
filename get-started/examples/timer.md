## Create Timer

### Code example

`swoole_timer.php`

``` php
// Executes the setted function repeatedly, with a fixed time dalay between each call 
swoole_timer_tick(2000, function($timer_id){
	echo "tick 2000ms\n";
});

// Executes the setted function after specified delay
swoole_timer_after(3000, function(){
	echo "after 3000ms\n";
});
```

Swoole provides the async timer like the `setInterval/setTimeout` of Javascript which is in milliseconds.

Swoole은 Javascript의`setInterval / setTimeout`과 같은 비동기 타이머를 밀리 초 단위로 제공합니다.

- `swoole_timer_tick($time, $callable)` corresponds to the `setInterval` of Javascript which is called repeatedly

-`swoole_timer_tick ($ time, $ callable)`은 반복적으로 호출되는 Javascript의`setInterval`에 해당합니다

- `swoole_timer_after($time, $callable)` corresponds to the `setTimeout` of Javascript which is called after a specified time

-`swoole_timer_after ($ time, $ callable)`는 지정된 시간 후에 호출되는 Javascript의`setTimeout`에 해당합니다

-`swoole_timer_after`와`swoole_timer_tick`는이 타이머의 id를 나타내는 정수를 반환합니다

- `swoole_timer_after` and `swoole_timer_tick` return a integer which represents the id of this timer

- Use `swoole_timer_clear($timer_id)` to clear the timer

-`swoole_timer_clear ($ timer_id)`를 사용하여 타이머 지우기
