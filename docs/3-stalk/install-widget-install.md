위젯 개발 환경
======================

## 설치
```
$ git clone https://github.com/xpush/io.stalk.static
$ cd io.stalk.static
$ npm install
```

## 소스 변경

src 폴더의 widget.js에는 아래와 같은 설정들을 상황에 맞게 변경합니다.

```js
var _CONFIG = {
	.
	.
	.
	server: 'http://admin.stalk.io:8000',
	css_url: 'http://static.stalk.io/widget.css',
	.
	.
	.
}
```

server : io.stalk.admin 이 설치된 서버의 url 입니다.
css_url : io.stalk.static 이 서비스된 url의 주소입니다.


## 빌드 
gulp 를 이용하여 build 합니다.

```
$ npm install gulp
$ gulp widget
```

빌드한 결과는 www 폴더 안에 생성됩니다.


## 실행

nodejs나 python 또는 자체 webserver를 통해 실행할 수 있습니다.

### 1. nodejs 로 실행

기본적으로 80 포트로 실행이 되기 때문에, linux에서 실행시 root 권한이 필요합니다.

```
$ sudo node web.js
```

### 2. python으로 실행
```
$ sudo python -m SimpleHTTPServer 80
```

### 3. websever로 실행 

apache httpd 나 nginx를 사용하여 프로젝트 내의 www 폴더를 document root로 구성한 후 실행합니다.