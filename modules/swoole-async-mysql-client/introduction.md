# Swoole Async MySQL client

The swoole contains the swoole async MySQL client. It has realized the protocal of MySQL and is a replacement of the other sync MySQL clients: libmysqlclient, mysqlnd, mysqli.

swoole에는 swoole async MySQL 클라이언트가 포함되어 있습니다. MySQL 클라이언트 : libmysqlclient, mysqlnd, mysqli.

## Example:

``` php
<?php
$db = new swoole_mysql;
$server = array(
    'host' => '192.168.56.102',
    'port' => 3306,
    'user' => 'test',
    'password' => 'test',
    'database' => 'test',
    'charset' => 'utf8',
    'timeout' => 2,
);

$db->connect($server, function ($db, $r) {
    if ($r === false) {
        var_dump($db->connect_errno, $db->connect_error);
        die;
    }
    $sql = 'show tables';
    $db->query($sql, function(swoole_mysql $db, $r) {
        if ($r === false)
        {
            var_dump($db->error, $db->errno);
        }
        elseif ($r === true )
        {
            var_dump($db->affected_rows, $db->insert_id);
        }
        var_dump($r);
        $db->close();
    });
});
```

## Events

* connect

## Methods:

### swoole_mysql->construct()

### swoole_mysql->on($event_name, callable $callback);

Register callback function based on event name, current only 'Clost' event is supported.

swoole은 swoole async를 swoole합니다. MySQL 클라이언트 : libmysqlclient, mysqlnd, mysqli.

### swoole_mysql->connect(array $serverConfig, callable $callback);

Connect to the remote MySQL server.

원격 MySQL 서버에 연결하십시오.

Example:

예제 :

``` php
<?php
// serverConfig
$server = array(
    'host' => '192.168.56.102',
    'user' => 'test',
    'password' => 'test',
    'database' => 'test',
    'charset' => 'utf8',
);

// callback function
function onConnect(swoole_mysql $db, bool $result);
```

### swoole_mysql->escape(string $str) : string

Escape SQL strings to avoid SQL injection attacks.

SQL 삽입 공격을 피하기 위해 SQL 문자열을 이스케이프 처리합니다.

Example:

예제 :

``` php
<?php
$db = new swoole_mysql;
$server = array(
    'host' => '127.0.0.1',
    'user' => 'root',
    'password' => 'root',
    'database' => 'test',
);
$db->connect($server, function ($db, $result) {
    $data = $db->escape("abc'efg\r\n");
});
```

#### swoole_mysql->query($sql, callable $callback);

Run SQL query.

SQL 쿼리를 실행하십시오.

Callback function:

콜백 함수 :

function onSQLReady(swoole_mysqli $link, mixed $result);

함수 onSQLReady (swoole_mysqli $ link, mixed $ result);

#### swoole_mysql->begin(callable $callback);

Start a MySQL transaction.

MySQL 트랜잭션을 시작하십시오.

Example:

예제 :

``` php
<?php
$db->begin(function( $db, $result) {
    $db->query("update userinfo set level = 22 where id = 1", function($db, $result) {
        $db->rollback(function($db, $result) {
            echo "commit ok\n";
        });
    });
});
```

#### swoole_mysql->commit(callable $callback);

Commit the MySQL transaction.

MySQL 트랜잭션을 커밋하십시오.

Example:

예 :

``` php
<?php
$db->begin(function( $db, $result) {
    $db->query("update userinfo set level = 22 where id = 1", function($db, $result) {
        $db->commit(function($db, $result){
            echo "commit ok\n";
        });
    });
});
```

#### swoole_mysql->rollback(callable $callback);

Rollback the MySQL transaction.

MySQL 트랜잭션을 롤백하십시오.

#### swoole_mysql->close();

Close the MySQL connection.

MySQL 연결을 닫습니다.