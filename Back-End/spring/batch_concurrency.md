# Spring Batch 데이터 일관성 관리


스프링 배치 애플리케이션이 같은 데이터를 변경하는 배치가 두 개 동시에 돌때 해결하는 방법이 무엇이 있을까요?

면접에서 받은 질문인데 더 자세히 한 번 알아보도록 하겠습니다.

### 동시성 제어하기

데이터 row에 관해 lock을 걸어 동시성을 제어하는 방법이에요

간단하고 직관적인 방법이지만 락의 대기 시간이 길어질 수 있고 데드락이 발생할 수도 있습니다.


### 분산 락 사용

여러 애플리케이션이 동시에 데이터 업데이트를 시도할 때, 분산 락을 사용해 각 애플리케이션이 데이터를 업데이트하기 전에 락을 획득하도록 해요, 이를 통해 한 번에 하나의 애플리케이션만이 데이터를 업데이트할 수 있도록 해요

분산 환경에서도 동시성을 제어할 수 있는 강력한 방법이지만, 락 관리에 대한 복잡성과 오버헤드가 발생할 수 있으며, 락 관리에 대한 중앙화된 시스템이 필요합니다.


### 일괄처리

좀 당연한 방법이라고 생각할 수 있는데 서로가 동시에 실행되지 않도록 조정하는거에요. 스케쥴러를 통해서 데이터 업데이트가 겹치지 않고 순차적으로 이루어지도록 합니다.


### 버전 관리

업데이트할 데이터에 버전 관리를 도입해서, 동시에 업데이트를 시도하는 경우에는 각 애플리케이션이 데이터 현재 버전과 일치하는지 확인하고, 버전이 일치할 때에만 업데이트를 수행하도록해요

데이터 변경 이력을 추적할 수 있으며, 동시성 제어에 유용한 방법이에요 그러나 데이터베이스 스키마 변경이 필요할 수 있어 처음부터 도입하지 않으면 조금 어려우며 버전 관리를 위한 추가적인 로직이 필요하며 오버헤드가 발생할 수도 있어요


스프링 배치는 대용량 데이터를 일정한 주기에 실행할 수 있도록 사용되는 배치 애플리케이션을 만드는 목적을 가지고 있기 때문에 배치 특성상 같은 데이터에 대한 처리를 여러번 돌린다는게 살짝 어색한 감이 없지않아 있다고 생각되지만 실무에서는 빈번히 일어날 수도 있다고 생각한다.

아직 실무에서 배치를 그렇게 작성해본 적이 없어서 더욱 알아봐야겠다