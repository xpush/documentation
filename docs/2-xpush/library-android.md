Android xpush library
=============

android에서 xpush를 사용하기 위한 library이며, jcenter에 공유되어 있습니다.

현재 최신 버젼은 0.0.3 입니다.

## 설정

### build.gradle

build.gradle 에 depencencies 설정을 추가합니다. 

	dependencies {
	    compile 'io.xpush:lib-xpush-android:0.0.3'
	}


### AndroidManifest.xml

android application을 세팅합니다.

	<!-- 받은 메시지를 처리하는 Receiver -->
	<receiver
	    android:name="io.xpush.chat.services.PushMsgReceiver"
	    android:permission="com.google.android.c2dm.permission.SEND" >
	    <intent-filter>
	        <action android:name="com.google.android.c2dm.intent.RECEIVE" />
	        <action android:name="io.xpush.chat.MGRECVD" />
	    </intent-filter>
	</receiver>

	<!-- 상태 변경에 따라 Service를 관리하기 위한 Receiver -->
	<receiver android:name="io.xpush.chat.services.ChangeStatusReceiver">
	    <intent-filter>
	        <action android:name="android.intent.action.BOOT_COMPLETED" />
	        <action android:name="android.intent.action.USER_PRESENT" />
	        <action android:name="android.intent.action.ACTION_PACKAGE_RESTARTED" />
	        <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
	    </intent-filter>
	</receiver>

	<!-- XPush의 connection을 유지하는 service -->
	<service android:name="io.xpush.chat.services.XPushService" android:enabled="true" android:exported="true" >
	</service>

	<!-- GCM을 notification key를 위한 service -->
	<service android:name="io.xpush.chat.services.RegistrationIntentService" android:exported="false" >
	</service>

	<!-- 데이터를 조회하기 위한 ContentProvider 설정-->
	<provider
    	android:name="io.xpush.chat.persist.XpushContentProvider"
    	android:authorities="@string/content_provider_authority" />

### string.xml

Local DB의 Data를 조회하기 위한 content_provider_authority와 xpush 고유의 app_id를 설정합니다.

	<string name="app_id">STALK</string>
    <string name="content_provider_authority">custom_ provider_name</string>   

### 초기화

Application에서 XPushCore instance를 초기화합니다.

```java
	public class MyApplication extends Application {
	    @Override
	    public void onCreate() {
	        super.onCreate();
	        XPushCore.initialize(this);     
	    }
	}
```

## 주요모듈 설명

### XPushCore

XPush 플랫폼에서 제공하는 기능들 중에서 세션 서버가 제공하는 API와 Global Socket이 제공하는 이벤트들을 함수 형태로 제공합니다. 주로 채팅방에 진입하기 전에 필요한 기능들을 제공하고 있으며, 주요 기능은 아래와 같습니다.

- 사용자 및 장치 관련 :  사용자 등록, 사용자 수정, 사용자 로그인, 장치 추가, 세션 정보 저장
- 친구 관련 : 친구 조회, 친구 추가 , 친구 삭제, 친구 목록 저장
- 채널 관련 : 채널 생성, 채널 목록 조회

### ChannelCore

채널 서버가 제공하는 Socket Event들을 사용하기 쉽게 구현해 놓은 클래스입니다. 주고 받는 모든 메세지는 이미 정의된 TABLE내에 자동으로 저장이 되기 때문에 메시지에 대한 조회를 쉽게 할 수 있도록 설계되어 있습니다. ChannelCore가 제공하는 주요 기능은 아래와 같습니다.

- 접속 관련 : 채널 접속, 채널에 사용자 초대, 채널에서 나가기
- 메시지 관련 : 메시지 발송, 이벤트 발송, 메시지 조회

### XPushService

Global Socket의 접속을 항상 유지하기 위한 Service 클래스입니다. 모바일 디바이스의 특성상 인터넷 연결이 끊어지는 현상이 자주 발생할 수 있는데, 이러한 문제를 해결하기 위해 Android의 알람 매니저(Alarm Manager)를 이용하여 5분 간격으로 Ping을 전송해서 소켓이 연결이 되어 있지 않은 경우에 다시 접속을 시도하는 로직이 구현되어 있습니다. 또한 해당 Library를 사용하는 어플리케이션이 활성화되지 않았을 때, 백그라운드로 메세지를 저장하고 모바일 알림(Notification)을 실행할 수 있도록 구현되어 있습니다.