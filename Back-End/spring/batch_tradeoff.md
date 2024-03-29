# Spring Batch 기술적 트레이드 오프


스프링 배치는 대규모 데이터 처리를 위한 배치 애플리케이션을 개발하기 위해 스프링에서 지원하는 프레임워크 입니다.

오늘은 스프링 배치 프레임워크의 기술적 트레이드오프와 어떠한 상황에서 적용해야 하는지

그리고 실시간 API 방식과의 차이에 대해서도 알아보도록 하겠습니다.

일단 스프링 배치의 트레이드 오프는 다음과 같을텐데요.

1. 복잡성
2. 유연성 대비 단순성

스프링 배치는 고급 기능을 지원하기 위해서 다양한 구성 요소와 설정이 필요할 수 있고 러닝 커브가 가팔라질 수 있긴합니다.

그리고 일부 간단한 배치 작업에 대해서는 스프링 배치 유연성이 필요하지 않을 수 있어, 이에 따라 복잡성이 불필요할 수 있어요

보통 이 부분은 성능적인 트레이드 오프보다는 학습 시간, 유연성에 대한 트레이드 오프군요 API나 쿼리를 통해서 처리하는 것과 성능상으로 무슨 차이가 있을지 알아볼게요

<br>

## API vs Batch

API 처리와 배치, 그리고 쿼리를 통한 데이터 정리는 다른 목적과 상황에서 사용됩니다.


### 실시간 처리 vs 배치 처리


API나 쿼리를 이용한 데이터 정리는 실시간 또는 즉시처리가 가능해요. 데이터 실시간 업데이트와 조회에 용이합니다. 그리고 불규칙한 주기로 실행되어요.

반면에 배치 처리는 대규모 데이터를 주기적으로 처리하고 정리하는데 사용되고 일정한 주기로 실행되어요.

### 처리 시간 및 자원 사용, 시스템 부하

배치 처리는 실시간처리에 비해서 처리 시간 및 자원 사용을 효율적으로 처리할 수 있는 장점이 있어요 (아래에서 더 자세히 언급)


그리고 대규모 데이터를 실시간으로 처리한다면 시스템 부하가 발생할 수 있어요. 반면에 배치 처리는 주로 유휴 시간에 실행되기 때문에 시스템 부하를 분산시킬 수 있는 장점도 있어요.

### 데이터 일관성

API, 쿼리 방식은 실시간 처리이기때문에 실시간 업데이트를 반영할 수 있으나, 이로 인해 일관성을 유지하기위한 추가적인 관리가 필요해요.

반면에 배치 처리는 주기적으로 실행되기 때문에 일관성을 유지하기 용이합니다. (물론 배치도 동시에 여러번 돌 수 있어요 이와 같은 해결방법은 다른 포스팅에서 말씀드리겠습니다.)


정리해보면 실시간으로 처리할 것인가 일정한 주기로 처리할 것인가.

대용량 데이터를 처리할 때 시스템 부하와 자원사용을 고려해봐야해요

- API -> 실시간 처리 / 상대적인 속도 / +  QA가 용이합니다
- Batch -> 후속 처리 / 절대적인 속도 / + QA가 복잡합니다.


그렇다고 스프링 배치에서 데이터 일관성을 항상 보장할 수 있는건 아니에요 [[Spring Batch 데이터 일관성 유지 방법]] 에서 자세히 설명했습니다.

### 스프링 배치를 어떠한 상황에 사용해야하나?

배치가 필요할 때는 **일정 주기로 실행하며, 실시간 처리가 어려울 정도로 대량의 데이터를 처리할 때**입니다.

대용량 데이터 처리가 필요한 상황 == 배치가 필요한 상황입니다.

스프링 배치에서는 `Paging` or `Cursor` 기준으로 항상 조회를 합니다.


