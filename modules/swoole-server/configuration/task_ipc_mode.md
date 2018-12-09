### task_ipc_mode

Set the communication mode between the task worker process and worker process.

- `1`, default mode, use unix socket to communicate

- `2`, use the message queue to communicate

- `3`, use the message queue to communicate and set the mode to competition

> the difference between mode `2` and `3` : mode `2` supports the feature of sending task to a specified task worker process by `$serv->task($data, $task_worker_id)` while the mode `3` don't support to specify task worker process.

The message queue uses the memory queue provided by os to store the data. 

If [the configuration mssage_queue_key](/modules/swoole-server/configuration/message_queue_key.md) hasn't been seted, the message queue would use the private queue and this private queue would been deleted after the close of swoole server.

If [the configuration mssage_queue_key](/modules/swoole-server/configuration/message_queue_key.md) has been seted, the data of message queue would not be deleted and the swoole server could get the data after restart.

Use `ipcrm -q message_queue_id` to delete the data of message queue

작업 작업자 프로세스와 작업자 프로세스 사이의 통신 모드를 설정하십시오.

-`1`, 디폴트 모드, 통신을 위해 유닉스 소켓 사용

-`2`는 메시지 큐를 사용하여 통신합니다.

-`3`, 메시지 대기열을 사용하여 통신하고 경쟁 모드로 설정하십시오

> 모드 2와 모드 3의 차이 : 모드 2는 모드 3 인 동안`$ serv-> task ($ data, $ task_worker_id) '에 의해 지정된 작업 작업자 프로세스로 태스크를 보내는 기능을 지원한다. 작업 작업자 프로세스를 지정하도록 지원하지 않습니다.

메시지 대기열은 os가 제공 한 메모리 대기열을 사용하여 데이터를 저장합니다.

[구성 mssage_queue_key] (/ modules / swoole-server / configuration / message_queue_key.md)가 설정되지 않은 경우 메시지 대기열은 개인 대기열을 사용하고이 개인 대기열은 스풀 서버가 닫힌 후에 삭제됩니다.

[구성 mssage_queue_key] (/ modules / swoole-server / configuration / message_queue_key.md)가 설정되어 있으면 메시지 대기열의 데이터가 삭제되지 않고 다시 시작한 후 스풀 서버가 데이터를 가져올 수 있습니다.

메시지 큐의 데이터를 지우려면`ipcrm -q message_queue_id '를 사용하십시오.
