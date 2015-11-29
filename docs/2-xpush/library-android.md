Android xpush library
=============

android에서 xpush를 사용하기 위한 library이며, jcenter에 공유되어 있습니다.

### 설정

#### build.gradle

build.gradle 에 depencencies 설정을 추가합니다.

	dependencies {
	    compile 'io.xpush:lib-xpush-android:0.0.1'
	}


#### AndroidManifest.xml

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

#### string.xml

Local DB의 Data를 조회하기 위한 content_provider_authority와 xpush 고유의 app_id를 설정합니다.

	<string name="app_id">STALK</string>
    <string name="content_provider_authority">custom_ provider_name</string>   

### 초기화

Application에서 XPushCore instance를 초기화합니다.

	public class MyApplication extends Application {
	    @Override
	    public void onCreate() {
	        super.onCreate();
	        XPushCore.initialize(this);     
	    }
	}
