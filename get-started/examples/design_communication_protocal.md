## Design Communication Protocol

### Why design communication protocol

The TCP protocol is connection oriented. Once established, the data can be sent bidirectional. It rearranges data packets in the order specified. Unlike UDP, the data transported by TCP is read as a “stream” with nothing to distinguish the packet end and front. And there may be multiple packets through per read.

TCP 프로토콜은 연결 지향적입니다. 일단 설정되면 데이터를 양방향으로 보낼 수 있습니다. 지정된 순서대로 데이터 패킷을 재배 열합니다. UDP와 달리 TCP로 전송 된 데이터는 패킷 끝과 앞을 구별하지 않고 "스트림"으로 읽습니다. 그리고 읽기마다 여러 개의 패킷이있을 수 있습니다.

When the applications want to use TCP to exchange data, it needs to use or design the protocol over TCP to solve the problem of distinguishing packets. There are many commonly used protocols over TCP, for instance, HTTP, FTP, SMTP, POP3, etc.

응용 프로그램이 TCP를 사용하여 데이터를 교환하려면 패킷을 구분하는 문제를 해결하기 위해 TCP를 통한 프로토콜을 사용하거나 설계해야합니다. HTTP, FTP, SMTP, POP3 등과 같이 TCP를 통해 많이 사용되는 프로토콜이 많이 있습니다.

Except for those commonly used protocols, you can design customized protocol according to your application. For designing protocol, the most important is how to distinguish the boundary between packets. There are two examples of customized protocol.

일반적으로 사용되는 프로토콜을 제외하고 응용 프로그램에 따라 사용자 지정된 프로토콜을 디자인 할 수 있습니다. 프로토콜을 설계 할 때 가장 중요한 것은 패킷 간의 경계를 구분하는 방법입니다. 사용자 정의 된 프로토콜에는 두 가지 예가 있습니다.

### Customized Protocol

#### EOF terminator protocol

This protocol adds a specified string in the end of every packet to represent the boundary of the packet. For example, the memcache, ftp and stmp use the `\r\n` as terminator. If the protocol use the `\r\n` as terminator, there mustn't be `\r\n` in the data.

이 프로토콜은 모든 패킷 끝에 지정된 문자열을 추가하여 패킷의 경계를 나타냅니다. 예를 들어, memcache, ftp, stmp는`\ r \ n`을 종결 자로 사용합니다. 프로토콜이`\ r \ n`을 종결 자로 사용하면 데이터에 \ r \ n이 없어야합니다.

It is easy to use EOF terminator protocol in swoole by setting the corresponding parameters.

EOF 터미네이터 프로토콜을 해당 매개 변수를 설정하여 swoole로 쉽게 사용할 수 있습니다.

```php
$server->set(array(
	'open_eof_split' => true,
	'package_eof' => "\r\n",
));

$client->set(array(
	'open_eof_split' => true,
	'package_eof' => "\r\n",
));

```

#### Fixed packet head and body protocol

This protocol devides the packet to two parts, head and body. The length of head is fixed. And one of parameter in the head indicates the whole length of the packet. When the server receives this kind of packet, it can control the length of reading from the data stream according to the head.

이 프로토콜은 패킷을 머리와 몸의 두 부분으로 나눕니다. 머리의 길이는 고정되어있다. 머리 부분의 매개 변수 중 하나는 패킷의 전체 길이를 나타냅니다. 서버가 이런 종류의 패킷을 받으면 헤드에 따라 데이터 스트림에서 읽는 길이를 제어 할 수 있습니다.

It is easy to set this kind of protocol in swoole by setting the corresponding parameters. When this kind of protocol is setted, the receive event isn't triggered until the server or client receive a full packet.

해당 매개 변수를 설정하여 이러한 종류의 프로토콜을 쉽게 swoole에 설정할 수 있습니다. 이러한 종류의 프로토콜이 설정되면 서버 또는 클라이언트가 전체 패킷을 수신 할 때까지 수신 이벤트가 트리거되지 않습니다.

```php
$server->set(array(
	'open_length_check' => true,
	'package_max_length' => 81920,
	'package_length_type' => 'n', //see php pack()
	'package_length_offset' => 0,
	'package_body_offset' => 2,
));
```
