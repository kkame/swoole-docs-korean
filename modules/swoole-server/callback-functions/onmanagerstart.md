### onManagerStart

The event `managerstart` happens when the manager process starts.

`managerstart` 이벤트는 매니저 프로세스가 시작될 때 발생합니다.

The callback function registered for event `managerstart` is called in the manager process.

`managerstart` 이벤트에 등록 된 콜백 함수는 매니저 프로세스에서 호출됩니다.

#### Example

```
void onManagerStart(swoole_server $serv);
```
