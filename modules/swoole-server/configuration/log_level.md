### log_level

Set the level of log. 

로그 수준을 설정하십시오.

The log that is inferior to the log_level setted will not be recorded to log file.

설정된 log_level보다 못한 로그는 로그 파일에 기록되지 않습니다.

#### Usage

```php
$serv->set(array(
    'log_level' => 1,
));
```

#### Log level list

```
0 =>DEBUG // all the levels of log will be recorded
1 =>TRACE
2 =>INFO
3 =>NOTICE
4 =>WARNING
5 =>ERROR
```
