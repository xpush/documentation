Session Server
======================

Session Server는 채팅 채널을 여러개로 분산해주기 위한 용도의 서버

## Session Server가 제공해주는 기능

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


