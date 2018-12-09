### chroot

Redirect the root path of worker process.

작업자 프로세스의 루트 경로를 리디렉션합니다.

This configuration is to separate the operation to the file system in the worker process from the real file system.

이 구성은 실제 파일 시스템에서 작업자 프로세스의 파일 시스템으로 작업을 분리하는 것입니다.

#### Usage

```php
$serv->set(array('chroot' => '/data/server/'));
```
