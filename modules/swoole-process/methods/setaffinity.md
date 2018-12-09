### swoole_process::setaffinity

#### Prototype

```php
bool swoole_process->setaffinity(array $cpu_set);
```

#### Illustration

Set the CPU affinity of the process.

프로세스의 CPU 선호도를 설정하십시오.

#### Parameter

- `$cpu_set` the array of cpu number. Use `SWOOLE_CPU_NUM` to get the number of cpu. for example: array(0,2,3) stands for CPU0/CPU2/CPU3

-`$ cpu_set`는 cpu 번호의 배열입니다. `SWOOLE_CPU_NUM`을 사용하여 CPU의 수를 얻으십시오. 예 : array (0,2,3)는 CPU0 / CPU2 / CPU3을 나타냅니다.

#### Return

`true` : success, `false` : fail
