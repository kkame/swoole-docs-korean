### onStart

When the swoole server starts, the event `start` happens and the swoole will call the callback function registered for `start` in the master process.

스풀 서버가 시작되면 이벤트`start`가 발생하고 스풀은 마스터 프로세스에서`start`를 위해 등록 된 콜백 함수를 호출합니다.

Before the `start` event, the swoole server has proceeded the below operations:

`start` 이벤트 전에, swoole 서버는 다음 작업을 진행했습니다 :

- Create the manager process
- Create the worker process
- Listen on the setted TCP/UDP Port
- Listen on the timer


- 관리자 프로세스 만들기
- 작업자 프로세스 만들기
- 설정된 TCP / UDP 포트 청취
- 타이머 듣기

After the `start` event, the reactor will receive event and the client can connect the server

`start` 이벤트 이후, 원자로는 이벤트를 수신하고 클라이언트는 서버를 연결할 수 있습니다

In the callback function registered for `start`, it only allows to log record and modify the name of process. 

`start`에 등록 된 콜백 함수에서는 기록을 남기고 프로세스 이름 만 수정할 수 있습니다.

The event `start` and `workerstart` happen concurrently in different processes and have no precedence.

이벤트`start`와`workerstart`는 다른 프로세스에서 동시에 일어나며 우선 순위가 없습니다.

It is recommended to record the value of `$serv->master_pid` and `$serv->manager_pid` into file. If so, you can wirte script to send signal to control the process.

$ serv-> master_pid와 $ serv-> manager_pid의 값을 파일에 기록하는 것이 좋습니다. 그렇다면 스크립트를 사용하여 프로세스를 제어하는 신호를 보낼 수 있습니다.

#### Example

```php
function onStart(swoole_server $server){

}
```
