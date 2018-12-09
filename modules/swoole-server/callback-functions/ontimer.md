### onTimer

The event `timer` happens when the timer expires.

이벤트 '타이머'는 타이머가 만료 될 때 발생합니다.

#### Example

```php
function onTimer(swoole_server $server, int $interval);
```

`$interval` is the interval setted by the timer. You can distinguish the timer by the interval.

`$ interval '은 타이머에 의해 설정된 간격이다. 간격으로 타이머를 구별 할 수 있습니다.

The timer is added by the `$serv->addtimer`.

타이머는`$ serv-> addtimer`에 의해 추가됩니다.