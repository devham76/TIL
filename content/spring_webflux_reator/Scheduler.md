## Schedulers
Reactor에서 실행 모델과 실행 위치는 사용된 Scheduler에 의해 결정된다.
Scheduler는 ExecutorServie와 유사한 스케쥴링 책임을 가지고 있지만 전용 추상화를 통해 더 많은 작업을 수행할 수 있고
특히 시계와 관련된 더 광번위한 구현(테스트를 위한 가상 시간, 트램폴린 또는 즉각적인 스케줄릳 등)을 가능하게 한다.

### method 종류
Scheduler class는 execution context에 엑세스할 수 있는 static method를 가지고 있다.
- Schedulers.immediate() : 현재 Thread
- Schedulers.single() : 재사용 가능한 단일 Thread
    - 스케줄러가 종료될 때까지 모든 호출에 대한 동일한 Thread를 재사용함
    - 호출 별 전용 Thread를 원하는 경우 각 호출에 대해 Schedulers.newSingle()을 사용해야 한다.
- Schedulers.elastic() : 무제한 탄성
    - 이 경우 backpressure 문제를 숨기고 너무 많은 Thread를 유발하는 경향이 있어 Schedulers.boundedElastic()도입 이후 더이상 선호 되지 않는다.
- Schedulers.boundedElastic() : 제한 탄성 Thread pool
    - 이전의 elastic()과 마찬가지로 필요에 따라 새 worker pool를 만들고 유휴 상태인 풀을 재사용한다.
    - 너무 오래 유휴 상태인 worker pool (default 60s)은 폐기된다.
    - elastic()과 달리 만들 수 있는 Thread수에 제한이 있다. (default, CPU core수 * 10)
    - 한도에 도달한 후 제출된 최대 10만 개의 작업이 대기열에 추가되고 Thread를 사용할 수 있게 되면 다시 스케쥴이 조정된다.
        - 지연으로 예약하면 Thread가 사용가능해지면 지연이 시작됨
    - 이것은 I/O blocking work에 더 나은 선택이다.
    - 이것은 다른 리소스를 묶지 않도록 차단 프로세스에 자체 Thread를 제공하는 편리한 방법이다.
    - 이것은 피할 수 없는 레거시 blocking code를 돕게 위해 만들어졌지만 single 및 parallel은 불가능하다.
- Schedulers.parallel() : 병렬 작업에 맞게 조정된 고정 worker pool


---
### Reference 
- https://luvstudy.tistory.com/97
