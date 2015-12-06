Admin Server 설정 및 시작
======================

Admin 서버를 실행하기 위해서는 필요한 몇가지 정보를 설정해야 합니다.

## 설정

host : 설치한 서버의 public ip나 domain을 입력합니다.

mongo: 사용할 mongoDB의 주소를 표기합니다.

xpush: 직접 설치한 XPUSH 서버를 사용하려고 한다면, 설치한 URL 정보를 입력합니다.

그렇지 않은 경우, XPUSH의 SANDBOX 도메인인 session.stalk.io:8000를 사용합니다.

### example.js

아래를 참조하여 example.js 파일을 생성합니다.

```js
module.exports = {
  // MongoDB connection options
  host: 'admin.stalk.io',
  mongo: {
    uri: 'mongodb://10.0.5.171/stalk-dev'
  },
  xpush: {
    url: "http://session.stalk.io:8000",
    A: "STALK"
  }
};
```

## 실행

admin server는 grunt 로 실행할 수 있습니다. 해당 명령어를 사용하면 9000번 port 로 서버가 실행됩니다.

config option을 통해 설정정보를 이용하여 서버를 시작할 수 있습니다. 

```
grunt serve --config example.js
```