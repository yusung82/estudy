# 배포 전략의 종류(롤링/블루 그린/카나리)

## 블루 그린 배포 (Blue Green)

![](https://velog.velcdn.com/images/jingrow/post/57f5e51e-6dc7-4f44-ada2-231d0e444d32/image.png)

이전 버전 blue 환경으로, 새 버전은 green 환경으로 부를 수 있습니다.

한 번에 하나의 버전만 게시됩니다. 동일한 서버를 미리 구축한 뒤, 라우팅을 순간적으로 전환하여 새로운 버전을 배포하는 방식입니다.

빠른 롤백이 가능하다는 장점이 있고 운영 환경을 유지하며 새로 배포될 버전의 테스트도 가능하지만, 자원이 두배로 필요하니 비용이 많이 발생한다는 단점도 있습니다.

## 롤링 배포 (Rolling)

![](https://velog.velcdn.com/images/jingrow/post/57f5e51e-6dc7-4f44-ada2-231d0e444d32/image.png)

롤링 배포는 애플리케이션이 실행 중인 인프라를 완전히 교체하여 이전 버전의 애플리케이션을 새로운 버전의 애플리케이션으로 서서히 교체하는 배포 전략입니다.

인스턴스를 정해놓은 단위로, 순차적으로 새로운 버전으로 교체됩니다. 

가용 자원이 제한적일 경우에 사용됩니다.

이와 같은 방식은 서버 수의 제약이 있을 경우 유용하지만 배포 중 인스턴스 수가 감소되므로 서버 처리 용량을 미리 고려해놔야 합니다.

## 카나리 배포(Canary Deployment)

![](https://velog.velcdn.com/images/jingrow/post/0e926b33-6f41-4c75-bca2-29d03ca1abc9/image.png)

전체 인프라에 새로운 소프트웨어 버전을 릴리즈하여 모든 사용자가 사용할 수 있도록 하기 전에 변경사항을 천천히 릴리즈함으로써 프로덕션 새로운 소프트웨어 버전을 도입하는 위험을 줄이는 기술입니다.

카나리아 새처럼 빠르게, 미리 위험을 감지하여 대응할 수 있도록 하는 배포 방식입니다. 구 버전의 서버와 새 버전의 서버들을 구성하고 일부 트래픽을 새 버전으로 분산하여 오류 여부를 판단하기 때문에 오류율 및 성능 모니터링에 유용하다고 합니다.