# Swoole scheduler

The swoole server provides the methods `swoole_server->tick` and `swoole_server->after` to realize the asynchronous timer. For the swoole client, the swoole also provides the functions to realize the asynchronous timer. These schedule functions are accurate to milliseconds.

swoole 서버는 비동기 타이머를 실현하기 위해`swoole_server-> tick` 및`swoole_server-> after` 메소드를 제공합니다. swoole 클라이언트의 경우 swoole은 비동기 타이머를 구현하는 기능도 제공합니다. 이러한 일정 기능은 밀리 초까지 정확합니다.

The swoole timer is based on timerfd and epoll.

swoole 타이머는 timerfd와 epoll을 기반으로합니다.

## Methods

### int swoole_timer_tick(int $duration_ms, callable $callback, mixed $param = NULL);

Trigger a timer tick by interval.

타이머 틱을 간격으로 트리거합니다.

#### Parameter

* `$duration_ms`	the number of millisecond
* `$callback`       the callback function called repeatedly with a fixed time delay between each call. The callback will be passed two arguments : 
                        `$timer_id` : id of timer which can be used to clear this timer using `swoole_timer_clear`
                        `$param` : the param passed in `swoole_timer_tick` 
* `$param`          the param passed to the callback

*`$ duration_ms` 밀리 세컨드 수
*`$ callback` 콜백 함수는 각 호출 사이에 일정한 시간 지연을두고 반복적으로 호출됩니다. 콜백은 두 개의 인수를 전달하려고합니다.
                         `$ timer_id` :`swoole_timer_clear`를 사용하여이 타이머를 지우는 데 사용할 수있는 타이머의 ID입니다.
                         `$ param` :`swoole_timer_tick`에 전달 된 매개 변수
*`$ param`은 콜백에 전달 된 매개 변수입니다.

#### Return

the timer id

타이머 ID

#### Example

``` php
<?php
function test($timerid, $param)
{
    var_dump($timerid);
    var_dump($param);
}
swoole_timer_tick(1500, "test",["param1", "param2"]);
```

### swoole_timer_after(int $after_duration_ms, callable $callback, mixed $param = NULL);

Trigger a one time callback function in the future.

앞으로 일회성 콜백 함수를 트리거하십시오.

#### Parameter

* `$after_duration_ms`	the number of millisecond
* `$callback`           the callback function called after a setted time. The callback will be passed an arguments : 
                        `$param` : the param passed in `swoole_timer_tick` 
* `$param`          the param passed to the callback

*`$ after_duration_ms` 밀리 세컨드 수
*`$ callback` 콜백 함수는 설정된 시간 후에 호출됩니다. 콜백은 인수로 전달되기를 원한다.
                         `$ param` :`swoole_timer_tick`에 전달 된 매개 변수
*`$ param`은 콜백에 전달 된 매개 변수입니다.

#### Return

the timer id

타이머 ID

#### Example

``` php
<?php
function test($param)
{
    var_dump(func_get_args());
    var_dump($param);
}

swoole_timer_after(1500, "test",["param1", "param2"]);
```

### boolean swoole_timer_clear($timer_id);

Cancel the timer tick or one time tick. Alias of function *swoole_timer_clear*.

타이머 틱 또는 한 번 틱을 취소하십시오. 함수의 별칭 * swoole_timer_clear *.

#### Parameter

* `$timer_id`	the id of timer

*`$ timer_id`는 타이머의 id입니다.

#### Return

bool

#### Example

``` php
<?php
$count = 0;
function test($timerid, $param)
{
    global $count;
    $count++;
    var_dump($count);
    if($count >= 10)
    {
        swoole_timer_clear($timerid);
    }
}

swoole_timer_tick(1000, "test",["param1", "param2"]);
```
