## redis
===============================

### 2.8에서의 redis 3.0으로의 주요 변화

* Redis Cluster : Redis Cluster가 중분히 테스트 되어 구현되었습니다.
* Key eviction을 위한 LRU 근사치 알고리즘이 매우 향상 되었습니다.
* WAIT 명령어는 쓰기가 지정된 숫자의 slave에 쓰여지기 전까지 대기할 것입니다.
* MIGRATE 명령어에 connection 캐싱이 추가되어 좀더 빨라졌으며, COPY REPLACE 라는 새로운 옵션이 추가되었습니다.
* CLINT PAUSE 명령어는 정해진 시간 만큼 클라이언트의 요청을 처리하는 것을 멈춥니다.
* BITCOUNT, INCR의 성능이 개선되었습니다.

* ** 출처 ** 
 - [REDIS Release Note](https://github.com/antirez/redis/blob/3.0/00-RELEASENOTES) 