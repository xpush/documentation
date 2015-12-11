Iphone xpush library
======================

ios에서 xpush 를 사용하기 위한 library이며, Cocoapods에 등재될 예정입니다. 
(Cocoapods 은 ios 에서 라이브러리를 편리하게 사용하기 위한 보조 도구 입니다.)

### 설정 

#### Framework 소스를 다운로드

 > git clone https://github.com/xpush/lib-xpush-ios
 
 xcode 에서 작업중인 프로젝트에 lib-xpush-ios를 드래그 해서 포함 시킨다. 
 
 프로젝트설정을 클릭한 뒤에 
  > General > Linked Frameworks and Libraries 안에 + 버튼을 클릭하여 XpushFramework.framework가 포함되도록 한다.
  
  
#### 초기화 
  
  app 의 시작파일인 AppDelegate(기본) 파일 안에서 Xpush의 기본 정보들을 넣고 초기화를 준비한다.
   > Xpush.setup("http://yourdomain", appId: {{appId}} );

#### 사용

  * Signup
  >        XPushAPI().signup( {{id}} , passwd: {{pass}} , cb: { status, data in
            if(status != "ok"){
                print(data);
            }
        } );
        

   * Signin
   >        XPushAPI().login(id.text!, passwd: pass.text!, cb: { status, data in
            if(status != "ok"){
                print(data);
            }
        } );

   * 부가적인 기능 
   
  부가적인 API들은 https://github.com/xpush/lib-xpush-ios 에 명시될 예정입니다.
