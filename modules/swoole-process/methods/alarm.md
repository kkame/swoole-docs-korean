### swoole_process::alarm

#### Prototype

```php
bool swoole_process->alarm(int $interval_usec, int $type = ITIMER_REAL)
```

#### Illustration

High precision timer which will trigger signal every fixed interval.

고정 된 간격마다 신호를 트리거하는 고정밀 타이머.

#### Parameter

- `$interval_usec`

- `$type`

#### Return

bool

#### Example
```php
<?php
swoole_process::signal(SIGALRM, function () {
    static $i = 0;
    echo "#{$i}\talarm\n";
    $i++;
    if ($i > 20) {
        swoole_process::alarm(-1);
    }
});

//100ms
swoole_process::alarm(100 * 1000);
```
