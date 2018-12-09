### daemonize

Daemonize the swoole server process.

스풀 서버 프로세스를 평준화합니다.

If the value of `daemonize` is more than 1, the swoole server will be daemonized. 

`daemonize`의 값이 1보다 크면, 스풀 서버는 데몬 화됩니다.

The program which wants to run long time must enable this configuration.

오랫동안 실행하려는 프로그램이이 구성을 사용 가능하게해야합니다.

If the `daemonize` has been enabled, the standard output and error of the program will be redirected to [logfile](/modules/swoole-server/configuration/log_file.md). And if the configuration of `log_file` hasn't been setted, the standard output and error of the program will be redirected to `/dev/null`.

`daemonize`가 활성화되면, 프로그램의 표준 출력과 오류는 [logfile] (/ modules / swoole-server / configuration / log_file.md)로 재 지정됩니다. 그리고`log_file`의 설정이 설정되지 않았다면, 프로그램의 표준 출력과 에러는`/ dev / null`으로 리디렉션됩니다.

> 프로세스를 데몬 화 한 후`CWD '의 값이 바뀌고 파일의 상대 경로가 달라집니다. 따라서 프로그램에서 절대 경로를 사용해야합니다.

> After daemonizing the processes, the value of `CWD` will change and the relative path of file will be different. So it must use absolute path in the program. 
