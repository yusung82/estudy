# Netty

Netty(네티)는 자바 기반의 비동기 이벤트 기반 네트워크 애플리케이션 프레임워크이다.

### 네티를 왜 사용하는가?

네티를 사용하면 TCP, UDP, HTTP 및 웹소켓과 같은 다양한 프로토콜을 처리할 수 있으며, **고성능, 확장성 및 유연성을 제공**한다.

네트워크 애플리케이션을 그냥 자바의 소켓 프로그래밍을 통해 구현하는 것에 비해 네티의 추상화로 인해 얼마나 간결하게 자바 네트워크 프로그래밍을 할 수 있는지를 보여준다.

### 네티에서 데이터 이동의 방향성

네티는 이벤트를 Inbound 이벤트, Outbound 이벤트로 구분한다.

클라이언트로 부터 데이터를 수신할 때 발생하는 이벤트에 관심이 있다면, Inbound 이벤트 중 하나인 데이터 수신 이벤트를 담당하는 메서드에 원하는 로직을 넣으면 된다.

## 동작 방식

![](https://velog.velcdn.com/images%2Fmonami%2Fpost%2F86203714-fdd3-441a-ba29-16ae9742b9dc%2FKakaoTalk_20210911_222645477.jpg)

소켓의 동작방식이 다르므로 입출력을 위한 메서드 및 프로그램 호출 구조가 다르다.

하지만 네티는 소켓의 모드와 상관없이 개발할 수 있도록 추상화된 전송 API를 제공한다.

따라서 소켓 모드를 바꾸기 위해서 데이터 송수신 부분의 로직을 고치지 않아도 된다.

## NIO(Non-Blocking I/O)


NIO는 자바에서 제공하는 I/O 처리 방식 중 하나로, 기존의 I/O 방식인 스트림 기반에 I/O 처리 방식과 다르게 채널(Channel)과 버퍼(Buffer)를 사용해 작업을 처리합니다.

