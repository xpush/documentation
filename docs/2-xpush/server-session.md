Session Server
======================

Session Server는 채팅 채널을 여러개로 분산해주기 위한 용도의 서버

## node-xpush의 기본 기능

### APIs

APIs               | Description           
--- | ---
node/:app/:channel | 채널서버를 할당받음

#### node/:app:channel
GET
채널ID를 통해 접속할 채널 서버의 정보를 가져온다.

##### Request
app      : 유니크한 XPUSH의 application id
channel  : 접속하려고 하는 channel id

##### Response
```js
{
  "status": "",
  "message": "",
  "result": {}
}
```

## xpush-chat의 Channel Server가 추가로 제공해주는 기능

### API List

APIs | Description           
--- | ---
/user/register | 사용자를 등록한다.
/user/update | 사용자의 정보를 수정한다.
/user/active  | 사용자가 현재 접속 중인지를 확인한다.
/user/search | 사용자를 조회한다.
/auth | 사용자 로그인 처리한다.
/device/add | 사용자 계정에 다른 장치를 신규로 등록한다.

#### /user/register
입력받은 사용자 정보를 이용하여 사용자를 신규로 추가한다.

- A : 사용중인 어플리케이션의 고유ID
- U : 사용자 ID
- PW : 사용자의 비밀번호
- N : Notification ID, Android의 GCM Registration ID나 Apple Push Notification ID를 사용
- D : 장치의 고유 ID
- DT : JSON 형태의 추가 사용자 정보, 사용자 정보나 프로필 이미지 등을 용도에 맞게 마음껏 사용할 수 있다.


##### Request
```js
{"A":"app01", "U":"user01", "PW":"password01", "DT":{}, "N":"gcm registration id 01", "D":"device01"  }
```

##### Response
```js
{"status":"ok"}
```

#### /user/update
입력받은 사용자 정보를 이용하여 사용자의 정보를 수정한다.

- A : 사용중인 어플리케이션의 고유ID
- U : 사용자 ID
- PW : 사용자의 비밀번호
- N : Notification ID, Android의 GCM Registration ID나 Apple Push Notification ID를 사용
- D : 장치의 고유 ID
- DT : JSON 형태의 추가 사용자 정보, 사용자 정보나 프로필 이미지 등을 용도에 맞게 마음껏 사용할 수 있다.

##### Request
```js
{"A":"app01", "U":"user01", "PW":"password01", "DT":{}, "N":"gcm registration id 01", "D":"device01"  }
```

##### Response
```js
{"status":"ok", "user":{} }
```

#### /user/active
입력받은 사용자 ID를 이용하여 사용자가 서비스에 접속 중인지를 확인한다.

- A : 사용중인 어플리케이션의 고유ID
- U : 사용자 ID

##### Request
```js
{"A":"app01", "U":"user01"}
```

##### Response
```js
{"status":"ok", "result": {"user01":true} }
```

#### /user/search
입력받은 값을 이용하여 특정 사용자를 검색한다. 사용자의 이름이나 사용자의 ID를 기반으로 검색을 수행한다.

- A : 사용중인 어플리케이션의 고유ID
- K : 겁색을 위한 입력값

##### Request
```js
{"A":"app01", "K":"james"}
```

##### Response
```js
{"status":"ok", "result": {users: users, count: count} }