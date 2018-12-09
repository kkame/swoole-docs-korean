### swoole_server->reload

#### Prototype

```php
bool swoole_server->reload(bool $only_reload_taskworkrer = false)
```

#### Illustration

Gracefully restart all the worker processes and reload the PHP files.

정상적으로 모든 작업자 프로세스를 다시 시작하고 PHP 파일을 다시로드하십시오.

- The reload only works for the files included after `onWorkerStart` and `onReceive`, and not for the files included before the start of the swoole_server 
- The reload not works for the runtime setting of the swoole server. The runtime setting should be changed by the restart of swoole server

- 리로드는`onWorkerStart`와`onReceive` 이후에 포함 된 파일들에 대해서만 작동하며, swoole_server가 시작하기 전에 포함 된 파일들에 대해서는 작동하지 않습니다
- 리로드가 스풀 서버의 런타임 설정에 작동하지 않습니다. 스풀 서버를 다시 시작하여 런타임 설정을 변경해야합니다.

#### Parameter

* `$only_reload_taskworkrer` if the call of reload only reloads taskworkrer

*`$ only_reload_taskworkrer`는 재로드 호출이 taskworkrer 만 재로드하는 경우입니다.

#### Return

the result if it has been reloaded successfully 

결과가 성공적으로 다시로드 된 경우 결과

#### Example

Restart all the worker processes by signal

모든 작업자 프로세스를 신호로 다시 시작하십시오.

```bash
kill -USR1 MASTER_PID
```

Only restart the task processes by signal

신호로 태스크 프로세스를 재시작하십시오.

```bash
kill -USR2 MASTER_PID
```

Get all the files loaded before the worker started

작업자가 시작되기 전에로드 된 모든 파일 가져 오기

```php
<?php
$server->on('WorkerStart', function($serv, $workerId) {
    var_dump(get_included_files());
});
```

When using APC/OpCache

APC / OpCache를 사용할 때

* *stat* in APC/OpCache has to be enabled for code reload
* Refresh OpCache with apc_clear_cache() or opcache_reset() if necessary

* 코드 재로드를 위해 APC / OpCache의 * stat *를 활성화해야합니다.
* 필요한 경우 apc_clear_cache () 또는 opcache_reset ()을 사용하여 OpCache를 새로 고칩니다.