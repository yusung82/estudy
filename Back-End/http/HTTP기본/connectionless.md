# 비 연결성 (connectionless)

클라이언트와 서버는 요청을 주고 받을때만 연결을 유지하여 최소한의 자원을 사용한다.

- HTTP는 기본이 연결을 유지하지 않는 모델
- 일반적으로 초 단위 이하의 빠른 속도로 응답
- 1시간 동안 수천명이 서비스를 사용해도 실제 서버에서 동시에 처리하는 요청은 수십개 이하로 매우 작음 예) 웹 브라우저에서 계속 연속해서 검색 버튼을 누르지 않는다.
- 서버 자원을 매우 효율적으로 사용 가능함

#### 한계와 극복
- TCP/IP 연결을 새로 맺어야함 > 3 way handshake 시간 추가
- 웹 브라우저로 사이트를 요청하면 html 뿐만 아니라 js , css ,image 등 수 많은 자원이 함께 다운로드
- 지금은 http 지속 연결로 문제 해결
- http//2 , http/3 에서 더 많은 최적화

![비연결](../image/connectionless.png)

#### Stateless 를 기억하자
서버 개발자들이 어려워하는 업무

- 정말 같은 시간에 딱 맞추어 발생하는 대용량 트래픽
- 예 ) 선착순 이벤트, 명절 ktx 예약, 학과 수업 등록
- 예 ) 저녁 6시 선착훈 1000명 치킨 할인 이벤트 > 수만명 동시 요청
