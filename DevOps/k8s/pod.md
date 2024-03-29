# Pod - Container, Label, Node Schedule


Pod은 쿠버네티스의 가장 기본적인 배포 단위입니다.

마스터 노드에서는 워커노드로 Pod을 전달하고 워커노드에서는 Pod을 수행하는 구ㅗ다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FctN0nC%2FbtqM5VlDbOg%2Fhz31qGnbzLxAnnsfThKwGk%2Fimg.png)

### 왜 Pod 단위로 묶어서 배포하는 것일까?

1. Pod 내부 컨테이너 간의 IP 및 Port 공유를 통한 용이성 향상

N개의 컨테이너가 한 개의 Pod에 탑재되어 배포된 어플리케이션을 고려해보자.

이 어플리케이션 안의 컨테이너끼리는 실시간으로 데이터를 교환하며, 그에 따라 상태를 업데이트 한다.

두 컨테이너는 별도의 IP호출 없이 localhost를 통해 통신이 가능하다.


## Container

Pod는 기본적으로 한 개 이상의 컨테이너들로 구성되어 있다.

Pod 안의 컨테이너들은 서비스가 서로 연결될 수 있도록 포트를 가지고 있다.

여기서, 한 컨테이너는 하나 이상의 포트를 가질 수 있지만, 한 포트를 여러 컨테이너가 공유하지는 못하게 됩니다.

Pod은 또한 생성될 때 고유 ip가 생성됩니다.

Pod를 IP를 통해서 접근할 경우 쿠버네티스 클러스터 내에서만 접근이 가능하고, 외부에서는 접근이 불가능합니다.

<br>

## Label
Pod 뿐만 아니라 모든 오브젝트에서 다 쓰입니다.

하지만, Pod에서 가장 많이 사용합니다.

Label을 사용하는 이유는 목적에 따라 오브젝트들을 분류할 수 있으며, 오브젝트들을 따로 연결하기 위해서 사용합니다.

구성은 키와 밸류 형태로 만들어집니다.

<br>

## Node Schedule
Pod은 여러 노드들 중 한 노드에 올라가야합니다.

직접 노드를 선택하는 방법과 쿠버네티스가 자동으로 선택하는 방법이 존재합니다.

쿠버네티스 스케쥴러가 판단하여 노드를 고를 수 있습니다
- CPU 사용량
- 메모리 사용량

