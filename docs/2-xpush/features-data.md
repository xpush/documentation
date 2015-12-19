데이터 저장
======================

## MongoDB에 저장

XPUSH는 MongoDB를 이용하여 플랫폼에 등록된 사용자 정보와 생성된 채널의 정보와 메세지 정보를 저장한다. 사용하는 collection은 아래와 같다. 

### channels

채널 정보를 저장하는 collection

`channel.create` 이벤트 발생시 채널 정보를 생성한다. 채널ID와 채널에 속해있는 사용자 정보를 저장한다.

`channel.join` 이벤트 발생시, 채널 내 사용자 리스트에 신규 사용자를 추가한다.

`channel.leave` 이벤트 발생시, 채널 내 사용자 리스트에서 신규 사용자를 삭제한다.


### messages

메세지 정보를 저장하는 collection이다.

`send` 이벤트 발생시 채널ID와 발신자의 정보, 메시지를 받을 사용자의 리스트, 메시지 정보를 저장한다. 저장된 메시지는 메세지를 받을 사용자가 접속시 조회할 수 있다.


### users

사용자 정보를 저장하는 collection이다. 등록된 장치들의 정보를 저장하고 있기 때문에 Multi Device 에게 메세지를 전송할 수 있다.


`/user/register` API 호출시 사용자 정보를 생성한다. 

`/user/update` API 호출시 사용자 정보를 수정한다.

`/device/add` API 호출시 사용자의 장비를 추가로 등록한다.
