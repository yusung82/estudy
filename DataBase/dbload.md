# 데이터베이스 부하분산(파티셔닝, 샤딩, 레플리케이션)


## 파티셔닝

특정한 기준으로 테이블을 분리하는 것.

종류로는 column을 기준으로 분리하는 수직 파티셔닝과
row를 기준으로 분리하는 수평 파티셔닝이 존재한다.

수평 파티셔닝 방식에서도 해쉬 파티셔닝과 범위 파티셔닝과 같은 것들이 존재한다.

파티셔닝을 진행할 때 특정한 데이터를 기준으로 파티셔닝 키를 지정한다. 그렇기에 가장 많이 조회될때 사용되는 데이터를 기준으로 파티셔닝 키를 정해야한다.

<br>
## 샤딩

샤딩은 간단히 말해 수평 파티셔닝에서 분리한 테이블을 각각의 다른 DB 서버에 저장하는 것이다.

여기서 파니셔닝 Key는 샤드 Key라고 부른다.

<br>

## 레플리케이션

DB를 복제해서 여러 대의 DB 서버에 저장하는 방식이다.

Master-Slave 구조를 가지고 설계되는게 보통이며 Master에는 Read/Write와 Slave는 Read 작업을 맡고 있다.

Slave의 버전은 최소 Master의 버전보다 높아야 한다.

간단하게 알아보았고 각각의 방법에 대해서 자세히 더 알아볼 예정이다.