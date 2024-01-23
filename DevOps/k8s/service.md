# Service - Cluster IP, Node Port, Load Balancer

## Service

먼저 Pod만을 사용하지 않고 Service를 사용하는 이유를 알아봅시다.

Pod라는 것은 쿠버네티스 환경에서 다양한 요인으로 인해 언제든지 고장이 날 수 있습니다.

그러면 추후에 알아볼 Controller등에서 Pod를 재생성하게 됩니다.

재생성된 Pod는 IP할당이 달라지게 됩니다. 즉, 신뢰성이 떨어지게 되는 것이죠.

그에 반해서 Service는 사용자가 직접 삭제하지 않는 한 지워지지 않습니다.

그러므로, Service와 함께 구성된 Pod는 더욱 신뢰성을 가지며, 클라이언트는 Service로 접근하여 Pod에 접근 가능하도록 만들어줍니다.

<br>

## Cluster IP
이름에서도 보시다시피, 외부에서는 접근이 불가능하고 클러스터 내에서만 접근이 가능한 오브젝트입니다.

Pod를 여러 개 연결 시킬 수 있으며, 여러 개의 Pod를 연결 했을 때, 서비스가 트래픽을 분산시켜 Pod에 전달하게 됩니다.

<br>

## Node Port
이 Option에서도 기본적으로 Cluster IP가 할당됩니다.

하지만 차이점은 Cluster IP는 Pod들과 Service의 연결이었다면, 이 Option에서는 Node 단위로 Service와의 연결이라는 점입니다.

쿠버네티스 클러스터에 연결되어있는 모든 Node에 똑같은 Port가 할당되어서 해당 Node, 해당 Port로 접속하게 되면, Service로 접근이 되고, Service는 자신에게 연결되어 있는 Pod에 트래픽을 전달하는 방법입니다.

<br>

## Load Balancer

Node Port의 성격을 그대로 가집니다.

각각의 노드에 트래픽을 분산시켜주는 역할을 하며, 로드밸런서에 접근하는 외부 접속 IP는 별도로 할당합니다.

실제 운영환경에서는, NodePort가 아닌 Load Balancer를 사용해야합니다. 그러한 이유는 노드의 직접적인 IP를 노출하게 되면 보안상 위험이 생길 수 있기 때문입니다.

