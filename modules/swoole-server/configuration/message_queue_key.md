### message_queue_key

Set the key of message queue.

메시지 큐의 키를 설정합니다.

This configuration only works if [the configuration of task_ipc_mode](/modules/swoole-server/configuration/task_ipc_mode.md) has been setted to `2` or `3`.

이 구성은 [task_ipc_mode의 구성] (/ modules / swoole-server / configuration / task_ipc_mode.md)이 '2'또는 '3'으로 설정된 경우에만 작동합니다.

The default value of `message_queue_key` is calculated by `ftok($php_script_file, 1)`.

`message_queue_key`의 기본값은`ftok ($ php_script_file, 1)`에 의해 계산됩니다.
