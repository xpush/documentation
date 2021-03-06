실시간 서비스 플랫폼
======================
`실시간 서비스`라고 하는 것은 채팅, 실시간 상황판, 모바일 알람 등 실시간으로 데이터를 송수신 하고자 하는 서비스를 말합니다. 이러한 실시간 데이터 송수신 기능 자체 만으로 다양한 사업분야에 활용 될 수 있으며, 다른 서비스와 결합되어 여러가지 용도로 사용될 수 있습니다.

실제로, 게임에서 복수의 캐릭터의 동작이나 화면 동기화와 같은 다양한 실시간 데이터 송수신이나, 메신져 또는 채팅을 위한 대화 발송 및 수신 등 활용되고 있는 분야는 다양합니다.

이러한 실시간 서비스에는 기본적으로 반드시 필요한 기능들이 공통으로 존재합니다.

 - 데이터 송수신, 데이터 저장 및 조회
 - 접속 사용자 및 Device 관리
 - 접속을 위한 인증 처리 및 Session 관리
 

`실시간 서비스 플랫폼`은 이러한 필수적인 기능들을 모아 별도의 서버로 구축하여 플랫폼화 한 것입니다. 그리고 이 플랫폼을 기반으로 다양한 실시간 서비스를 개발할 수 있도록 하는 것이 본 프로젝트 팀의 목표입니다.

실시간 서비스를 구현하려는 개발자는 `실시간 서비스 플랫폼`을 사용하여 다양한 실시간 기능을 구현할 수 있습니다. 만약 이러한 `실시간 서비스 플랫폼`이 없다면, 각각의 실시간 서비스 시스템을 구축하고자 할 때마다 모든 기능들을 각각 새로 개발해야만 하거나, 공통의 기능을 모두 구현해야만 할 것입니다.

플랫폼에 구현된 기능들을 실시간 서비스에 기본적으로 필요한 **필수 기능** 이라 할 수 있으며, 이 플랫폼을 기반으로 개발된 다양한 서비스별로 각각 다르게 구현되어야 하는 기능을 **서비스 기능** 이라고 할 수 있습니다.

플랫폼에 구현된 **필수 기능**들은 각기 다른 모든 서비스에 영향을 주는 영역이며, **서비스 기능**들은 플랫폼에 영향을 주지 않는 각각의 서비스에 해당하는 기능들입니다.
이러한 기능들은 플랫폼과 서비스 별로 별도로 기능 업데이트 될 수 있어야 하며, 각각의 서비스는 플랫폼의 필수 기능을 공통으로 사용할 수 있어야 보다 유연하게 운영 관리 될 수 있을 것입니다.
