# Swoole Buffer

Memory management module enable developers managing memory like C language without worrying about memory allocation and release.

메모리 관리 모듈을 사용하면 개발자가 메모리 할당 및 릴리스 걱정없이 C 언어와 같은 메모리를 관리 할 수 있습니다.

> The memory allocated by swoole_buffer is not shared memory and can not be accessed by multiple processes.

> swoole_buffer에 의해 할당 된 메모리는 공유 메모리가 아니며 여러 프로세스에서 액세스 할 수 없습니다.

### Quick Example

``` php
<?php
$buffer = new swoole_buffer();
$buffer->append(str_repeat("A", 10));
$buffer->append(str_repeat("B", 20));
$buffer->append(str_repeat("C", 30));
var_dump($buffer);
```

### Methods

#### swoole_buffer->__construct(int $size = 128);

Fixed size memory blocks allocation.

고정 크기 메모리 블록 할당.


#### int swoole_buffer->append(string $data);

Append the string or binary data at the end of the memory buffer and return the new size of memory allocated.

문자열 또는 이진 데이터를 메모리 버퍼 끝에 추가하고 할당 된 새 메모리 크기를 반환하십시오.

#### string swoole_buffer->substr(int $offset, int $length = -1, bool $remove = false);

Read data from the memory buffer based on offset and length. Or remove data from the memory buffer.

오프셋 및 길이에 따라 메모리 버퍼에서 데이터를 읽습니다. 또는 메모리 버퍼에서 데이터를 제거하십시오.

> If $remove is set to be true and $offset is set to be 0, the data will be removed from the buffer. The memory for storing the data will be released when the buffer object is deconstructed.

> $ remove가 true로 설정되고 $ offset이 0으로 설정되면 데이터가 버퍼에서 제거됩니다. 데이터를 저장하기위한 메모리는 버퍼 객체가 해체 될 때 해제됩니다.

#### swoole_buffer->clear();

The memory buffer will be reset.

메모리 버퍼를 재설정하려고합니다.

#### swoole_buffer->expand(int $new_size);

Expand the size of memory buffer.

메모리 버퍼의 크기를 확장하십시오.

#### swoole_buffer->write(int $offset, string $data);

Write data to the memory buffer. The memory allocated for the buffer will not be changed.

데이터를 메모리 버퍼에 씁니다. 버퍼에 할당 된 메모리는 변경되지 않습니다.

#### swoole_buffer->read(int $offset, int $length)

Read data from the memory buffer based on offset and length.

오프셋 및 길이에 따라 메모리 버퍼에서 데이터를 읽습니다.

#### swoole_buffer->recycle();

Release the memory to OS which is not used by the memory buffer.

메모리 버퍼에서 사용하지 않는 OS로 메모리를 해제하십시오.


