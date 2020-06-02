# daily-study
> 매일 학습한 내용을 기록합니다.

- 매일 학습한 내용과 배운점, 느낀점을 포함하여 기록합니다.
- 주관적인 의견을 제외한 내용은 [기술 블로그](http://devham76.github.io/)에 기록합니다.

# 개인 학습

| Date       | Content|
| ---------- | ----------- |
| 2020-05-27 | [GitKraken과 git-flow 사용해보기](/content/daily/2020-05-27.md) |
| 2020-05-28 | [로드 밸런서 & Blocking-NonBlocking-Synchronous-Asynchronous](https://devham76.github.io/tags/#server) |
| 2020-05-29 | [mysql 스토리지엔진](/content/daily/2020-05-29.md) |
| 2020-05-30 | [라우팅](/content/daily/2020-05-30.md) |
| 2020-05-31 | [MSA , MQ](/content/daily/2020-05-31.md) |
| 2020-06-01 | [NoSQL](/content/daily/2020-06-01.md) |
| 2020-06-02 | [Web에서 client의 요청은 server에서 어떻게 처리될까?](/content/daily/2020-06-21.md) |




# 학습할 내용
- 궁금하고 관심있는 학습예정 목록을 기록합니다.
- 빠른시일 내에 조사, 공부하고 기록할 예정입니다.

## 내용
- GET요청에는 BODY가 들어갈수있을까?
- JAVA8, JAVA11
  - 곧 java8지원이 중단된다. 개발시 11을 권장합니다
- singleton패턴 구현



- 비동기 프로그래밍
  - <https://devham76.github.io/tags/#server>
- DB엔진
  - MySQL은 MyISAM, InnoDB가 있다.
  - MyISAM
    - select할때 좋다 InnoDB보다 Storage limit 크다 / 트랜잭션x
  -  InnoDB
    - 트랜잭션 지원, update,delete 할때 빠르다

- 이진검색(구현방법과 평균, 최악 복잡도)
  - 이미 정렬되어있는 배열에서 검색한다.
  - 하나의 값을 뽑고 찾는것보다 작으면 우측, 크면 좌측 반씩 나누므로 O(logN)
  - ※ 이진 트리에서 일반 검색한다면
    - 트리 삭제를 잘못해서, 편향이진 트리가 만들어질 수 있고 그렇게 되면 O(n)이 될수도 있다.
  - ※ 퀵 정렬
    - 이진트리와 비슷하게 pivot을 고르고 pivot보다 작은값왼쪽, 큰값 오른쪽으로 정렬한다.
    - 반씩 나누는걸 배열개수만큼 해서 최선,평균 O(logN)
    - 계속해서 바꿔야 하는 상황이면 최악, O(N^)

- 마이크로서비스 아키텍쳐란?
  - 시스템을 여러 애플리케이션으로 분리하여 결합도를 낮추는 설계방법
  - api로 통신하는데 이때 Messqge 시스템을 이용해서 통신한다
  - MOM(Message Orinted Middleware)는 producer가 data를 생성해서 MQ에 넣고 consumer가 이를 사용하는 형태
  - RebbitMQ , Kafka가 있다.
    - RebbitMQ
      - 메시지 전달을 보장한다 (신뢰성, 안정성을 위한 기능 제공)
      - 관리 UI가 있어 관리가 편하다

    - Kafka
      - 대규모 분산 처리에 특화되어있다.
      - 가장 빠른 MQ / 설치, 운영 쉽다
      - 보통은 MQ -> consumer로 push 하지만 Kafka는 cosumer가 MQ에서 데이터를 pull한다

- 쿠버네티스란?
  - Docker와 비슷한것 같은데 무슨차이일까
- CDN이란?
  - Content Distribution N/w  , Content Delivery NetWork
  - N/W상에 동일한 콘텐츠를 복제해서 대규모 인터넷상에 분산시켜놓음
  - 하나의 웹서버에 콘텐츠를 두는것보다 훨씬 빠르다
  - Vue.js , Bootstrap 을 사용할때 이용한적있다.
- 분산서버 아키텍처
- [git pull request merge](https://meetup.toast.com/posts/122)
