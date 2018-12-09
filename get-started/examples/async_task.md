## Create Async Task

### Background

If you want to execute a time-consuming operation in the program, for instance broadcasting in a chat program and sending email in a web server. These operations would block the program and slow down the program in reuslt. 

프로그램에서 시간이 많이 걸리는 작업을 실행하려는 경우 (예 : 채팅 프로그램에서 브로드 캐스팅하고 웹 서버에서 전자 메일 보내기). 이러한 작업은 프로그램을 차단하고 다시 프로그램을 느리게 만듭니다.

Swoole provides the function for async task. You can send these time-consuming tasks to a task worker process pool to execute.

Swoole은 비동기 작업을위한 기능을 제공합니다. 시간이 많이 걸리는 작업을 작업 작업자 프로세스 풀로 보내 실행할 수 있습니다.

### Code Example

`async_task.php`

``` php
// Create the server object and listen 127.0.0.1:9501 port
$server = new swoole_server("127.0.0.1", 9501);

// Set the number of task worker process
$server->set(array(
	'task_worker_num' => 4
));

// Register the function for the event of receiving
$server->on('receive', function($server, $fd, $from_id, $data){
	
	// Send data to the task worker process
	$task_id = $server->task($data);
	echo "Dispatch async task: id = {$task_id}\n";

	// Send data to the client
    $server->send($fd, "Server: " . $data);
});

// Register the function for the event of receiving task
$server->on('task', function($server, $task_id, $from_id, $data){
	echo "Receive new task, id : {$task_id}\n";

	// Return the result of executing task
	$server->finish("{$data} ->finished");
});

// Register the function for the event of receiving task result
$server->on('finish', function($server, $task_id, $data){
	// Handle the result of executing task
	echo "Async task {$task_id} result : {$data} \n";
});

// Start the server
$server->start();
```

The code above is based on `tcp_server.php`. To send task, it needs to register two functions for event `task` and `finish`. And more, it needs to set the num of task worker precess according to your task amount and elapsed time.

위의 코드는`tcp_server.php`를 기반으로합니다. 태스크를 보내려면 이벤트`task`와`finish`에 대해 두 가지 함수를 등록해야합니다. 또한 작업량과 경과 시간에 따라 작업 근로자의 주행 횟수를 설정해야합니다.

> The callback function registered for event `finish` is optional. There is no need to set this function when the task doesn't return result

> 이벤트`finish`에 등록 된 콜백 함수는 선택 사항입니다. 작업이 결과를 반환하지 않을 때이 함수를 설정할 필요가 없습니다.

### Run program

``` bash
php server.php
```
