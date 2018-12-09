### swoole_process::daemon

#### Prototype

```php
bool swoole_process->daemon(bool $nochdir = true, bool $noclose = true);
```

#### Illustration

Change the process to be a daemon process.

프로세스를 데몬 프로세스로 변경하십시오.

#### Parameter

* $nochdir: whether change the current path.

* $ nochdir : 현재 경로 변경 여부.

* $noclose: whether close the standard I/O of the process.

* $ noclose : 프로세스의 표준 I / O를 닫을 지 여부.

#### Return

bool
