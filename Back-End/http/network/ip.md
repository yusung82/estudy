# IP(인터넷 프로토콜)

### IP 란 ?
- IP(Internet Protocol) 란 인터넷에 연결되어 있는 모든 장치들(컴퓨터, 서버 장비, 스마트폰 등)을 식별할 수 있도록 각각의 장비에게 부여되는 고유 주소이다.

### IP의 역할
- 지정한 IP 주소에 데이터 전달
- 패킷이라는 통신 단위로 데이터 전달

### 패킷 전달 과정
- IP 패킷 정보가 필요하다 : 출발지 IP 도착지 IP ,기타 ...
- `클라이언트 패킷 전달` : 클라이언트가 서버에 데이터를 전달하려 하면 여러개의 노드를 거쳐 목적지 IP로 데이터를 전달시킨다.
- `서버 패킷 전달` : 서버가 클라이언트에게 전달할때도 클라이언트 IP로 정보를 전달한다.

<br>

### IP 프로토콜의 한계

#### 비연결성
- 패킷이 받을 대상이 없거나 서비스 불능 상태여도 패킷 전송

#### 비신뢰성
- 중간에 패킷이 사라지면?
- 패킷이 순서대로 안오면?

#### 프로그램 구분
- 같은 IP를 사용하는 서버에 실행중인 애플리케이션이 둘 이상이면 ?


#### 발생하는 문제
대상이 서비스 불능 , 패킷전송 ->  
1. 대상 서버가 패킷을 받을 수 있는 지 모름 
2. 패킷 소실
3. 패킷 전달 순서 문제 발생


<br>

> 그리하여 나온게 TCP와 UDP이다.