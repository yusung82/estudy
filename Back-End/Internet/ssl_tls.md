# SSL(Security Socket Layer), TLS(Transfer Layer Security)

## SSL 

Security Socket Layer

인터넷을 통해 전달되는 정보 보안의 안전한 거래를 사용하기 위해 Netscape사에서 개발한 인터넷 통신 규약
  
90년대 중반 폐기된 프로토콜

SSL 계층은 응용 프로그램 계층과 전송 계층 사이에 위치

1. 응용 프로그램 계층 데이터가 SSL 계층에 전달
2. SSL 계층은 응용 프로그램 계층에서 수신한 데이터에 대한 암호화를 수행
3. 암호화된 데이터에 SSL 헤더(SH)라는 자체 암호화 정보 헤더를 추가
4. SSL 계층 데이터는 전송 계층(TCP/UDP)에 대한 입력이 된다.

### SSL 인증서를 복호화하는 것도 암호화하는 요소에 포함되어 있다.

SSL 인증서?  
쉽게 말하면, 사용자가 방문하는 사이트가 믿을 만한 사이트인가? 라는 것을 증명해주는 '정품 인증'같은 것이다.
  
CA는 서버 운영 기업이 넘겨진 공개키를 인증서 발급자, CA의 이름 등과 함께 묶어서 CA가 가지고 있는 개인키로 암호화해서 SSL인증서로 발급한다.


## TLS
![](https://velog.velcdn.com/images/sweet_sumin/post/2f0b2f3a-df2d-4098-9313-88f1c999c337/image.png)

Transfer Layer Security

SSL 3.0을 기초로해서 IETF가 만든 프로토콜이다.

보안 및 개인 정보 보호 기능이 강화된 후속 인터넷 표준이다.

TLS는 단일 프로토콜이 아니고 2계층에 걸친 프로토콜이다.

현재 브라우저의 버전을 확인해보니 TLS 1.3 임을 확인했다.

![](https://velog.velcdn.com/images/sweet_sumin/post/14ea84f8-4ed0-4256-a450-42c5b1bf47a9/image.png)

## SSL, TLS의 암호화하는 방식

결론적으로 **SSL, TLS 암호화는 공유키와 공개키 방식을 둘다 사용한다.**

전자 인증서에는 CA, 서버에 대한 정보, 공개키, 전자서명을 가지고 있다.

1. 클라이언트가 서버에 연결 요청을 한다.
2. 서버가 클라이언트에게 자신을 증명할 수 있고, 서로의 데이터를 암호화할 수 있는 전자 인증서를 보낸다.
   1. 몇 가지 방법이 있긴 하지만 비밀키는 CA에서 주는 것으로 한다.
   2. 즉, 서버가 전자 인증서를 클라이언트에 보냄으로써 클라이언트와 서버가 동시에 공개키를 가지고 있게 된다.
3. 클라이언트에서 난수를 생성해 공개키를 사용하여 난수를 암호화한다. 이 암호화된 내용이 공유키다.
4. 공유키를 서버로 보낸다. 그 다음 통신부터는 공유키로 암호화된 데이터만 주고받는다.

공유키가 없는 처음 한번만 공유키를 서버에 줄 때 그 한번에 해당 공유키를 탈취당할 경우말고는 그 이후의 통신부터는 데이터만 주고받기 때문에 보안성을 어느정도 지키면서도 공유키의 장점인 빠른 속도로 통신한다는 장점을 해당 방법을 사용했다.

공유키를 만들기 위해 공개키와 난수의 계산은 리소스가 크기 때문에 처음 통신 한번일때만 실행한다.

여기서 공유키는 대칭키이고, 공개키는 비대칭키라고 한다.