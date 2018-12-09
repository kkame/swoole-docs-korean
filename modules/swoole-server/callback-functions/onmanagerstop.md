### onManagerStop

The event `managerstop` happens when the manager process stops.

`managerstop` 이벤트는 매니저 프로세스가 멈 추면 발생합니다.

The callback function registered for event `managerstop` is called in the manager process.

`managerstop` 이벤트에 등록 된 콜백 함수는 매니저 프로세스에서 호출됩니다.
#### Example

```
void onManagerStop(swoole_server $serv);
```
