Admin Server 설치
======================

Admin Server를 설치하고 사용하기 위해서는 nodejs와 mongoDB가 그리고 XPUSH가 필요합니다.

해당 [링크](https://stalk.gitbooks.io/documentation/content/docs/2-xpush/install-server.html)를 참조하여 nodejs와 mongoDB, XPUSH를 설치합니다.(XPUSH는 반드시 설치할 필요는 없습니다.)

소스는 [여기](https://github.com/xpush/io.stalk.admin)에 공개되어 있습니다.

## 설치 

git에서 소스를 clone 받아서 npm과 bower를 이용하여 의존성 라이브러리를 설치합니다.

```
git clone https://github.com/xpush/io.stalk.admin
cd io.stalk.admin
npm install
bower install
```