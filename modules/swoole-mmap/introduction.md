# Swoole MMap

Swoole provides the api to use mmap for files access. This is useful when multiple threads or processes accessing data in a read only fashion from the same file.

Swoole은 api가 파일 액세스에 mmap을 사용할 수있게합니다. 이것은 여러 스레드 또는 프로세스가 동일한 파일에서 읽기 전용 방식으로 데이터에 액세스 할 때 유용합니다.

### Example

``` php
<?php
$file = __DIR__.'/data.dat';
$size = 8192;
if (!is_file($file)) {
    file_put_contents($file, str_repeat("\0", $size));
}

$fp = swoole\mmap::open($file, 8192);

fwrite($fp, "hello world\n");
fwrite($fp, "hello swoole\n");

fflush($fp);
fclose($fp);
```

### Methods

#### function swoole_mmap->open($file, $size = -1, $offset = 0);

Map a file into memory and return a *stream* resource which can be used by PHP stream operations.

파일을 메모리에 매핑하고 PHP 스트림 작업에서 사용할 수있는 * stream * 리소스를 반환합니다.

### Methods to use mmap in PHP

* *fread*: read data from mmap stream
* *fgets*: read data from mmap stream
* *fwrite*: write data to mmap stream
* *fputs*: write data to mmap stream
* *fflush*: sync data on the disk file
* *fclose*: sync data on the disk file and close the file


* * fread * : mmap stream에서 데이터 읽기
* * fgets * : mmap stream에서 데이터 읽기
* * fwrite * : mmap stream에 데이터 쓰기
* * fputs * : mmap 스트림에 데이터 쓰기
* * fflush * : 디스크 파일의 데이터 동기화
* * fclose * : 디스크 파일에 데이터를 동기화하고 파일을 닫습니다.
