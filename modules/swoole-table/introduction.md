# Swoole Table

Swoole table is a high performance memory management module, implemented based on shared memory and spin lock. 

Swoole 테이블은 공유 메모리 및 스핀 잠금을 기반으로 구현 된 고성능 메모리 관리 모듈입니다.

> In order to keep the data synchronization, have to use Swoole\Lock if the memory is modified and accessed by multiple threads or processes.

> 데이터 동기화를 유지하려면 메모리가 수정되고 여러 스레드 또는 프로세스가 액세스하는 경우 Swoole \ Lock을 사용해야합니다.

Swoole table provides a two dimensions memory table for developers. 

Swoole 테이블은 개발자를위한 2 차원 메모리 테이블을 제공합니다.

## Why to use swoole table

* High performance, the single thread read/write speed is more than 2 millions per second.
* Can be used by multiple threads or processes.
* In application counters storage.

* 고성능, 단일 스레드 읽기 / 쓰기 속도는 초당 2 백만 이상입니다.
* 여러 스레드 또는 프로세스에서 사용할 수 있습니다.
* 응용 프로그램 카운터 저장소.

## Methods

### swoole_table->__construct($table_size);

Construct a Swoole memory table with size.

크기가있는 스몰 메모리 테이블을 만듭니다.

### swoole_table->column($name, $type, $size = 0);

Set the data type and size of the columns.

열의 데이터 유형과 크기를 설정하십시오.

### boolean swoole_table->create();

Create the swoole memory table.

스풀 메모리 테이블을 만듭니다.

### swoole_table->set(string $row_key, array $value);

Update a row of the table by $row_key.

$ row_key에 의해 테이블 행을 갱신하십시오.

### swoole_table->get(string $row_key, string $column_key);

Get the value by $row_key and $column_key.

$ row_key 및 $ column_key로 값을 가져옵니다.

### swoole_table->del(string $row_key);

Delete a row by $row_key.

$ row_key로 행을 삭제하십시오.

### swoole_table->exist(string $row_key);

Check if a row is existed by $row_key.

$ row 키에 의해 행이 존재하는지 확인하십시오.

### swoole_table->incr(string $row_key, string $column_key, integer $incr_by = 1);

Increment the value by $row_key and $column_key.

$ row_key 및 $ column_key만큼 값을 증가 시키십시오.

### swoole_table->decr(string $row_key, string $column_key, integer $decr_by = 1);

Decrement the value by $row_key and $column_key.

$ row_key 및 $ column_key 값을 감소시킵니다.

### long swoole_table->count($mode = 0);

Count the rows in the table, or count all the elements in the table if $mode = 1.

$ mode = 1 인 경우 표의 행을 계산하거나 표의 모든 요소를 계산하십시오.

### boolean swoole_table->destroy();

Destroy the memory table.

메모리 테이블을 파괴하십시오.

### swoole_table->rewind

> PCRE is needed for this function

>이 기능을 위해서는 PCRE가 필요합니다.

### swoole_table->next

> PCRE is needed for this function

>이 기능을 위해서는 PCRE가 필요합니다.

### swoole_table->current

> PCRE is needed for this function

>이 기능을 위해서는 PCRE가 필요합니다.

### swoole_table->key

> PCRE is needed for this function

>이 기능을 위해서는 PCRE가 필요합니다.

### swoole_table->valid

> PCRE is needed for this function

>이 기능을 위해서는 PCRE가 필요합니다.

### Iterator and Countable

> The iterator and countable depends on pcre-devel

> 반복자와 셀 수는 pcre-devel에 따라 다릅니다.

```php
<?php
foreach($table as $row)
{
    var_dump($row);
}
echo count($table);
```

### Example


