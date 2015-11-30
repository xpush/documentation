XPUSH 구성 요소
======================

서버 구성도 

사용하는 Redis, Zookeeper 에 대한 소개


## [Zookeeper](http://zookeeper.apache.org/)

Zookeeper는 메모리를 이용하기 때문에 데이터에 대한 엑세스가 빠르고, 또한 분산 락이나 동기화에 대한 데이터의 안정성을 보장합니다. 또한 자체적은  장애 처리 기능을 제공하기 때문에 Apache Hbase와 유명한 같은 분산 솔루션에서 많이 활용되고 있습니다.


### Zookeeper 활용

XPUSH 는 분산 서버들의 실시간 코디네이션을 위하여 zookeeper 를 사용하고 있습니다.

세션 서버는 zookeeper의 */xpush/servers*라는 znode를 watching 하는 방법으로 채널 서버목록을 동기화하고 있습니다.

세션 서버는 채널 서버가 상태가 변경될 때 채널 서버의 목록을 변경하는 방법을 이용해서 서버가 동적으로 추가가 되거나 제거가 되더라도, 적절한 채널 서버를 할당할 수 있습니다.


### 채널 서버의 추가

채널 서버가 시작될 때, 해당 서버에 대한 접속정보를 zookeeper 의 */xpush/servers* znode에 자식으로 추가합니다.

세션 서버는 znode가 추가되었음을 인지하고, 채널 서버 목록에 새로운 서버를 추가합니다.


### 채널 서버의 제거

채널 서버가 종료되면, 해당 서버에 대한 정보를 */xpush/servers* znode에서 제거합니다. 

세션 서버는 znode가 제거되었음을 인지하고, 채널 서버 목록에 해당 서버를 제거합니다.


## [redis](http://www.redis.io/)

Redis는 메모리 기반의 Key/Value 저장소입니다. 모든 데이타가 메모리에 있어 data에 대한 access가 빠르기 때문에 DB 조회 후에 결과를 저장하는 cache나 세션 storage 용도로 많이 사용되고 있습니다.


### Redis 활용

XPUSH는 서버에 연결되어 있는 정보를 실시간 저장하고 기본데이터를 캐쉬하기 위해 Redis를 사용합니다. 
redis cluster를 구성할 경우에 효율적으로 data를 엑세스할 수 있도록 설계되어 있습니다.
