서버 설치
=============

XPUSH를 사용하기 위해서는 [nodejs](http://nodejs.org/), [zookeeper](http://zookeeper.apache.org/), [redis](http://redis.io/) 의 설치가 필요합니다.


본 가이드 문서는 64bit linux( ubuntu 14.04 )에서 설치하는 방법을 다루고 있습니다. 여러분의 환경에 맞는 설치가 필요합니다.
이미 설치되어 있다면, 준비 단계를 skip하셔도 좋습니다.


## 1. 준비

### nodejs 설치

[nodejs installation](http://nodejs.org/download/)를 참조하여 nodejs를 다운로드한 후에 압축을 해제합니다.

	mkdir -p $HOME/xpush
	cd $HOME/xpush
	wget https://nodejs.org/dist/v5.1.0/node-v5.1.0-linux-x64.tar.gz
	tar zvf node-v5.1.0-linux-x64.tar.gz
	mv node-v5.1.0-linux-x64 nodejs

환경변수 PATH에 설정하여 node와 npm을 global하게 사용할 수 있도록 합니다.
	
	PATH=$HOME/xpush/nodejs/bin:$PATH

### zookeeper

[zookeeper installation](http://zookeeper.apache.org/doc/trunk/zookeeperStarted.html)를 참조하여 zookeeper를 설치하고 실행합니다.

아래는 zookeeper 3.4.6을 설치하고 실행하는 코드입니다.

	cd $HOME/xpush
	wget http://apache.mirror.cdnetworks.com/zookeeper/stable/zookeeper-3.4.6.tar.gz
	tar xvf zookeeper-3.4.6.tar.gz
	mv zookeeper-3.4.6 zookeeper
	cp zookeeper/conf/zoo_sample.cfg zookeeper/conf/zoo.cfg
	cd zookeeper/bin
	./zkServer.sh start

### redis

[redis installation](http://redis.io/download)를 참조하여 redis를 설치하고 실행합니다.

아래는 redis 3.0.5를 설치하고 실행하는 코드입니다.
	
	cd $HOME/xpush
	wget http://download.redis.io/releases/redis-3.0.5.tar.gz
	tar xvf redis-3.0.5.tar.gz
	mv redis-3.0.5 redis
	cd redis/src
	make
	./redis-server

## 2. XPUSH 설치

### github에서 설치

	cd $HOME/xpush
	git clone https://github.com/xpush/node-xpush.git
	cd node-xpush
	npm install

### session server 실행

	node examples/sever-session.js

### channel server 실행

	node examples/sever-channel.js

