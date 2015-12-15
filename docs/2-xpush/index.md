XPUSH Live Chat Platform
========================

## XPUSH-CHAT

xpush-chat은 node-xpush를 기반으로 하고 있는 채팅을 위한 모듈입니다.

[node-xpush](https://github.com/xpush/node-xpush)가 메시지 전송을 위한 기본적인 기능을 제공하는 것에 비해

[xpush-chat](https://github.com/xpush/xpush-chat)은 1:1 대화방 생성, 그룹 대화방 생성, 대화방에 사용자 초대 등의 기능을 추가로 제공하고 있습니다. 또한 전송되는 모든 메시지가 MongoDB에 저장되기 때문에, 네트워크에 연결 중이지 않은 사용자에게도 추후에 메세지를 전달할 수 있습니다.

주요 기능은 아래와 같습니다.

 - 사용자 관련 :  사용자 등록, 사용자 수정, 사용자 로그인
 - 장치 관련 : 신규 장치 등록
 - 친구 관련 : 친구 조회, 친구 추가 , 친구 삭제
 - 채널 관련 : 채널 생성, 채널 목록 조회, 채널에 사용자 추가, 채널에서 나가기
 - 메시지 관련 : 메시지 저장, 메시지 조회, GCM Notification 발송