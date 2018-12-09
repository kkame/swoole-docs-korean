### task_tmpdir

Set the path of temporary task data. 

If the data sended by task exceeds 8192 bytes, the swoole will use the temporary file to store the data.

The default of `task_tmpdir` is `/tmp`.

임시 작업 데이터의 경로를 설정합니다.

작업으로 보낸 데이터가 8192 바이트를 초과하면 스풀은 임시 파일을 사용하여 데이터를 저장합니다.

`task_tmpdir`의 기본값은`/ tmp`입니다.