## fromCallable

- public static <T> Mono<T> fromCallable(Callable<? extends T> supplier)
- Create a Mono producing its value using the provided Callable. If the Callable resolves to null, the resulting Mono completes empty.
- 제공된 Callable을 사용하여 값을 생성하는 모노를 만듭니다. Callable이 null로 결정되면 결과 모노가 빈 상태로 완료됩니다.

![image](https://user-images.githubusercontent.com/55946791/114134091-18544800-9942-11eb-9492-a9f45ead674c.png)

- `exception을 자동으로 Mono.error로 래핑합니다.`
- Cold Publisher이며 subscribe(구독) 하지않으면 데이터를 방출하지 않습니다.


## fromSupplier
- public static <T> Mono<T> fromSupplier(Supplier<? extends T> supplier)
- Create a Mono, producing its value using the provided Supplier. If the Supplier resolves to null, the resulting Mono completes empty.
- 제공된 Supplier를 사용하여 모노 값을 생성하는 모노를 만듭니다. Supplier가 null로 결정하면 결과 모노가 빈 상태로 완료됩니다.

![image](https://user-images.githubusercontent.com/55946791/114134218-53567b80-9942-11eb-8a74-ad5fa19538ef.png)


## 참고

subscribeOn으로 별도 스레드로 동작시키고자 한다면 fromSupplier이 아닌 fromCallable을 추천.
Callable과 Supplier의 기능상으로 크게 차이는 없지만(Callable은 exception이 throw 될 수도 있다는 가정의 추가 정도), 인터페이스상 목적의 차이가 존재하는 것으로 알고 있습니다.

Callable이 Supplier의 기능의 구체화된 의미로 보시면 되고, Callable이 해당 instance가 다른 스레드로 실행될 수 있다라는 의미를 내포하고 있다.
따라서, 현재는 subscribeOn으로 다른 스레드로 동작시키기에, Callable이 좀 더 유의미한 사용일것이다.

- https://stackoverflow.com/questions/52215917/callable-vs-supplier-interface-in-java

---
### Reference
- https://projectreactor.io/docs/core/release/api/reactor/core/publisher/Mono.html
