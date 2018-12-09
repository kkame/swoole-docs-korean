### swoole_process::signal

#### Prototype

```php
bool swoole_process->signal(int $signo, callable $callback);
```

#### Illustration

Setup signal callback function.

설정 신호 콜백 기능.

#### Parameter

- `$signo` the signal 

- `$callback` the callback function called when the signal is triggered

-`$ signo '신호

-`$ callback` 신호가 트리거 될 때 호출되는 콜백 함수

#### Return

bool
