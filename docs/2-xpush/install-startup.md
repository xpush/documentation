XPUSH 실행
======================

## 설정

xpush를 실행할 때 사용할 option을 설정합니다.

####config
XPUSH server 실행될 때 사용할 CONFIG FILE 위치를 지정합니다.

```
--config ./config.sampel.json

```

XPUSH server 실행될 때 사용할 CONFIG FILE 위치를 지정합니다.

####host
XPUSH server 실행될 때 사용할 hostname.
zookeeper에 서버가 등록될 때 사용되기 때문에 반드시 접근가능한 URL이어야 합니다. default 127.0.0.1

```
--host www.sample.net
```

####port
XPUSH server가 실행될 때 사용할 PORT

```
--port 8000
```

## 실행

### session server 실행
```node
node ~/xpush/xpush-chat/bin/session-server --port 8000
```

### channel server 실행
```node
node ~/xpush/xpush-chat/bin/channel-server --port 8080
```