### log_file

Set the log path of swoole.

swoole의 로그 경로를 설정하십시오.

#### Tips

In the log file, there are some labels to distinguish the thread or process that output the log item.

로그 파일에는 로그 항목을 출력하는 스레드 또는 프로세스를 구별하는 레이블이 있습니다.

- `#` Master process

- `$` Manager process

- `*` Worker process

- `^` Task worker process

-`#`마스터 프로세스

-`$`관리자 프로세스

-```작업자 프로세스

-`^`작업 작업자 프로세스

#### Reopen the log file

If the log file has been `mv` or `unlink`, the log can't be recorded normally. In this situation, you can send `SIGRTMIN` 

로그 파일이`mv` 또는`unlink` 인 경우 로그를 정상적으로 기록 할 수 없습니다. 이 상황에서`SIGRTMIN`을 보낼 수 있습니다.