Channel Server
======================

Channel Server는 채팅을 실제로 하기 위한 기능을 제공하는 서버

## node-xpush의 Channel Server가 제공해주는 기능

### socket events

socket events | Description           
--- | ---
send | 메시지를 전송함

#### send
Message를 전송함

##### Request
```js
{}
```

##### Response
```js
{}
```

## xpush-chat의 Channel Server가 추가로 제공해주는 기능

### global socket events

socket events | Description           
--- | ---
channel.create | 채널을 생성한다.
group.list | 친구목록을 조회한다.
group.add  | 친구목록에 추가한다.
group.remove | 친구목록에서 삭제한다.

#### channel.create
입력받은 채널 id를 이용하여 파라미터로 사용자들을 멤버로 추가시키면서 채널을 생성한다.

##### Request
```js
{"C":"channel01", "U":"['user01','user02']"}
```

##### Response
```js
{"status":"", "result":{}}
```

#### group.list
입력받은 userId( GR )을 이용하여 친구 리스트를 조회한다.

##### Request
```js
{"GR":"user01"}
```

##### Response
```js
{"status":"", "result":[]}
```

#### group.add
group id를 가진 유저에게 입력받은 사용자들을 친구로 추가한다.

##### Request
```js
{"GR":"user01", "U":"['user01','user02']"}
```

##### Response
```js
{"status":""}
```

#### group.remove
Group Id 에서 입력받은 user 를 친구에서 삭제한다.

##### Request
```js
{"GR":"user01", "U":"user01"}
```

##### Response
```js
{"status":""}
```

### channel socket events

메시지 전송을 위한 event들이 정의되어 있다.

socket events | Description           
--- | ---
channel.join | 해당 채널에 사용자를 추가한다.
channel.leave | 채널에서 나간다.
message.unread | 채널 내의 읽지 않은 메시지들을 조회한다.

#### channel.join
현재 채널에 파라미터로 입력받은 사용자들을 멤버로 추가시킨다.

##### Request
```js
{"U":"['user01','user02']"}
```

##### Response
```js
{"status":"", "result":[]}
```

#### channel.leave
현재 채널에서 떠난다.

##### Request
None

##### Response
```js
{"status":"ok"}
```

#### message.unread
현재 채널에서, 파라미터로 입력받은 epoch timestamp 이후의 메세지들을 조회한다.

##### Request
{"TS":1448879201}

##### Response
```js
{"status":"ok", "result":[]}
```
