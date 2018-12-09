# Swoole Async File I/O

The swoole provides the functions of asynchronous file I/O. 

swoole은 비동기 파일 I / O의 기능을 제공합니다.

> The task process in swoole_server is syncing and blocking without using EventLoop, can't benefit from Async I/O.

> swoole_server의 작업 프로세스가 EventLoop, 비동기 I / O를 사용하지 않고 동기화 및 차단됩니다.

## Methods

### swoole_async_set(array $setting);

Update the Async I/O options:

비동기 I / O 옵션 업데이트 :

- thread_num: number of async file I/O threads

- thread_num : 비동기 파일 I / O 스레드 수

- aio_mode: AIO mode: SWOOLE_AIO_BASE/SWOOLE_AIO_LINUX

- aio_mode : AIO 모드 : SWOOLE_AIO_BASE / SWOOLE_AIO_LINUX

    `SWOOLE_AIO_LINUX` : use the linux native aio system call
    `SWOOLE_AIO_BASE` : use the thread pool to realize the async io

    `SWOOLE_AIO_LINUX` : 리눅스 네이티브 aio 시스템 호출을 사용합니다.
    `SWOOLE_AIO_BASE` : 스레드 풀을 사용하여 비동기식 IO를 실현합니다.

- enable_signalfd: whether enable signalfd

- enable_signalfd : enable signalfd 여부

- socket_buffer_size: socket buffer size

- socket_buffer_size : 소켓 버퍼 크기

- socket_dontwait: do not block when the buffer is full

- socket_dontwait : 버퍼가 가득 차면 차단하지 않습니다.

```php
<?php
swoole_async_set(array(
    'aio_mode' => SWOOLE_AIO_LINUX,
));
```

### swoole_async_readfile(string $filename, mixed $callback);

Read files in the async way. When the operation of reading content from file finished, the callback registered is callback automatically.

비동기 방식으로 파일을 읽습니다. 작업이 완료되면 등록 된 콜백이 자동으로 콜백됩니다.

The max length of file is 4M.

파일의 최대 길이는 4M입니다.

Example:

예제 :

```php
<?php
swoole_async_readfile(__DIR__."/server.php", function($filename, $content) {
     echo "$filename: $content";
});
```

### swoole_async_writefile(string $filename, string $fileContent, callable $callback = null, int $flags = 0)

Write file in the async way. When the operation of writing content to file finished, the callback registered is callback automatically.

파일을 비동기 적으로 씁니다. 쓰기 작업이 끝나면 등록 된 콜백은 자동으로 콜백입니다.

- `$filename` the file path of file. If fail to open this file, the method return false; 

- `$filename`은 파일의 파일 경로입니다. 이 파일을 열지 않으면 메서드는 false를 반환합니다.

- `$fileContent` the content to write to the file, The max length is 4M.

- `$fileContent`는 파일에 쓸 내용입니다. 최대 길이는 4M입니다.

- `$callback` the callback function triggered when the operation of writing content to file finished.

- `$callback` 파일에 내용을 쓰는 작업이 끝났을 때 발생하는 콜백 함수.

- `$flags` `FILE_APPEND`: append content to the end of file.
            If the aio mode setted by `swoole_async_set` is `SWOOLE_AIO_BASE`, the method can't support append content to the end of file and must set the value of `$fileContent` to integer multiples of 4096.

- `$flags`` FILE_APPEND` : 파일의 끝에 내용을 추가합니다.
             swoole_async_set에 의해 설정된 aio 모드가 SWOOLE_AIO_BASE라면,이 메소드는 파일의 끝에 추가 내용을 지원할 수 없으며 `$fileContent`의 값을 4096의 정수배로 설정해야합니다.

Example:

예제 :

```php
<?php
swoole_async_writefile('test.log', $file_content, function($filename) {
    echo "wirte ok.\n";
}, $flags = 0);
```

### bool swoole_async_read(string $filename, mixed $callback, int $size = 8192, int $offset = 0);

Read the file content stream in the async way. When the operation of reading content from file finished, the callback registered is callback automatically.

비동기 방식으로 파일 내용 스트림을 읽습니다. 작업이 완료되면 등록 된 콜백이 자동으로 콜백됩니다.

The difference between this method and `swoole_async_readfile` is that the former reads file by fragment and uses less memory. This method reads content of `$size` length from file every time and can be used to read big file.

이 방법과`swoole_async_readfile`의 차이점은 이전의 파일을 조각으로 읽고 더 적은 메모리를 사용한다는 것입니다. 이 메소드는 매번 파일에서 `$size` 길이의 내용을 읽고 큰 파일을 읽는 데 사용할 수 있습니다.

- `$size` the size of content to read from file

- `$size`는 파일로부터 읽을 내용의 크기입니다.

The callback function prototype is :

콜백 함수 프로토 타입은 다음과 같습니다 :

```
bool callback(string $filename, string $content);
```
- `$filename` the name of file

- `$filename` 파일의 이름

- `$content` the content readed from the file.

-`content` 내용은 파일에서 읽습니다.

You can control that if continue to read file by return true or false in the callback function.

콜백 함수에서 true 또는 false 인 경우이를 제어 할 수 있습니다.

- `return true;` continue to read file

-`return true;`계속 파일을 읽습니다.

- `return false;` stop to read file and close file

-`return false;`파일 읽기와 파일 닫기를 멈춤

### bool swoole_async_write(string $filename, string $content, int $offset = -1, mixed $callback = NULL);

Write file stream in the async way. When the operation of writing content to file finished, the callback registered is callback automatically.
            
비동기 방식으로 파일 스트림을 작성하십시오. 쓰기 작업이 끝나면 등록 된 콜백은 자동으로 콜백입니다.

The difference between this method and `swoole_async_writefile` is that the former writes file by fragment and uses less memory.

이 방법과`swoole_async_writefile`의 차이점은 전자가 조각으로 파일을 쓰고 메모리를 덜 사용한다는 것입니다.

- `$offset` The method uses the `$offset` parameter to decide the postion to write file. 
            If the `$offset` is setted to `-1`, it stands for that it appends content to the end of file.
            If the aio mode setted by `swoole_async_set` is `SWOOLE_AIO_BASE`, the method can't support append content to the end of file and must set the value of `$content` and `$offset` to integer multiples of 512. Otherwise the call of this method will fail and set the error code to `EINVAL`.

- `$offset`이 메소드는 `$offset` 매개 변수를 사용하여 파일을 쓸 위치를 결정합니다.
              `$offset`이`-1`로 설정되면, 그것은 파일의 끝에 추가한다는 것을 의미합니다.
             `swoole_async_set`에 의해 설정된 aio 모드가`SWOOLE_AIO_BASE` 인 경우, 메소드는 파일의 끝에 추가 내용을 지원할 수 없으며 `$content`와 `$offset`의 값을 512의 정수배로 설정해야합니다. 이 메소드를 호출하여 실패하고 오류 코드를 'EINVAL'로 설정하십시오.

### swoole_async_dns_lookup(string $host, mixed $callback)

Async DNS lookup. The call of this method is non-blocking. 

비동기 DNS 조회. 이 메소드의 호출은 비 블록화입니다.

- If the operation of DNS lookup finished, the callback registered is called automatically.

- DNS 검색 작업이 끝나면 등록 된 콜백이 자동으로 호출됩니다.

- If the operation of DNS lookup failed, the callback registered is also called automatically and the parameter `$ip` will be empty.

- DNS 조회 작업이 실패하면 등록 된 콜백도 자동으로 호출되며 매개 변수 `$ip '는 비어 있습니다.

Example:

예제 :

```php
<?php
// Disable DNS cache
swoole_async_set(array(
    'disable_dns_cache' => true,
));
// Set the DNS server list
swoole_async_set(array(
    'dns_server' => '8.8.8.8',
));
// Lookup using random DNS server
swoole_async_set(array(
    'dns_lookup_random' => true,
));

// Lookup the DNS of www.google.com
swoole_async_dns_lookup("www.google.com", function($host, $ip){
    echo "{$host} : {$ip}\n";
});
echo "start async dns lookup\n";
```
